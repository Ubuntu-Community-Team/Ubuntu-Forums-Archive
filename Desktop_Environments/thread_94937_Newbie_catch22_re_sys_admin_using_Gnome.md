---
title: "Newbie catch22 re sys admin using Gnome"
date: 2005-11-25
forum: Desktop Environments
---

### Post by philcal on 2005-11-25
Hi 

I'm tying to config a new BBadger install on my amd64 laptop. This of course needs root access. I have tried sudo -s -H, sudo passwd root etc and am aware that Ubuntu restricts root access with Gnome. I can su to root in the Gnome console.
The BB5.04 Starter guide next step is using the main Gnome menu sys-admin to change the login security for Gnome, but nothing happens when I do this (I presume it should prompt for root password but it doesnt  -it only thinks about it) 

It seems you need to be  root user to configure Gnome so that it will accept  root user --  catch 22!  I guess a console cmd will be needed to edit the Xorg config.

Any suggestions? 


For any other would be amd64 laptop installers a website by 'Kastor' was very usefull on getting around the ATI driver problem and others alerting that you need to set vga=77 noapic switches at boot stage. My next battle will be fixing the  IOCGIFFLAGS error: No such device network error which I suspect is making the connection very slowww.

Thanks 
Phil C 
Perth Aus

---

### Post by taurus on 2005-11-25
First, make sure you, current user, belong to group adm in /etc/group.  You can view that with "more /etc/group."  And if you are, then create a password for root as

sudo passwd root

Then, just either log in as root or "su -" to root then...

---

### Post by philcal on 2005-11-25
Thanks Taurus

I tried what you suggested  
terminal extract:

phil@ubuntu:~$ sudo passwd root
phil@ubuntu:~$ su root
Password:
root@ubuntu:/home/phil# more /etc/group
root:x:0:
daemon:x:1:
bin:x:2:
sys:x:3:
adm:x:4:phil
.......

However when I try frome gnome any of the sys/adm programs I get the hourglass for a while but nothing else. It seems like its seaching for password but doesnt find it and doesnt promt for one also.

---

### Post by taurus on 2005-11-25
What programs you have in mind?  See if you can do this

sudo apt-get update
sudo apt-get upgrade

---

