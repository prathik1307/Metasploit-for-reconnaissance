# Metasploit-for-reconnaissance
# Metasploit
Metasploit for reconnaissance in pentesting

# AIM:

To get introduced to Metasploit Framework and to  perform reconnaissance  in pentesting .

## DESIGN STEPS:

### Step 1:

Install kali linux either in partition or virtual box or in live mode

### Step 2:

Investigate on the various categories of tools as follows:

### Step 3:

Open terminal and try execute some kali linux commands

## EXECUTION STEPS AND ITS OUTPUT:

Find out the ip address of the attackers system
## OUTPUT:
<img width="650" height="326" alt="image" src="https://github.com/user-attachments/assets/e3b72c32-b212-4ae2-b45d-f2329721dbc4" />


Invoke msfconsole:
## OUTPUT:

<img width="590" height="563" alt="image" src="https://github.com/user-attachments/assets/fc0a5e92-aa36-4f26-ad78-bc953d598d74" />


Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.

## output:

<img width="733" height="616" alt="image" src="https://github.com/user-attachments/assets/456d75f1-2ecf-4711-8128-ccf093908482" />



Port Scanning:
Following command is executed for scanning the systems on our local area network with a TCP scan (-sT) looking for open ports between 1 and 1000 (-p1-1000).
msf >  nmap -sT 192.168.1810/24 -p1-1000  (Replace with appropriate IP Address)
## OUTPUT:
<img width="509" height="397" alt="image" src="https://github.com/user-attachments/assets/19d3a58e-24b2-4c17-9540-52115b2f51a1" />

step4:
use the db-nmap command to scan and save the results into Metasploit's postgresql attached database. In that way, you can use those results in the exploitation stage later.

scan the targets with the command db_nmap as follows.
msf > db_nmap 192.168.181.0/24
## OUTPUT:

<img width="598" height="332" alt="image" src="https://github.com/user-attachments/assets/d57e15f8-2031-4ac6-9e37-8b5d46746095" />


Metasploit has a multitude of scanning modules built in. If we open another terminal, we can navigate to Metasploit's auxiliary modules and list all the scanner modules.
cd /usr/share /metasploit-framework/modules/auxiliary
kali > ls -l
## OUTPUT:
<img width="544" height="367" alt="image" src="https://github.com/user-attachments/assets/ed1c3b44-a50a-484a-a809-086b14091fcb" />

Search is a powerful command in Metasploit that you can use to find what you want to locate. 
msf >search name:Microsoft type:exploit
## OUTPUT:

<img width="779" height="380" alt="image" src="https://github.com/user-attachments/assets/2d60fbcf-3617-4161-8bf2-65e082725801" />


The info command provides information regarding a module or platform,

Before beginning, set up the Metasploit database by starting the PostgreSQL server and initialize msfconsole database as follows:
systemctl start postgresql
msfdb init
## OUTPUT:

<img width="784" height="404" alt="image" src="https://github.com/user-attachments/assets/07300de7-d7c4-4b03-86d9-1904e5770906" />

## MYSQL ENUMERATION
Find the IP address of the Metasploitable machine first. Then, use the db_nmap command in msfconsole with Nmap flags to scan the MySQL database at 3306 port.
db_nmap -sV -sC -p 3306 <metasploitable_ip_address>

## OUTPUT:

<img width="775" height="153" alt="image" src="https://github.com/user-attachments/assets/d2588619-1299-4f27-a74a-bdc2a5ec89eb" />


Use the search option to look for an auxiliary module to scan and enumerate the MySQL database.
search type:auxiliary mysql
## OUTPUT:

<img width="770" height="264" alt="image" src="https://github.com/user-attachments/assets/b6da9016-7c4e-4245-a716-2e9b0a4828de" />

use the auxiliary/scanner/mysql/mysql_version module by typing the module name or associated number to scan MySQL version details.
use 11
Or:
use auxiliary/scanner/mysql/mysql_version
## OUTPUT:

<img width="782" height="274" alt="image" src="https://github.com/user-attachments/assets/034a0972-3fcf-4756-8d08-ac60a6d304ad" />

Use the set rhosts command to set the parameter and run the module, as follows:
## OUTPUT:

<img width="769" height="141" alt="image" src="https://github.com/user-attachments/assets/4a83bbc5-bb63-4068-b08b-fff37387eb0a" />


After scanning, you can also brute force MySQL root account via Metasploit's auxiliary(scanner/mysql/mysql_login) module.
## OUTPUT:


<img width="772" height="336" alt="image" src="https://github.com/user-attachments/assets/75c436e4-45c4-459e-96da-d56a4e45f7f0" />


set the PASS_FILE parameter to the wordlist path available inside /usr/share/wordlists:
set PASS_FILE /usr/share/wordlistss/rockyou.txt
Then, specify the IP address of the target machine with the RHOSTS command.
set RHOSTS <metasploitable-ip-address>
Set BLANK_PASSWORDS to true in case there is no password set for the root account.
set BLANK_PASSWORDS true
## OUTPUT:

<img width="770" height="263" alt="image" src="https://github.com/user-attachments/assets/1a59b149-8ea9-4dd3-a5d9-0379d2e8c820" />

## RESULT:
The Metasploit framework for reconnaissance is  examined successfully
