---
title: "Ubuntu Server 7.04 on Dell 390 Desktop"
date: 2007-07-12
forum: Dell  Ubuntu Support
---

### Post by dsilver668 on 2007-07-12
Linux Noob here..
Ok I have a Dell 390 which has Windows XP Service Pack 2 installed with VMWARE.
I can load server, and logon via command line, but I would like a GUI, so I did "sudo apt-get install ubuntu-desktop" Seemed to work fine but afterwards it reboots back to command line. I am just not ready for a command line only os just yet.. I am working at it trust me.

It is almost as though it doesn't like the video card or something. Here is the caviat though. Ubuntu Desktop 7 loads great! I can run Ubunutu or Kubuntu with out issue. 

Only reason I want server is I plan to run Open AudIT and Nedi on it for network administration so I need LAMP done from the begining and server gives me that option painlessly.

Anyone who has had issues inthe past and worked through them please post. Even if you only loaded desktop a few times please post. I need to get my system up and running and I have been fighting with it all week.. 
Thansk Peace out..
:guitar:

---

### Post by apjjr on 2007-07-13
Try "sudo /etc/init.d/gdm start".

-Alex

---

### Post by dsilver668 on 2007-07-13
Thanks for your input Alex:
When I put in sudo /etc/init.d/gdm start I get the following

Password: "Ok do that"

* Starting GNOME Display Manager...            [ok]

Then it takes me back to command line prompt... :lolflag:

Ok now something weird happens. I did Ctrl Alt Insert to reboot.
It tries loading X server but I get the following:
Failed to start x server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?
I went and ran sudo apt-get update
Then ran sudo apt-get purge-- remove ubuntu-desktop
then I did a sudo apt-get install ubuntu-desktop gdm
then ran sudo apt-get update
then sudo apt-get /etc/init.d/gdm start
WOOOHOOO!!! got a logon screen
I am very happy now..

---

### Post by SirBob1701 on 2007-07-13
i've never installed desktop from server but i'm thinking you might have to hit Ctrl+Alt+F7 after you start gdm.  I think it only starts in that tty i might be completely wrong tho

---

