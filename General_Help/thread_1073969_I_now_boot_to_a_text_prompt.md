---
title: "I now boot to a text prompt?"
date: 2009-02-18
forum: General Help
---

### Post by jmclein on 2009-02-18
Everything was working fine and dandy.  I turned my laptop off at work, brought it home and booted it back up 20 mins later but now my ubuntu is loading up to a text prompt.

When I turn it on it does it's bios check, then it gives me the option for ubuntu or windows XP (I installed with WUBI).  I select ubuntu just like I always have and I get the splash screen but then it goes to a text prompt that say -

Booting Ubuntu 8.10 Kernel 2.6.27-11-generic
Filesystem type is ntfs, partition type 0x07
The current working directory (i.e, the relative path) is /ubuntu/disks  A few other lines

Loading, please wait
ubuntu 8.10 tty1

Ubuntu login:


Ummm, what happened?

---

### Post by mikewu on 2009-02-18
It could be that gdm isn't starting up. After you get to that screen press Ctrl-Alt-F7. That should switch you to the first graphical terminal which you are usually on. 

If you want a one time fix so you can access things more easily, log into that terminal and type startx. That should start up x on virtual terminal 7.

Otherwise, check dmesg and other system logs to see if gdm or anything else failed at bootup.

---

### Post by jmclein on 2009-02-18
I hit ctrl-alt-ft and it switched to a screen with a blinking cursor in the upper left hand corner of the screen and is just sitting there.  I can type but thats it.

---

### Post by mikewu on 2009-02-18
Do that same thing again. Then type exec gnome-session. This should launch gnome. Then check the logs and we'll try to help you from there.

---

### Post by jmclein on 2009-02-18
> **mikewu said:**
> Do that same thing again. Then type exec gnome-session. This should launch gnome. Then check the logs and we'll try to help you from there.

When I typed that it said **(gnome-session:5545): Waring**: Cannot open display:

---

### Post by mikewu on 2009-02-18
Okay kill vt7 with Ctrl-Alt-Backspace
Go back to the first virtual terminal with ctrl-alt-F1
xinit -- :0 vt7
This should start x with the display variable set to 0 and on virtual terminal 7
then 
exec gnome-session

Hopefully that gets gnome working.

---

### Post by jmclein on 2009-02-18
> **mikewu said:**
> Okay kill vt7 with Ctrl-Alt-Backspace
Go back to the first virtual terminal with ctrl-alt-F1
xinit -- :0 vt7
This should start x with the display variable set to 0 and on virtual terminal 7
then 
exec gnome-session

Hopefully that gets gnome working.

ctrl alt backspace isnt doing anything for me.

---

### Post by jmclein on 2009-02-18
ctrl alt f1 doesnt do anything either.

---

### Post by jmclein on 2009-02-18
> **jmclein said:**
> ctrl alt backspace isnt doing anything for me.I take that back. ctrl-alt-backspace just type [^H

---

### Post by jmclein on 2009-02-19
I'm not sure if bumping is allowed here but I guess this is a bump as my I am still having the same issue.  Can anyone help?

---

### Post by crazyfuturamanoob on 2009-02-19
Maybe try to reinstall Ubuntu? (and copy important stuff into a memory stick first)

---

### Post by jmclein on 2009-02-19
> **crazyfuturamanoob said:**
> Maybe try to reinstall Ubuntu? (and copy important stuff into a memory stick first)

This install is only 2 days old.  I would much rather find out what happened as opposed to having to re-install a pretty much brand new install.

---

### Post by perpetualcacophany on 2009-02-19
The same thing happened to me yesterday on my new install. When you get to the prompt give it your username and password then type:

```
sudo dpkg-reconfigure -phigh xserver-xorg
sudo startx
```

It worked for me.

Hope it helps.

---

### Post by jmclein on 2009-02-19
> **perpetualcacophany said:**
> The same thing happened to me yesterday on my new install. When you get to the prompt give it your username and password then type:

```
sudo dpkg-reconfigure -phigh xserver-xorg
sudo startx
```

It worked for me.

Hope it helps.

That fixed it!! Thank you for your help!

---

