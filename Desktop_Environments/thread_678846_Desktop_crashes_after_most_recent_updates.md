---
title: "Desktop crashes after most recent updates"
date: 2008-01-26
forum: Desktop Environments
---

### Post by neonedge9 on 2008-01-26
After running the software updates yesterday, I can no longer login using a Gnome session. I have not made any other changes to the system since then that would cause it, and creating a new user has the same effect. The system is behind a firewall, so I know it isn't a compromise or anything. Again, the only thing that has changed is that update installed a bunch of new libraries, and modified xcore. Here is the error messages:
==================================================================
(process:6700): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    [http://www.gtk.org/setuid.html](http://www.gtk.org/setuid.html)

Refusing to initialize GTK+.

(process:6704): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    [http://www.gtk.org/setuid.html](http://www.gtk.org/setuid.html)

Refusing to initialize GTK+.
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/laser:/tmp/.ICE-unix/6697
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0322 (rev a1) (prog-if 00 [VGA])
Checking for texture_from_pixmap: Initializing gnome-mount extension
The application 'gnome-session' lost its connection to the display :0.0;
most likely the X server was shut down or you killed/destroyed
the application.
not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: nautilus: Fatal IO error 104 (Connection reset by peer) on X server :0.0.
==================================================================

And here are the packages that were modified yesterday:
==================================================================
drwxr-xr-x    2 root root  4096 2008-01-25 18:35 libisccfg30
drwxr-xr-x    2 root root  4096 2008-01-25 18:35 libisccc30
drwxr-xr-x    2 root root  4096 2008-01-25 18:35 libisc32
drwxr-xr-x    2 root root  4096 2008-01-25 18:35 libdns32
drwxr-xr-x    2 root root  4096 2008-01-25 18:35 libbind9-30
drwxr-xr-x    2 root root  4096 2008-01-25 18:35 liblwres30
drwxr-xr-x    2 root root  4096 2008-01-25 18:35 libavahi-core5
drwxr-xr-x    2 root root  4096 2008-01-25 18:35 libavahi-common-data
drwxr-xr-x    2 root root  4096 2008-01-25 18:35 libavahi-common3
drwxr-xr-x    2 root root  4096 2008-01-25 18:35 dnsutils
drwxr-xr-x    2 root root  4096 2008-01-25 18:35 bind9-host
drwxr-xr-x    2 root root  4096 2008-01-25 18:35 avahi-autoipd
drwxr-xr-x    2 root root  4096 2008-01-25 18:35 libavahi-compat-libdnssd1
drwxr-xr-x    2 root root  4096 2008-01-25 18:35 libavahi-client3
drwxr-xr-x    3 root root  4096 2008-01-25 18:35 avahi-daemon
drwxr-xr-x    2 root root  4096 2008-01-25 18:35 libgs8
drwxr-xr-x    2 root root  4096 2008-01-25 18:35 ghostscript
drwxr-xr-x    2 root root  4096 2008-01-25 18:35 libavahi-glib1
drwxr-xr-x    2 root root  4096 2008-01-25 18:35 ghostscript-x
lrwxrwxrwx    1 root root    10 2008-01-25 18:35 cupsys-bsd -> libcupsys2
drwxr-xr-x    2 root root  4096 2008-01-25 18:35 libxfont1
drwxr-xr-x    2 root root  4096 2008-01-25 18:35 libboost-thread1.34.1
drwxr-xr-x    2 root root  4096 2008-01-25 18:35 libboost-filesystem1.34.1
drwxr-xr-x    2 root root  4096 2008-01-25 18:35 libavahi-qt3-1
drwxr-xr-x    2 root root  4096 2008-01-25 18:35 xserver-xorg-core
drwxr-xr-x    3 root root  4096 2008-01-25 18:35 libcupsys2
==================================================================

As of right now, when I login as any user with a Gnome desktop, the login sound starts to play, and then it crashes back to the login page. xfce is working fine, and Gnome-failsafe seems to work.
Any help appreciated.

---

### Post by neonedge9 on 2008-01-26
Additional Information: It seems that the theme is bad. This from messages & daemon.log:
=====================================================================
Jan 26 11:51:26 laser gdmgreeter[7757]: WARNING: Theme broken: must have pam-message label! 
Jan 26 11:51:31 laser gdm[7557]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 
Jan 26 11:51:40 laser gdmgreeter[7931]: WARNING: Theme broken: must have pam-message label! 
=====================================================================

How do I select a new theme when I can't login to gnome?

---

### Post by bongoboi on 2008-01-26
Same thing is happening here. At first I thought it was some compiz badness, but i removed all compiz packages and the problem persists. I ran a failsafe gnome session so i can get an xterm and ran all the commands in /usr/share/gnome/default.session and they all seem to work, but then when i run gnome-session i'm kicked back to gdm login screen. At this point i'm clueless about what's going on.

---

### Post by astoltz on 2008-01-26
Have you installed a newer Nvidia driver?  The Xorg update overwrote one of the files the in the nvidia driver causing X to crash.

---

### Post by breaking on 2008-01-27
Can you provide more details please, astoltz?  What solution are you suggesting?

I have this same problem, but which NVidia driver I use doesn't seem to affect it... I'm using the new 169.09 drivers, but I tried downgrading back to 169.07 (which used to work fine), and it doesn't affect anything at all.  I also tried reinstalling xserver-xorg-core, in case that helped, but again it doesn't have any effect.   All I know is I applied some automatic updates and now I can't login except with the failsafe session!

Other threads have suggested cleaning out ~/.gnome2/session, but I don't have that file, or cleaning out xfce4 init files, but I'm using Gnome not xfce4.

Anyone have any more suggestions as to where I should be looking to narrow down the problem further?

---

### Post by astoltz on 2008-01-27
I was having the same issue - X crashed right after logging in.  Turns out that the xserver-xorg-core update overwrote the file: /usr/lib/xorg/modules/extensions/libglx.so.  That file is causing the new nvidia drivers (169.07) to crash and bring down X - it should be a symbolic link that points to the nvidia version.  So **after** updating xorg, the following fix worked for me. ```
cd /usr/lib/xorg/modules/extensions/
sudo mv libglx.so libglx.so.old
sudo ln -s libglx.so.169.07 libglx.so
```Yours may not be the same problem since you say you upgraded to 169.09 which is supposed to have fixed this issue.  But it's worth checking.

---

