---
title: "HELP URGENT: Messed up my system"
date: 2009-09-11
forum: Desktop Environments
---

### Post by futureal2032 on 2009-09-11
Hi,
i am on Jaunty

and iw as using it fine ..

i installed my nvidia drivers from 8400gs and enabled compiz and its effects
and it was working fine..

then i decided to change the looks of my desktop so i followed this tutorial from here ..

[http://ubuntuforums.org/showthread.php?t=1209904&highlight=create+image+installed+ubuntu](http://ubuntuforums.org/showthread.php?t=1209904&highlight=create+image+installed+ubuntu)

(I followed the post installation parts)

then i set gnome-do and disabled gnome-panel (By disabling its "execute" permissions)..but after reboot gnome-do wont start, i got a blank desktop..so i managed to re-enable gnome-panel again from terminal changing its permissions using chmod.

Now my ubuntu desktop is back but now i have following problems

1. Synapitc package manager does not start. When i click on it nothing happens.

2. My desktop effects are disabled. When i try to enable dekstop effects..it gives me error "No drivers found" cannont enable desktop effects"

3. I tried to uninstall gnome-do via terminal using command "sudo apt-get remove gnome-do"
it gave me error
"sudo: must be setuid root"

4. I find out if i try to use any command it gives me that same error
"sudo: must be setuid root"

Can anyone please help me in getting back to my priginal desktop??

---

### Post by futureal2032 on 2009-09-11
UPDATE: managed to solve first part of my problem

I booted in the recovery console

and types following

"chown root:root /usr/bin/sudo"
"chmod 4755 /usr/bin/sudo"
chmod 4755 /bin/su"

This solved my Synaptic Problem..it is opening now and i uninstalled gnome-do too.

and the commands have started working again interminal

but i still cant enable desktop effects..

---

### Post by earthpigg on 2009-09-11
> (I followed the post installation parts)

you need to be much more specific than that.

***_exactly_*** what was the status of your system before you started running commands you did not understand?

***_exactly_*** which random commands from some random forum post written by some random and untrusted potential Al Queda operative did you run?

do not ever run things as root (sudo ...) unless you understand *every* *_single_* ***_part_*** of the command.

i will now quote myself, in large and red letters:
> 
[SIZE="5"][COLOR="Red"]do not ever run things as root (sudo ...) unless you understand *every* *_single_* ***_part_*** of the command.[/COLOR][/SIZE]

---

### Post by futureal2032 on 2009-09-11
> **earthpigg said:**
> you need to be much more specific than that.

***_exactly_*** what was the status of your system before you started running commands you did not understand?

***_exactly_*** which random commands from some random forum post written by some random and untrusted potential Al Queda operative did you run?

do not ever run things as root (sudo ...) unless you understand *every* *_single_* ***_part_*** of the command.

i will now quote myself, in large and red letters:

thanks for the warning...already know that.... i read all the replies in that post i mentioned and after reading user opinions i did everything
by the way that tutorial is good but i realised it is not for Nvidia at least not in its present form.

so i had to install Nvidia drivers from scratch again..but now i have no probs with my system...

besides...if you dont tinker with the system a little..you ar not going to learn new things..mainly trouble shooting.

---

