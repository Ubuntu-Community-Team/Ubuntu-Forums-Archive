---
title: "Kubuntu 8.10 boot Autostart How ?"
date: 2009-02-10
forum: Desktop Environments
---

### Post by packet123 on 2009-02-10
Hello All,

I am new to Ubuntu as well as kubuntu ... I installed kubuntu8.10 USB on a 2 GB Flash .
its booting well but i need following things to run my application !!!!!

In Knoppix5.1.1 USB ,while booting it will search for a knoppix.sh file in Knoppix directory to execute user commands . knoppix.sh file is like post-configuration shell script. and we can put a our application script in the path /etc/skel/.kde/Autostart .

my question is how to i get in kubuntu ? is there any other option to run my application script in the boot up ?

if yes please tell me in steps .

Thanks :confused:

---

### Post by Monsieur Gonzalez on 2009-02-10
Hi!

Just go to System Settings, Advanced tab, then enter the Autostart section where you'll be able to add startup programs and/or scripts

---

### Post by packet123 on 2009-02-10
Hi,

I tried its not working ...

-> system setting -> advance tab -> Autostart -> add script 

-> I added from the path /cdrom/syslinux/example.sh 

-> after reboot it is not doing what expected it simply putting the script in the path /hoe/ubuntu/.kde/Autostart

example.sh contain following commands
#!/bin/sh

sudo mkdir /mnt/USB
sudo chmod 777 /mnt/USB

sudo cp /cdrom/syslinux/gprs /etc/ppp/peers/gprs
sudo cp /cdrom/syslinux/time /home/ubuntu

-> so what i need to do to execute example.sh script automatically after boot?

( Note : permission of example.sh is 777  and Kubuntu is on 2GB Flash means it is Read Only file system i.e files will not save after reboot !!! )

---

### Post by Monsieur Gonzalez on 2009-02-10
Well, have you considered running the script at boot time? You might add those lines (without the sudo part) to /etc/rc.local, then your script should work.

---

