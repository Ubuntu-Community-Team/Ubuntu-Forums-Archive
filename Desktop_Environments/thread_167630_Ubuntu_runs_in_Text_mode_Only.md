---
title: "Ubuntu runs in Text mode Only"
date: 2006-04-28
forum: Desktop Environments
---

### Post by mooha on 2006-04-28
Hello every one,

I am new to Linux, I installed Ubuntu 5.10, the system works fine, one day I ran Add application, and then I rebooted after successful Pakages Adding, I dont have the Login Screen it only gives me a Text Mode login Only. Can you please help me to how to recover this, or is there a system repair ? your help is very appreciated.

Many Thanks

---

### Post by bluevoodoo1 on 2006-04-28
after you login try...

sudo /etc/init.d/gdm restart

if that comes up with some errors referring to "x" then try reconfiguring x with perhaps the vesa driver with this command...

sudo dpkg-reconfigure xserver-xorg

---

### Post by Ptero-4 on 2006-04-28
sudo dpkg-reconfigure gdm.
And if it complains that gdm doesn't exist in your system (shouldn't happen) then do sudo apt-get install gdm.

---

### Post by az on 2006-04-28
Boot into recovery mode and try

dpkg-reconfigure -phigh xerver-xorg

and then 

init 2

---

