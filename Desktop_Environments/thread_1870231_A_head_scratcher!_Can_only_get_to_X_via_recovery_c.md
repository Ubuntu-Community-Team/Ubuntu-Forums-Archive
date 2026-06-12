---
title: "A head scratcher! Can only get to X via recovery console"
date: 2011-10-26
forum: Desktop Environments
---

### Post by W00ster on 2011-10-26
This has become somewhat of a head scratcher for me.

Upgraded my box from 11.04 to 11.10, not smooth I have to add.
I then installed the latest ATi Catalyst 11.9 and now the puzzle starts. I had Catalyst installed under 11.04 too and had no issues whatsoever.

Now, if I boot, I get the normal ubuntu start screen before you actually get to the login manager. Then the screen goes blank and my monitor goes into hibernation as no signal can be found. I can not even switch to a text console using ALT+Fx

If I boot, but go into Grub and select recovery console and wait for the text menu, then select resume normal boot, everything works like a charm, I get the login manager screen and can work as normal!

Anyone else seen anything like it?

My box has an Intel Extreme Edition 12 core CPU with an Ati 5770HD card.

---

### Post by collisionystm on 2011-10-26
> **W00ster said:**
> This has become somewhat of a head scratcher for me.

Upgraded my box from 11.04 to 11.10, not smooth I have to add.
I then installed the latest ATi Catalyst 11.9 and now the puzzle starts. I had Catalyst installed under 11.04 too and had no issues whatsoever.

Now, if I boot, I get the normal ubuntu start screen before you actually get to the login manager. Then the screen goes blank and my monitor goes into hibernation as no signal can be found. I can not even switch to a text console using ALT+Fx

If I boot, but go into Grub and select recovery console and wait for the text menu, then select resume normal boot, everything works like a charm, I get the login manager screen and can work as normal!

Anyone else seen anything like it?

My box has an Intel Extreme Edition 12 core CPU with an Ati 5770HD card.

Join the club off the less fortunate ATI owners.

There is a bad problem with X, Gnome3 and ATI.

I suggest you roll on back to something more stable unless you want to hang around on the edge. You can find a lot of posts that discuss the problems you are having.

[http://askubuntu.com/questions/68245/ubuntu-hits-a-black-screen-after-boot](http://askubuntu.com/questions/68245/ubuntu-hits-a-black-screen-after-boot)

However, I do have a question. When you installed fglrx, did you open a terminal and do sudo aticonfig --initial -f

If not, after doing it, try to reboot like normal. 

Also, remove xserver-xorg-video-ati

---

### Post by W00ster on 2011-10-27
> **collisionystm said:**
> Join the club off the less fortunate ATI owners.

Cheers! :)

> **collisionystm said:**
> 
However, I do have a question. When you installed fglrx, did you open a terminal and do sudo aticonfig --initial -f

If not, after doing it, try to reboot like normal. 

Also, remove xserver-xorg-video-ati

Actually, yes I did do this and it runs fine at 1920x1080 as long as I go the route around the recovery console.

I'll guess I'll just back out of the fglrx driver.

---

### Post by unobtruse on 2011-10-27
I have a Radeo HD 3400, but after replacing the "fglrx" from /etc/X11/xorg.conf with "radeon", my system worked fine again. I did this using the Ctrl-Alt-F1 non-X terminal ang logging into my usual account.

The problem I have now is that after fiddling around further with the ati drivers, trying to get fglrx "totally" removed, I get the login screen but am unable to login to the user account on which I changed these settings last. I enter my password en hit return, then the screen flashes around a bit and returns the lightDM login as if nothing happened... 

I am able to login to another account I created afterwards. It's really annoying. Please help!

---

### Post by unobtruse on 2011-10-27
> **unobtruse said:**
> I have a Radeo HD 3400, but after replacing the "fglrx" from /etc/X11/xorg.conf with "radeon", my system worked fine again. I did this using the Ctrl-Alt-F1 non-X terminal ang logging into my usual account.

The problem I have now is that after fiddling around further with the ati drivers, trying to get fglrx "totally" removed, I get the login screen but am unable to login to the user account on which I changed these settings last. I enter my password en hit return, then the screen flashes around a bit and returns the lightDM login as if nothing happened... 

I am able to login to another account I created afterwards. It's really annoying. Please help!
I managed to solve my problem. See: [http://ubuntuforums.org/showthread.php?t=1870180](http://ubuntuforums.org/showthread.php?t=1870180) .

Hope you manage W00ster.

---

### Post by W00ster on 2011-10-27
Well.. <scratch scratch>...

$ cd ~
$ ls -la .Xauthorization
ls: cannot access .Xauthorization: No such file or directory
$ ls -la .X*
-rw------- 1 w00ster w00ster 271 2011-10-27 16:28 .Xauthority

---

### Post by W00ster on 2011-11-02
The problem has been resolved.

To fix any similar issues, download and install ati-driver-installer-11-10-x86.x86_64.run, remove the old driver, install the new and reboot.

---

