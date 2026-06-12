---
title: "Accessing windows XP shares.."
date: 2005-12-12
forum: General Help
---

### Post by actronx on 2005-12-12
Hello ,
Iam anewbie ubuntu user ..
my problem is 
i cann't access shared folders or administrative shares ex: C$  on another computer on the network running windows XP PRO SP2 , everytime i try to connect to it , it says the connection fails ...
the computer running XP has a public ip address...

however , i can access all other computers running winxp on the network...theyare all on the same subnet mask ...have private ip addresses...


so what can i do to access my XP computer 


Thanks in advance,

---

### Post by redactech on 2005-12-12
Don't worry every thing will work unless there's a catch in your network. You need to know  the workgroup of your network

in the terminal : 

sudo gedit /etc/samba/smb.conf

find this line

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = MSHOME

save and exit

in the terminal do 

sudo /etc/init.d/samba restart

then try to access the others XP shares

---

### Post by LordDante on 2005-12-12
ok then.. 
i have a pc with xp sp2 on 192.168.0.102
and my notebook with ubuntu a64 192.168.0.130

the pc has two accounts (well three actually but..irrelevant)
my private acc 
and

Share

user share is NOT in the admin group BUT has access to the admin share (via local security policy editing)

so when i want to access something from my notebook i just connect to server, enter my IP adress and select username and pass for the user Share

now.. 

does your xp have simple file sharing? (i really suggest you turning it off)
do you have access to a simple share eg: you share c:\download\ as "download"?
do you have firewall software on the XP?

if all else fails you can setup an ftp server on XP :) i use it all the time :) its faster (file transfer) and gives you less headaches.

if all else fails use filezilla ftp server

---

### Post by actronx on 2005-12-12
ok ,,
nothing worked !
even filezilla server !!!
 
the question is .... WHY cant I access my XP machine!!!

i tried to connect to filezilla from another computer running windows XP , it worked fine....

but i cant connect from ubuntu! the command line in filezilla stats that ive logon successfully but ubuntu says the document containts no data!!!!

ok from ubuntu i can access all shares on all other computers running XP...except the one which has the problem...

the one with the problem has a public ip address (actronx.no-ip.org) and running behind ADSL router .... other computers has local ip address and belong to same subnet and same work group as the laptop running ubuntu

idont konw whats going on this problem is drivin me crazy!!!!!!!!!

---

### Post by redactech on 2005-12-12
Wo!

don't panic, normally what you're trying to do is done by paid sysadmin. The problem you are experiencing has nothing to do with ubuntu but with the network.

Please give us the interfaces settings for both machine and be sure sure they are on the same workgroup (windows XP : ipconfig /all and ifconfig on ubuntu)

try to ping your xp machine with ubuntu and give us the results

---

