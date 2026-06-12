---
title: "samba and to log in"
date: 2006-07-28
forum: Desktop Environments
---

### Post by shazbot on 2006-07-28
I have Samba installed on my laptop (me thinks) and can see the Ubuntu in my Workgrop on my XP machine

When I try and and access ths ubuntu thru XP in ask for a name and password, I have tried my loogin and root password to no avail, so I can't get further than the the XP window asking for a namle and password

I have tried sudo /etc/rc.d/init.d/smb start, but get a command not found

Also have tried to see if there is a smb.conf but seems that isnt one

Any idees as am a litlle lost as still a newbie ti linux

Thanks

---

### Post by bigken on 2006-07-28
in the terminal type
sudo apt-get install samba
sudo smbpasswd -e yourname
sudo smbpasswd -a  yourname
sudo /etc/init.d/samba

---

### Post by shazbot on 2006-07-28
That worked just great, many thanks

would you be as kind as to explain what is 

sudo smbpasswd -e yourname

sudo smbpasswd -a yourname

sudo /etc/init.d/samba

as would like to understand a little more

---

### Post by bigken on 2006-07-28
-e is edit i think and -a is add and init.d restarts samba as far as I know 
pleased its fixed enjoy ubuntu ;)

---

