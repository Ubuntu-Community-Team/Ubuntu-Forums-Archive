---
title: "help!! - cannot log-in: my username seem to be deleted after installing virtualbox!"
date: 2007-05-29
forum: Desktop Environments
---

### Post by chikko on 2007-05-29
hey guys - i really need your help here:

i'm using Kubuntu 7.04 for quite a long time now (used to have the alpha version before the final has come out) and hadn't any problems before.
about half an hour ago i installed VirtualBox (using automatix2) and after the installation was succeeded it told me to reboot in order to use the software.  so i did.
after the boot sequence i suddenly saw the login screen (although i configured the system to login automatically) and so i entered my username and password - which "weren't current"! :(
i tried to hit the "switch user" button in the login-options menu and could only see "Unused" instead of user names (i'm not sure i should have seen any users there, but..)
so now i'm stuck outside my system and don't know what to do!!  help!! :(

**_IMPORTANT (after editing):_**
when i try and login with a non-existing user, or an incorrect password - i get a red "LOGIN FAILED" messege right away - but when i try and log in with my username and the correct password - the screen tries to change resolution, waits for about a second or so - and then shows the login screen again - which means, i guess, that my user was not deleted after all..

**_another update:_**
i tried hitting alt+ctrl+F4 and log-in without the X - i succeeded to see my files.  the user still exists after all.
i also tried sudo aptitude remove virtualbox - but after removing and alt-ctrl-F7 the login was no different than what i described above.. :(

p.s.
i already succeeded in installing VirtualBox on my laptop's kubuntu 7.04 in the exact same way..  no problems happened there..


appreciate any help what-so-ever..
thanks,
chikko.

---

### Post by seshomaru samma on 2007-05-29
mmm
try to log in as root , by rebooting and choosing the 'recovery mode' from the grub menu
if it lets you login as root then.....

not sure really....sorry
maybe uninstall virtualbox?

---

### Post by chikko on 2007-05-29
> **seshomaru samma said:**
> mmm
try to log in as root , by rebooting and choosing the 'recovery mode' from the grub menu
if it lets you login as root then.....

not sure really....sorry
maybe uninstall virtualbox?

thanks for replying, seshomaru samma.
unfortunately i've got a cordless keyboard - so i cannot choose the safe mode option in grub (merde..)..
already tried to uninstall virtualbox - no changes..
root login is possible, ofcourse - but only in konsole mode - no GUI what-so-ever.. :(

---

### Post by bodhi.zazen on 2007-05-29
> **chikko said:**
> hey guys - i really need your help here:

i'm using Kubuntu 7.04 for quite a long time now (used to have the alpha version before the final has come out) and hadn't any problems before.
about half an hour ago i installed VirtualBox (using automatix2) and after the installation was succeeded it told me to reboot in order to use the software.  so i did.

This is highly unusual behavior for VirtualBox. One does not need to reboot after installing VirtualBox.

My suggestion is your problem is with Automatix and not virtualbox.

Perhaps post on their forum and describe your problem.

---

### Post by arnieboy on 2007-05-29
> **bodhi.zazen said:**
> This is highly unusual behavior for VirtualBox. One does not need to reboot after installing VirtualBox.

My suggestion is your problem is with Automatix and not virtualbox.

Perhaps post on their forum and describe your problem.
One does need to reboot after installing Virtual Box.. 
and the problem is not with Automatix.

---

### Post by arnieboy on 2007-05-29
> **chikko said:**
> hey guys - i really need your help here:

i'm using Kubuntu 7.04 for quite a long time now (used to have the alpha version before the final has come out) and hadn't any problems before.
about half an hour ago i installed VirtualBox (using automatix2) and after the installation was succeeded it told me to reboot in order to use the software.  so i did.
after the boot sequence i suddenly saw the login screen (although i configured the system to login automatically) and so i entered my username and password - which "weren't current"! :(
i tried to hit the "switch user" button in the login-options menu and could only see "Unused" instead of user names (i'm not sure i should have seen any users there, but..)
so now i'm stuck outside my system and don't know what to do!!  help!! :(

**_IMPORTANT (after editing):_**
when i try and login with a non-existing user, or an incorrect password - i get a red "LOGIN FAILED" messege right away - but when i try and log in with my username and the correct password - the screen tries to change resolution, waits for about a second or so - and then shows the login screen again - which means, i guess, that my user was not deleted after all..

**_another update:_**
i tried hitting alt+ctrl+F4 and log-in without the X - i succeeded to see my files.  the user still exists after all.
i also tried sudo aptitude remove virtualbox - but after removing and alt-ctrl-F7 the login was no different than what i described above.. :(

p.s.
i already succeeded in installing VirtualBox on my laptop's kubuntu 7.04 in the exact same way..  no problems happened there..


appreciate any help what-so-ever..
thanks,
chikko.

The problem is not because of Virtual Box (that has nothing to do with gdm failures).. The issue might be related to kernel upgrades that you got recently from Ubuntu.. Do you have an nvidia card by any chance?
also if possible please paste the results of the following command:
```
cat /home/**your_user_name**/.xsession-errors
```
One other thing: Are you using Beryl/Compiz?

---

### Post by sameat on 2007-05-29
How did you add yourself to the vboxusers group?  I once used usermod without the -a switch and removed myself from every group I was in.  It caused some major headaches.

Check your group membership.  If the account truly doesn't exit, it won't help.

Just a thought.

---

### Post by chikko on 2007-06-01
hey again guys.

first of all - i wanna thank you all for trying to help.
indeed - i have an Nvidia card and it was a kubuntu software upgrade which cause all the mess.  i managed to fix it by removing the nvidia driver (a restore command given by the automatix installation helper) - so it's all good now.
i wanna apologize to VirtualBox - i know it wasn't your fault!  how did i ever question you..? :)

thanks again.

---

