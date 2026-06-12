---
title: "Administrative password lost"
date: 2009-04-27
forum: Dell Ubuntu Support (CLOSED)
---

### Post by trp on 2009-04-27
Hello everyone!

Recently purchased a used dell mini 910 running Ubuntu 8.04.1, Hardy Heron.  The previous owners (about 2 months) could not remember setting up an administrative password, so as a result I cannot download upgrades or even add users, every option is blocked out (not an active icon)> I have gone on several help sites each says to get into boot menu and select Recovery Mode.  When I boot, the boot menu shows no option for recovery mode so I am stuck.  I do have the Dell CD and driver so I could do a fresh install but that seems so drastic.  Any suggestions?  Thanks in advance.  PS I am new to Ubuntu so am not totally familiar with this OS yet.  

Tom

---

### Post by coffeeaddict22 on 2009-04-28
Hi,
Messing around with the root password isn't good form.  Ubuntu is a little bit different to most Linux distro's: the root account is hidden.  However, the first user set up after install is given administrative access. The previous users will have had a password to log in; this will have given them root access when used with sudo.

---

### Post by bapoumba on 2009-04-28
If you have your own account on the machine, please boot in recovery mode at grub menu (hit escape to see the menu if hidden):
```
adduser <insert_your_username_here> admin
reboot
```
Then your user should have be able to gain admin privilege with sudo or gksudo.

---

### Post by sahabcse on 2009-04-28
login to your system user

then type in terminal
#sudo bash

It will login to root mode

There type 

#passwd (for changing root user password)

---

### Post by trp on 2009-04-28
> **bapoumba said:**
> If you have your own account on the machine, please boot in recovery mode at grub menu (hit escape to see the menu if hidden):
```
adduser <insert_your_username_here> admin
reboot
```
Then your user should have be able to gain admin privilege with sudo or gksudo.
 
 
 Here is the problem.  I can`t set up an account under users.  All the icons are inactive.  I can not add or remove any users listed.  (There is only one-the admin).  Any attempted changes requires the admin`s password which is unknown.  When I boot the system and hit 0 or 2 (o takes me to the boot menu but nowhere do I see an option for recovery mode or a way to type text in the terminal (if I`m even in the terminal)  learning Linux will take some time after Windows based systems.  I`m not sure what the grub menu shouild look like.  Any further elaboration would be very useful.  Sorry for being such a newbee.

---

### Post by gbrainin on 2009-04-28
Well, first of all let's make sure you're looking at the right boot menu.  Many Dell computers have a boot option where you hit an F key (F2 or F11 or whatever) that puts you in a menu where you can select what source to boot from (hard drive, CD, memory stick, whatever).  That's not the boot menu we're talking about.

After the BIOS boots up, you should briefly get an opportunity to view the GRUB boot menu.  Depending on how the system is set up, the menu may appear, or you may need to hit ESC to make it appear.  The GRUB menu is an old-fashioned text-mode list of different options for booting from the hard drive.  It will have entries something like (exact text may be different):

Ubuntu, kernel 2.6.16-25-386
Ubuntu, kernel 2.6.16-25-386 (recovery mode)
[and so on]

You can use the arrow keys to scroll down the list and enter to select the highlighted item.  That is the boot menu we're talking about, and if you're not seeing that, you need to find it.

Again, there may be only a brief time that the screen says to hit ESC to see the menu.  Unfortunately, some systems are set for this time period to be as little as 0 seconds, which can make it tricky (but not impossible) to hit ESC at the right time.

If you're seeing the right menu, and there is still no recovery mode option, then come back and say so, and someone should be able to make another suggestion.

---

### Post by trp on 2009-04-29
Thank you for all your suggestions!  I have been a slave to windows my entire life with just a little dos here and there.  So far I am enjoying this new OS and thanks to members like yourself, am learning how to manage it so one day I may be able to provide suppoprt on this forum and return the favor.
 
Thanks again!

---

