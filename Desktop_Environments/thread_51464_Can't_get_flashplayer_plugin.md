---
title: "Can't get flashplayer plugin"
date: 2005-07-24
forum: Desktop Environments
---

### Post by harrisxml on 2005-07-24
When I try and get the FlashPlayer plugin for Firefox I get this:

```
harrisxml@harrisxml:~$ sudo apt-get install flashplayer-mozilla
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
``` 

What is wrong and how do I fix it?

Also, I am attempting to install the new version of Mozilla Firefox (this is a seperate issue that I am thinking of addressing so it is not causing problems for the above issue) and I have the package downloaded and sitting on my desktop.  How do I install it?  Could I please have the code for use in Terminal that I will be entering?

---

### Post by NeoChaosX on 2005-07-24
You don't happen to have Synaptic or another apt-get process running while you're installing it, by any chance, do you? That error comes up if you try to use apt in the terminal when another program like Synaptic is open. Close/kill any other processes that could be using apt, then try again.

Is the Firefox package you downloaded the one you can get from mozilla.org?

---

### Post by harrisxml on 2005-07-24
I download the new Firefox from [http://www.getfirefox.com](http://www.getfirefox.com).  Version 1.06.  Here's what's happening now:
```
harrisxml@harrisxml:~$ sudo apt-get install flashplayer-mozilla
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package flashplayer-mozilla
harrisxml@harrisxml:~$
``` 

Am I missing a source or something (this also ocurrs when I attempt to do "sudo apt-get install sun-j2re1.5")?

---

### Post by NeoChaosX on 2005-07-24
Did you enable the universe and multiverse repositories in /etc/apt/sources.list? Since Flash isn't free software, Ubuntu has it in the Multiverse repos. [This link](http://ubuntuguide.org/#extrarepositories) tells you how to enable universe and multiverse.

And to install that package:
1. Go to the directory you downloaded the package in
2. **sudo tar -xvzf firefox-1.0.6.installer.tar.gz**
3. **cd ./firefox-installer**
4. **sudo ./firefox-installer**

---

### Post by harrisxml on 2005-07-24
How do I enable the Universe Multiverse repositories?  I added sources to my list at [Www.ubuntuguild.org](Www.ubuntuguild.org)...  But obviously that didn't do much for me.

Here's what happens when I try to install the new Firefox using your method (thank you BTW).

```
harrisxml@harrisxml:~/Desktop/firefox-installer$ sudo ./firefox-installer

(firefox-installer-bin:8873): Gdk-WARNING **: locale not supported by Xlib

(firefox-installer-bin:8873): Gdk-WARNING **: can not set locale modifiers

(firefox-installer-bin:8873): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-installer-bin:8873): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-installer-bin:8873): Gtk-WARNING **: /usr/lib/gtk-2.0/2.4.0/engines/libclearlooks.so: cannot open shared object file: No such file or directory

** (firefox-installer-bin:8873): WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
** (firefox-installer-bin:8873): WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
** (firefox-installer-bin:8873): WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
** (firefox-installer-bin:8873): WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
** (firefox-installer-bin:8873): WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
** (firefox-installer-bin:8873): WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
** (firefox-installer-bin:8873): WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
** (firefox-installer-bin:8873): WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
** (firefox-installer-bin:8873): WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
** (firefox-installer-bin:8873): WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
** (firefox-installer-bin:8873): WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-installer-bin:8873): GLib-GObject-CRITICAL **: file gobject.c: line 1561 (g_object_ref): assertion `G_IS_OBJECT (object)' failed

** (firefox-installer-bin:8873): CRITICAL **: file pango-engine.c: line 68 (_pango_engine_shape_shape): assertion `PANGO_IS_FONT (font)' failed

** ERROR **: file shape.c: line 75 (pango_shape): assertion failed: (glyphs->num_glyphs > 0)
aborting...
./firefox-installer: line 56:  8873 Aborted                 ./${BINNAME}-bin $@
```

---

### Post by NeoChaosX on 2005-07-24
By adding what was on Ubuntu Guide, you enabled Multiverse. Now it's just a matter of installing flashplayer-mozilla again.

Try running **./firefox-installer**, without the sudo and tell me what happens.

---

### Post by NeoChaosX on 2005-07-24
In fact, now that I think about it, it would be a smarter idea NOT to install the Firefox package from mozilla.org. Sure, it's up-to-date, but it will conflict with the already-installed version of Firefox included with Ubuntu. Plus, since you seem to have added the new repositories in /etc/apt/sources.list, you should be able to install the Firefox included with Ubuntu to 1.0.4 with apt.

---

### Post by harrisxml on 2005-07-24
I run "sudo apt-get install mozilla-firefox" and it tells me that I already have the newest version.  This is contradictory because when i go to Help>>About Mozilla Firefox it tells me that I am using 1.02...  And I still can't get J2RE or Flash plugin...

```
root@harrisxml:/ # sudo apt-get install sun-j2re1.5
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package sun-j2re1.5
root@harrisxml:/ # sudo apt-get install flashplayer-mozilla
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package flashplayer-mozilla
root@harrisxml:/ #
```

---

### Post by NeoChaosX on 2005-07-24
Paste the contents of your /etc/apt/sources.list file here. Let's see what's up?

---

### Post by harrisxml on 2005-07-24
If it helps my system is AMD64.

```
deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release amd64 (20050407)]/ hoary main restricted


deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to fetch updated software from the network
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted
```

---

### Post by NeoChaosX on 2005-07-24
Okay, *that* explains it. There's no Flash plugin for AMD64 Linux right now.

---

### Post by harrisxml on 2005-07-24
What about Java???  Why is it giving me that error?

---

### Post by NeoChaosX on 2005-07-24
No 64-bit version of the Java plugin, either. Sorry, dude.

---

### Post by harrisxml on 2005-07-24
Ah damn.  That really sucks.  I TRULY appreciate all of your help.  :)

---

