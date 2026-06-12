---
title: "Session lasts less than 10 seconds"
date: 2007-10-05
forum: Desktop Environments
---

### Post by lvijay on 2007-10-05
Hi

I'm on Ubuntu Gutsy Gibbon 7.10 beta and things were fine until today.  There were some software updates (I don't remember which) and after that I've been having the common "Session lasted less than 10 seconds error".  However my problem does not seem to be the same as what other users have had, which I why I'm posting.

My desktop environment is Gnome.

I have enough space:

-------------
/home/vijay $ df -h

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2             9.9G  4.8G  4.6G  52% /
varrun                502M   92K  502M   1% /var/run
varlock               502M     0  502M   0% /var/lock
udev                  502M   64K  502M   1% /dev
devshm                502M     0  502M   0% /dev/shm
lrm                   502M   34M  468M   7% /lib/modules/2.6.22-12-generic/volatile
/dev/sda3              24G   15G  8.0G  65% /home
-------------

My error seems to be related to some program running setgid() and setuid() in GTK+ which, apparently, isn't necessary.

-------------
/home/vijay $ cat .xsession-errors 

(process:10807): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    [http://www.gtk.org/setuid.html](http://www.gtk.org/setuid.html)

Refusing to initialize GTK+.

(process:10811): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    [http://www.gtk.org/setuid.html](http://www.gtk.org/setuid.html)

Refusing to initialize GTK+.
/etc/gdm/Xsession: Beginning session setup...
/etc/gdm/Xsession: 165: xmodmap: not found
/etc/gdm/Xsession: 191: ls: not found
/etc/gdm/Xsession: Executing /usr/bin/gnome-session failed, will try to run x-terminal-emulator
exec: 204: x-terminal-emulator: not found
-------------

I couldn't tell which process causes the problem though.

This is my system:
-------------
/home/vijay $ uname -a

Linux balrog 2.6.22-12-generic #1 SMP Sun Sep 23 18:11:30 GMT 2007 i686 GNU/Linux
-------------

I even did "sudo apt-get install xubuntu-desktop" and tried logging into an xfce session but even that failed.

Please tell me if you need more information.  Any assistance appreciated.

Thanks
Vijay

---

