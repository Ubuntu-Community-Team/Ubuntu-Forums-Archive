---
title: "kde applications requiring password can't start from icon"
date: 2007-08-14
forum: Desktop Environments
---

### Post by zl2k on 2007-08-14
hi, there

I am using kubuntu feisty and got the problem that those kde applications requiring password (such as synaptic package manager etc.) can't be started by clicking the application icon from the menu after input the correct password. But they can be started by typing "sudo ..." in the terminal. 

The kubuntu never behaved like this before and I don't remember I did anything wrong. I did nothing but restart the computer many times, sometime I can start the application by click the icons but most time I can't. Please help.

zl2k

---

### Post by misfitpierce on 2007-08-15
Sometimes its possible for the icon to just bounce but not load program.. It hangs for too long then cancels out. This rarely happens to me but when it does I just click the program icon again and it'll load right up.

---

### Post by kellemes on 2007-08-15
> **zl2k said:**
> hi, there

I am using kubuntu feisty and got the problem that those kde applications requiring password (such as synaptic package manager etc.) can't be started by clicking the application icon from the menu after input the correct password. But they can be started by typing "sudo ..." in the terminal. 

The kubuntu never behaved like this before and I don't remember I did anything wrong. I did nothing but restart the computer many times, sometime I can start the application by click the icons but most time I can't. Please help.

zl2k

Try "gksu synaptic" from the command line and see what happens.

Edit: KDE is it? So try..
"kdesu synaptic"

---

### Post by zl2k on 2007-08-15
sudo, gksu are all fine with synaptic.
kdesu synaptic got the problem:
kdesu synaptic
xauth: (argv):1:  bad display name ":0.0" in "list" command
kdesu (kdelibs): WARNING: No X authentication info set for display :0.0
xauth: (argv):1:  bad display name ":0.0" in "list" command
kdesu (kdelibs): WARNING: No X authentication info set for display :0.0

---

### Post by Prefader on 2007-08-15
This is a known bug, I'll hunt around launchpad for the bug report link.  My understanding of what's happening is this:

kdesu uses sudo to authenticate, and sudo has a timeout on the session it starts.  kdesu is getting confused by this timeout and fails to authenticate.

One fix is to edit your sudoers file (type "sudo visudo" in a terminal) and add

timestamp_timeout=0

to the "Defaults" line.  Mine looks like this:

Defaults        !lecture,tty_tickets,!fqdn,timestamp_timeout=0

The upshot is that the session created by the sudo command ends immediately, and so kdesu can authenticate just fine.  The downside is that you'll need to enter your password every time you use the "sudo" command.  Hope that helps.

Launchpad bug here: [https://bugs.launchpad.net/ubuntu/+source/kdebase/+bug/72545](https://bugs.launchpad.net/ubuntu/+source/kdebase/+bug/72545)

---

