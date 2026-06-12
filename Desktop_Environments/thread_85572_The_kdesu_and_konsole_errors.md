---
title: "The kdesu and konsole errors"
date: 2005-11-03
forum: Desktop Environments
---

### Post by hualala on 2005-11-03
I just install kubuntu for two or three days.The first time I used it ,it worked well.
Now three problem come:
1,I cannot use kdesu,
when I use adept or other system tools,after i input the password,it says,cannot find the the program "su",please check your "PATH".
But i can use sudo or su in console ,I am sure $PATH has no problem
2.The konsole don't accept any input.the cursor freezes and there is no prompt.
when i start konsole in xterm ,it says:
kdecore(KProcess):WARNING:Can't open a pseudo teletype
I can use kdesu and konsole by:
sudo konsole
sudo kdesu adept (for example)
I works normal when sudo.
3.I used to mount iso files to local filesystem.but now it reports cannot find /dev/loop( I fix it by "sudo modprobe loop",but why it happens????)

I donnot know how these problems come ,Maybe because I shut the kde with ctrl+alt+backspace with konsole and adept still open??

---

### Post by ltmon on 2005-11-03
Possibly.

One thing you can try is:

> kbuildsycoca

This tries to reconfigure KDE (including lots of the stuff that is normally cached from your last session).

L.

---

### Post by hualala on 2005-11-03
I format my hard disk and install kubuntu again,reboot again and again.
Finally I find that:
If I install 
linux-image-2.6.12-9-386 linux-restricted-modules-2.6.12-9-386 linux-restricted-modules-common
and enter the system using 2.6.12 kernel
then the two problems will come.
if I using 2.6.10-5-386,nothing will happen except the usplash donnot work.

Is this a bug??
Anyone else see it too?

---

### Post by hualala on 2005-11-03
by the way,I used to use ubuntu 5.10(gnome) with 2.6.12 kernel in my computer.
so,It seems to be the problem about kde

---

