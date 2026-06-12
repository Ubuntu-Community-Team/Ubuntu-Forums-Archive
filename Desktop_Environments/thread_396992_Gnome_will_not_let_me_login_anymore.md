---
title: "Gnome will not let me login anymore"
date: 2007-03-30
forum: Desktop Environments
---

### Post by rolando on 2007-03-30
Hi
I am using Edgy Eft.

I was messing around with my hosts and hostname file (trying to install zimbra) and now gnome will not let me login.  (It logs in then tells me my last session lasted less than 10 seconds, etc)

Anyway here is the xsessions error it produces.

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "rolando"
/etc/gdm/Xsession: Beginning session setup...
/etc/X11/Xsession.d/55gnome-session_gnomerc: line 4: [: `)' expected, found /usr/bin/gnome-session
Could not init font path element /usr/share/fonts/X11/TTF/, removing from list!
Could not init font path element /usr/share/fonts/X11/OTF, removing from list!
Could not init font path element /usr/share/fonts/X11/CID/, removing from list!
/usr/bin/startxgl.sh: line 2: exec: gnome-session: not found

I have restored my hosts and hostname file to their former glory, but still no luck

My interface lo is set up:
 auto lo in /etc/network/interfaces

I have tried to re-install ubuntu-desktop with apt-get via command line but get this error:

ubuntu-desktop: Depends x org but is not going to be installed.

I was using Beryl, so maybe it something to do with that


I am at a bit of a loss what to do next, has anyone got any ideas?

Thanks in advance 

Rolando

---

### Post by ComplexNumber on 2007-03-30
unfortunately, i don't know what to do in your circumstances with regard to the hosts and hostfile. i haven't met that situation before so i can't go from experience. 
but i have encountered the "the session lasted less than 10 seconds".for me, it was because i overloaded my home directory, so there was very little memory left on my home partition. low memory can cause that error message, but i've heard other causes can be:
-a problem with the .ICEauthority file in the home directory. this can sometimes be caused by using sudo instead of gksudo for running graphical applications. i think this needs to be deleted before attempting login again.
-a problem with permissions somewhere. sometimes the home directory. sometimes the /tmp directory.

---

### Post by rolando on 2007-03-30
Thanks

None of the above im afraid

du -h shows I have 24GB used up I have a 60GB hard drive, none of my partitions are even near 90% so i cant be that

Deleted the .ICEAuthority no luck either

Ill check the permissions on my home dir and tmp, but cant see it being that

Luckily i installed Enlightenment a while back but never used it - I am now!!

Cheers

Rolando

---

### Post by rolando on 2007-03-31
ok fixed it

I used enlightenment and run gnome-panel, synaptic etc and re-installed ubuntu-desktop after getting my house in order as far as my repositories went

All is well with the world

Now to fix the wireless in the 2.6.17.11 upgrade as its broken now.

:)

---

