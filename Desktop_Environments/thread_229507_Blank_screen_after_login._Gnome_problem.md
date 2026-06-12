---
title: "Blank screen after login. Gnome problem?"
date: 2006-08-04
forum: Desktop Environments
---

### Post by Strolls on 2006-08-04
Hi there,

I hope someone can help, because I've never seen this one before. I have just installed the latest version of Unbuntu on an old Pentium 3; the install seemed to go fine & when I reboot the machine I see the Ubuntu logo & box in which to enter my username.

The problem is that after I enter my username & password the screen goes blank - all I see is the white pointer and it remains like this indefinitely.
I am able to return to the logon screen only by connecting via SSH and killing the process of "x-window-manage"

I am convinced the problem is not with X11 because I do actually get a login screen which [looks like this]("http://www.ccs.neu.edu/home/jabra/install-docs-ubuntu_files/image032.jpg").
I think that this screen is actually produced by GDM - does this indeed indicate that X11 is running normally?

I know the problem is not authentication because I can log on with the same username & password via SSH.

If I remove .dmrc  .gconf/ .gconfd/ and .xsession-errors then they are recreated when I log in:

```
freecycler@ubuntu:~$ ls -a
.  ..  .bash_history  .dmrc  .gconf  .gconfd  .xsession-errors
freecycler@ubuntu:~$ rm -rf .dmrc .gconf .gconfd/ .xsession-errors 
freecycler@ubuntu:~$ ls -a
.  ..  .bash_history
freecycler@ubuntu:~$ ls -la
total 32
drwxr-xr-x 4 freecycler freecycler 4096 2006-08-04 19:06 .
drwxr-xr-x 3 root       root       4096 2006-08-01 10:58 ..
-rw------- 1 freecycler freecycler  264 2006-08-04 03:27 .bash_history
-rw------- 1 freecycler freecycler   26 2006-08-04 19:06 .dmrc
drwx------ 2 freecycler freecycler 4096 2006-08-04 19:06 .gconf
drwx------ 2 freecycler freecycler 4096 2006-08-04 19:06 .gconfd
-rw------- 1 freecycler freecycler  117 2006-08-04 19:06 .Xauthority
-rw-r--r-- 1 freecycler freecycler  268 2006-08-04 19:06 .xsession-errors
freecycler@ubuntu:~$ ls -la /home/
total 12
drwxr-xr-x  3 root       root       4096 2006-08-01 10:58 .
drwxr-xr-x 21 root       root       4096 2006-08-01 09:56 ..
drwxr-xr-x  4 freecycler freecycler 4096 2006-08-04 19:06 freecycler
freecycler@ubuntu:~$
```I don't know what "normal" looks like for this file, but .xsession-errors looks ok to me:```

freecycler@ubuntu:~$ cat .xsession-errors 
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "freecycler"
/etc/gdm/Xsession: Beginning session setup...
freecycler@ubuntu:~$
```

The following file gets created at boot-up, before I log in:
```
freecycler@ubuntu:~$ cat /var/log/gdm/\:0.log

X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.12 i686
Current Operating System: Linux ubuntu 2.6.15-23-386 #1 PREEMPT Tue May 23 13:49:40 UTC 2006 i686
Build Date: 16 March 2006
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Aug  4 19:22:18 2006
(==) Using config file: "/etc/X11/xorg.conf"
dlopen: /usr/lib/xorg/modules/extensions/libGLcore.so: undefined symbol: __glXLastContext
(EE) Failed to load /usr/lib/xorg/modules/extensions/libGLcore.so
(EE) Failed to load module "GLcore" (loader failed, 7)
error opening security policy file /etc/X11/xserver/SecurityPolicy
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
freecycler@ubuntu:~$
```Could this be related?
I'm thinking particularly of the line "error opening security policy file"

This machine seems to have a Voodoo 3 graphics card:
```
freecycler@ubuntu:~$ sudo lspci -v -d  121a:0005 
0000:01:00.0 VGA compatible controller: 3Dfx Interactive, Inc. Voodoo 3 (rev 01) (prog-if 00 [VGA])
        Subsystem: 3Dfx Interactive, Inc.: Unknown device 103a
        Flags: 66MHz, fast devsel, IRQ 11
        Memory at f6000000 (32-bit, non-prefetchable) [size=32M]
        Memory at fc000000 (32-bit, prefetchable) [size=32M]
        I/O ports at 9000 [size=256]
        Capabilities: [54] AGP version 1.0
        Capabilities: [60] Power Management version 1

freecycler@ubuntu:~$
```
This would appear to be specified correctly in the xorg.conf (attached). This is actually the xorg.conf copied from the Ubuntu 5.10 LiveCD running on the same hardware - this boots to the desktop perfectly - but I get the same problem with the xorg.conf which was installed by 6.06 from the install CD.

Any suggestions very gratefully received. As you may have guessed from the prompts I only want to install Ubuntu on this machine so I can give it away as a complete machine with an o/s installed. There's no Windows licence sticker on this PC and I hope that giving computers away for free with Linux preinstalled will help "spread the word". But the time I'm wasting doing this is not a pleasure or a chore that I'll ever see the benefit of, so this problem is quite annoying!!

Stroller.

---

### Post by Anduu on 2006-08-04
Well judging from the error loading GLCore this could be the culprit....

Try commenting it out under the modules section of your xorg.conf and see what happens....I know a lot of 3D cards don't require GLCore to function...my ATI doesn't...

---

### Post by Strolls on 2006-08-06
> **Anduu said:**
> Well judging from the error loading GLCore this could be the culprit....

Try commenting it out under the modules section of your xorg.conf and see what happens...
Sorted! Many thanks.
For the benefit of Google the relevant line is that with "glx" in it - a hash at the start of the line & all worked perfectly.  :D

Stroller.

---

### Post by ManLord on 2006-08-13
I think i have the same problem, but it doesn't help to comment out the glx line..

As with strolls, I get the loginscreen and after that I see the "progress bar" with the different items beeing loaded. But it only show the window manager icon and nothing more happens. If i click the "progress bar" it dissapears.

I have no idea what to do.. If anyone could help me I would be grateful. I have no idea how to access logs or anything, but give a pointer and I will post them.

---

### Post by difranr on 2006-08-15
This happened to me as well, and what I did was login in via the "Fail Safe Mode" of GNOME and ran **dpkg**.  I forget the exact options, but I did a **sudo apt-get update** and it told me what the correct options were.  Once I did that and re-started my server it worked like a champ.

---

### Post by Strolls on 2006-08-15
> **ManLord said:**
> ...As with strolls, I get the loginscreen and after that I see the "progress bar" with the different items beeing loaded.
Actually, I didn't even get the progress bar - just a blank screen and the pointer.

> **ManLord said:**
> ... I have no idea what to do.. If anyone could help me I would be grateful. I have no idea how to access logs or anything, but give a pointer and I will post them.
Posting logfiles may be helpful - in fact these days I often find them informative enough that I resolve things for myself.

You can access a shell using on of the [virtual terminals]("http://www.tuxfiles.org/linuxhelp/shortcuts.html") by pressing Ctrl, Alt and one of the function keys together. Ctrl + Alt + F7 gets you back to the X session.

You should be able to copy log files to /mnt/floppy and post relevant extracts here (or in a new thread).

Stroller.

---

