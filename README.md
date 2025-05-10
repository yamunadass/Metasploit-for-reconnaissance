# Metasploit-for-reconnaissance
## Metasploit
Metasploit for reconnaissance in pentesting

## AIM:

To get introduced to Metasploit Framework and to  perform reconnaissance  in pentesting .

### BY: Yamuna M
### REG. NO: 212223230248

## DESIGN STEPS:

### Step 1:

Install kali linux either in partition or virtual box or in live mode

### Step 2:

Investigate on the various categories of tools as follows:

### Step 3:

Open terminal and try execute some kali linux commands

### EXECUTION STEPS AND ITS OUTPUT:
Find out the ip address of the attackers system
#### OUTPUT:
![image](https://github.com/user-attachments/assets/b9703284-6b8f-46e3-afac-9ab1d0c31e86)


Invoke msfconsole:
![image](https://github.com/user-attachments/assets/5f1bfa0e-4cbf-4a74-8680-7d96bba8f87e)


Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.

![image](https://github.com/user-attachments/assets/772ef2b2-9340-484a-8f74-3059357b4952)


#### Port Scanning:
Following command is executed for scanning the systems on our local area network with a TCP scan (-sT) looking for open ports between 1 and 1000 (-p1-1000).
msf >  nmap -sT 192.168.1810/24 -p1-1000
#### OUTPUT:
![image](https://github.com/user-attachments/assets/598bcf5c-a3ad-474d-bbef-edf8d72990f5)

step4:
use the db-nmap command to scan and save the results into Metasploit's postgresql attached database. In that way, you can use those results in the exploitation stage later.

scan the targets with the command db_nmap as follows.
msf > db_nmap 192.168.181.0/24
#### OUTPUT:
![image](https://github.com/user-attachments/assets/6c8eb0a5-23d6-4eb3-b2e3-9731bfa9fa67)


Metasploit has a multitude of scanning modules built in. If we open another terminal, we can navigate to Metasploit's auxiliary modules and list all the scanner modules.
cd /usr/share /metasploit-framework/modules/auxiliary
kali > ls -l
#### OUTPUT:
![image](https://github.com/user-attachments/assets/b7fae978-cd19-4bf9-909a-4b1bb675325c)


Search is a powerful command in Metasploit that you can use to find what you want to locate. 
msf >search name:Microsoft type:exploit

The info command provides information regarding a module or platform,
#### OUTPUT
![image](https://github.com/user-attachments/assets/fad6d941-f0b2-4858-9df5-3ea49880600a)


Before beginning, set up the Metasploit database by starting the PostgreSQL server and initialize msfconsole database as follows:
systemctl start postgresql
msfdb init
#### MYSQL ENUMERATION
Find the IP address of the Metasploitable machine first. Then, use the db_nmap command in msfconsole with Nmap flags to scan the MySQL database at 3306 port.
db_nmap -sV -sC -p 3306 <metasploitable_ip_address>
![image](https://github.com/user-attachments/assets/00f5d101-b106-4260-90fe-9c48af3bf1f2)


Use the search option to look for an auxiliary module to scan and enumerate the MySQL database.
search type:auxiliary mysql
![image](https://github.com/user-attachments/assets/7b606c3d-c7c2-4cc0-8da0-dc3493b32dd8)


use the auxiliary/scanner/mysql/mysql_version module by typing the module name or associated number to scan MySQL version details.
use 11 Or: use auxiliary/scanner/mysql/mysql_version
![image](https://github.com/user-attachments/assets/c272702f-85fa-4797-9259-1b04298e48ec)



Use the set rhosts command to set the parameter and run the module, as follows:
![image](https://github.com/user-attachments/assets/7cb2df0e-aebd-454e-a992-5b6b8de362a9)



After scanning, you can also brute force MySQL root account via Metasploit's auxiliary(scanner/mysql/mysql_login) module.
![image](https://github.com/user-attachments/assets/6d98cae1-206d-40e2-a5d9-e33b68e1f48a)


set the PASS_FILE parameter to the wordlist path available inside /usr/share/wordlists:
set PASS_FILE /usr/share/wordlistss/rockyou.txt
Then, specify the IP address of the target machine with the RHOSTS command.
set RHOSTS <metasploitable-ip-address>
Set BLANK_PASSWORDS to true in case there is no password set for the root account.
set BLANK_PASSWORDS true
![image](https://github.com/user-attachments/assets/4618a435-9885-45ed-8a5e-362bedc1f987)



## RESULT:
The Metasploit framework for reconnaissance is  examined successfully.
