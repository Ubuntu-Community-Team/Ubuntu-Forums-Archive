---
title: "Gtk-WARNING **:   Refusing to Initialize GTK+"
date: 2008-01-25
forum: Desktop Environments
---

### Post by notrump3 on 2008-01-25
I just ran the install updates and when I returned to my machine, it was off.  This could have been a power blip, but now it is giving me this after the login screen...

>  
(process: 7605): Gtk-WARNINGG **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must creat a helper program instead.  Fur further details, see:

	[http://www.gtk.org/setuid.html](http://www.gtk.org/setuid.html)

Refusing to initialize GTK+.

(process: 7608): Gtk-WARNINGG **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must creat a helper program instead.  Fur further details, see:

	[http://www.gtk.org/setuid.html](http://www.gtk.org/setuid.html)

Refusing to initialize GTK+.
/etc/gdm/Xsession: Beginning session setup...
/usr/bin/gnome-session: error while loading shared libraries: /usr/lib/libavahi-common.so.3: file too short


I've searched on various components of this error and can't seem to find anything that is applicable or that will work.

Base Environment Info
compaq D510 - Running Gutsy x86

This is a fairly simple install of desktop with no fancy peripherals and has been working really well since feisty initially.  Let me know what other info is required to troubleshoot...

I can get to a terminal session, but that's it...

Any help is appreciated.

---

### Post by PeterJS on 2008-01-25
So what happened is your system shut down with the update manager still running. The update manager was running with elevated privilages when the system shutdown, so the session manager saved it in that state. Now that you're trying to restart, the session manager is try to restart the update manager with eleveated privilages, and GTK is rightly refusing to let it do so.

To fix this delete the gnome session file located at:
~/.gnome2/session

Or if you're looking for more precision, open it up and cut out the section for the update manager

And then try logging in again.

---

### Post by notrump3 on 2008-01-26
I can't seem to find a session file in the ~/.gnome2 directory.  I cd to the directory, but there is no such file or folder there.  Am I missing something?

---

### Post by breaking on 2008-01-27
PeterJS, I'm having this problem too and I'm certain you can't be right because I don't use the option for the session manager to save what programs I have open.  Obviously I also don't have a ~/.gnome2/session file.

Any other suggestions please?

---

### Post by PeterJS on 2008-01-27
Sorry guys it would appear I have misdiagnosed the problem, I don't know what to tell you. My only suggestion would be setting up a new account, and migrating settings over a few at a time until it breaks.

---

### Post by Seisen on 2008-01-27
Did either one of you two run anything as root instead of using sudo?

---

### Post by ispy on 2008-01-27
I have the same problem. i get the error "Your session only lasted less than 10 seconds, if you have not logged out yourself, this could mean that there is some installation problem or that you may be out of diskspace. Try logging in with one of the failsafe sessions to see if you can fix this problem."

this was after i completely removed Enlightenment from my system, (in enlightenment), and logged out and back in. I tried to recover from a live CD, but I can't. also, when I log in at a "failsafe session", it only gives me a terminal, nothing else, so if anyone has an idea how to fix this, it has to be in the terminal. thanks!!

---

### Post by evilc on 2008-01-27
This problem with GTK+ has been around since Gutsy released, you will find hundreds of queries on the net regarding this and as far as I know no fixes around.
If you think you didn't  have it before try booting with live CD then in Nautilus check the home folder for  xsession-error. If it's there you can bet it's the bug.

---

### Post by notrump3 on 2008-01-28
> **Seisen said:**
> Did either one of you two run anything as root instead of using sudo?

I've done everything as sudo where I'd ve tried.  I did su to root to look for the session file, incase there was something I was missing, but I did not execute anything as root.

My upgrade to gutsy worked for the last 3 weeks, something else must've happened in the last upgrade or as noted my upgrade was hit with a power blip, but there has got to be a way to fix this.

---

### Post by perixx on 2008-01-28
Perhaps it's worth trying ```
sudo dpkg-reconfigure -phigh xserver-xorg
```
If nothing else works, I'd try to re-install the desktop:```
sudo apt-get install ubuntu-desktop --reinstall
``` But maybe someone has a better solution...

perixx

---

### Post by notrump3 on 2008-01-28
> **perixx said:**
> Perhaps it's worth trying ```
sudo dpkg-reconfigure -phigh xserver-xorg
```
If nothing else works, I'd try to re-install the desktop:```
sudo apt-get install ubuntu-desktop --reinstall
``` But maybe someone has a better solution...

perixx

I tried these as well as "sudo apt-get install --reinstall libavahi-common3"...

the error I received was as follows (the error part was the same when I tried to reinstall the desktop, jsut the top part was a little different)...

> 
Reading package lists... Done
Buidling Dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 8 not upgraded
15 not fully installed or removed
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue[Y/n]y
Setting up libisc32 (1:9.4.1-P1-3ubuntu1) ...
dpkg (subrpocess): unable to execute post-installation script: Exec format error
dpkg: errror processin libisc32 (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of libdns32:
 libdns32 depends on libisc32; however:
  Package libisc32 is not configured yet.
dpkg: error processing libdns32 (--configure):
 dependency probelms - leaving unconfigured
dpkg: dependency problems prevent configuration of libisccc30:
 libisccc30 depends on libisc32; however:
  Package libisc32 is not configured yet.
dpkg: error processing libisccc30 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libisccfg30:
 libisccfg30 depends on libdns32; however:
  Package libdns32 is not configured yet.
 libisccfg30 depends on libisc32; however:
  Package libisc32 is not configured yet.
 libisccfg30 depends on libiscc30; however:
  Package libiscc30 is not configured yet.
dpkg: error processing libisccfg30 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libbind9-30:
 libbind9-30 depends on libdns32; however:
  Package libdns32 is not configured yet.
 libbind9-30 depends on libisc32; however:
  Package libisc32 is not configured yet.
 libbind9-30 depends on libisccfg30; however:
  Package libisccfg30 is not configured yet.
dpkg: error processing libbind9-30 (--configure):
 dependency problems - leaving unconfigured
Setting up liblwres30 (1:9:4.1-P1-3ubuntu1) ...
dpkg (subrpocess): unable to execute post-installation script: Exec format error
dpkg: error processing liblwres30 (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of bind9-host:
 bind9-host depends on libbind9-30; however:
  Package libbind9-30 is not configured yet.
 bind9-host depends on libdns32; however:
  Package libdns32 is not configured yet.
 bind9-host depends on libisc32; however:
  Package libisc32 is not configured yet.
 bind9-host depends on libisccfg30; however:
  Package libisccfg30 is not configured yet.
 bind9-host depends on liblwres30; however:
  Package liblwres30 is not configured yet.
dpkg: error processing bind9-host (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of dnsutils:
 dnsutils depends on libbind9-30; however:
  Package libbind9-30 is not configured yet.
 dnsutils depends on libdns32; however:
  Package libdns32 is not configured yet.
 dnsutils depends on libisc32; however:
  Package libisc32 is not configured yet.
 dnsutils depends on libisccfg30; however:
  Package libisccfg30 is not configured yet.
 dnsutils depends on liblwres30; however:
  Package liblwres30 is not configured yet.
 dnsutils depends on bind9-host; however:
  Package liblwres30 is not configured yet.
  Package host is not installed.
  Package bind9-host which provides host is not cnofigured yet.
dpkg: error processing dnsutils (--configure):
 dependency problems - leaving unconfigured
Setting up avahi-autoipd (0.6.20-2ubuntu3.2) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing avahi-autoipd (--configure):
 subprocess post-installation script returned error exit status 2
Setting up libavahi-common3 (0.6.20-2ubuntu3.2) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing libavahi-common3 (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of libavahi-core5:
 libavahi-core5 depends on libavahi-common3 (>= 0.6.10); however:
  Packafe libavahi-common3 is not configured yet.
dpkg: error processing libavahi-core5 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of avahi-daemon:
 avahi-daemon depends on libavahi-common3; however:
  Packafe libavahi-common3 is not configured yet.
 avahi-daemon depends on libavahi-core5; however:
  Packafe libavahi-core5 is not configured yet.
dpkg: error processing avahi-daemon (--configure):
 dependency problems - leaving unconfigured
Setting up libgs8 (8.61.dfsg.1\svn8187-0ubuntu3.3) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing libgs8 (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of ghostscript:
 ghostscript depends on libgs8; however:
  Packafe libgs8 is not configured yet.
dpkg: error processing ghostscript (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libavahi-compat-libdnssd1:
 libavahi-compat-libdnssd1 depends on libavahi-common3 (>= 0.6.10); however:
  Packafe libavahi-common3 is not configured yet.
dpkg: error processing libavahi-compat-libdnssd1 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libisc32
 libdns32
 libisccc30
 libisccfg30
 libbind9-30
 liblwres30
 bind9-host
 dnsutils
 avahi-autoipd
 libavahi-common3
 libavahi-core5
 avahi-daemon
 libgs8
 ghostscript
 libavahi-compat-libdnssd1
E: Subprocess /usr/bin/pkg returned an error code (1)


---

### Post by perixx on 2008-01-28
Hm. My last guess would be to re-install the GTK-package and try to fix dependencies with apt-get....
> sudo apt-get update -f to auto-fix packages, if I'm not mistaken.

perixx

---

### Post by notrump3 on 2008-01-29
I gave up!  I archived my home folders, and re0installed over top of my root and boot partition.  the first time it seemed to work until I ran the update and then the browser and open office wouldn't open (it started to with the tab in the bottom line, but then just went away).  I've just reinstalled for the second time and I'm only updating the security update, fingers crossed... thanks to everyone who tried to help, I appreciate the effort.

---

### Post by perixx on 2008-01-29
I myself had too much trouble installing 7.10 in the first place. Sticked to Feisty for the time being. Maybe Hardy'll be my 'hero' :]

perixx

---

### Post by besson3c on 2008-01-29
I'm having this problem too, but only with a particular user on this system oddly enough. I tried deleting all non-essential dot directories in my home directory to try to restore my home directory to no avail.

Any advice as to how I can track down this specific home directory problem?

---

### Post by perixx on 2008-01-30
Well, then I hope your problem is kind of 'solved'? Perhaps you could mark the thread as solved, then...

perixx;)

---

### Post by besson3c on 2008-01-30
I solved the problem by copying all of the dot directories out of a new account into my damaged account. This worked.

---

### Post by perixx on 2008-01-30
Maybe re-installing were a 'cleaner' solution :)

perixx

---

### Post by robinm on 2008-02-06
Okay, I can also confirm this problem :(. But the problem did (yes, I fixed it...) not exist on itself. Another error message that was there was that it could not make a certain temporary directory. I think the normal security mode of /tmp was not 1777 (sticky) but something else. This problem really caught my attention when I tried to read a man-page in a failsafe terminal in X.

My 'fix' was just:

sudo chmod 1777 /tmp

My other linux computer (this) also has 1777 as standard setting, but not sure if it is a safe setting because users (may?) see other users' private data in temp files (? not sure). However, everybody (me...) who logs into my computer is considered safe so I could safely do this thing.

Hope I can help anybody with this 'fix'. I really don't know how this setting has changed, but now it works...for now ;)
:guitar:

EDIT:
one more thing to mention: the problem occured not only on one user, but when trying to log in any user.

---

### Post by silentph03nix on 2008-02-13
Well, I got this error and saw a post regarding my /tmp file. I looked again and at the very bottom of the error message I was getting was this:  ```
mkdtemp: private socket dir: Permission denied
```  I logged in via console and my /tmp was set to dr_xr_xr_x_  which is not correct so I ran ```
sudo chmod 1777 /tmp
```  This fixed my problem and I was able to login.  Hope this helps some folks out there who get this  error.

---

