---
title: "Send in the Cleaner - part 2"
date: 2009-04-12
forum: General Help
---

### Post by MartinHansell on 2009-04-12
Hi...

_[Send in the Cleaner Pt 1](http://ubuntuforums.org/showthread.php?t=1122641)_  led me to produce the output below as a starter towards solving my problem... which is this >>

When I installed my latest version of (I Love) Ubuntu, I copied over my backup files to my home folder, but when the system finished they weren't there...  At the time something wasn't right (derrrr) (but I can't remember what... coz it was a while ago now), and it may have been that I was not logged in properly (don't ask how) - or something equally weird.

Anyhow, I figured I would just copy the lot over again and (after a small test) I managed to do that.  Only thing is... of course... then I had used up twice as much space on my hard disk as I had needed.  But when I searched to delete the first set of files they were nowhere to be found.  I figured it would become an issue when I started to run out of space... and guess what?  Yep!  My, how time flies when you're having fun.

So far I have taken a look at some of the obvious things, like my "hidden" files (which everyone knows exactly how to "un-hide").  And I did a quick check of the sizes of directories on my system (see below) which mainly tells me what I know... my disk is verging on full.

So, how do I find out where these byte-sized bandits are skulking and drive them off my precious merry-go-round?  Send in the Cleaner?

Many thanks in eager anticipation...

> 
mangoking@Mangostine:/$ sudo du -s /*
6228	/bin
24000	/boot
0	/cdrom
3112	/dev
15964	/etc
du: cannot access `/home/mangoking/.gvfs': Permission denied
10571112	/home
0	/initrd.img
0	/initrd.img.old
191752	/jmemorize
215860	/lib
16	/lost+found
350763138	/media
4	/mnt
4	/opt
du: cannot access `/proc/22061/task/22061/fd/3': No such file or directory
du: cannot access `/proc/22061/task/22061/fdinfo/3': No such file or directory
du: cannot access `/proc/22061/fd/3': No such file or directory
du: cannot access `/proc/22061/fdinfo/3': No such file or directory
0	/proc
8793940	/root
8528	/sbin
28	/scripts
13750660	/sgml
104784	/sgml_useless
4	/srv
0	/sys
392	/tmp
4418548	/usr
20142948	/var
0	/vmlinuz
0	/vmlinuz.old
mangoking@Mangostine:/$ 


---

### Post by lloyd_b on 2009-04-12
What exactly is in "/root"?  This directory is normally VERY small.  8GB for it seems way out of line.

Are you running a web server on that box?  Unless you are, the "/var" directory seems outlandishly huge.

Lloyd B.

---

### Post by MartinHansell on 2009-04-12
Thanks for the response Lloyd,

Yes I am running a web server and mysql within /var hence its size.

Here is the output from ls -a on root...

> 
Mangostine:/root$ ls -a.
..
.bash_history
.bashrc
.bashrc~
.bluefish
.cache
.config
.dbus
Desktop
.esd_auth
.fr-bCAP9b
.gconf
.gconfd
.gegl-0.0
.gimp-2.6
.gnome2
.gnome2_private
.gstreamer-0.10
.gtk-bookmarks
.kino-history
.kinorc
.local
.mozilla
.nautilus
.openoffice.org2
.profile
.pulse
.pulse-cookie
.recently-used
.recently-used.xbel
.synaptic
.thumbnails
.tvtime
.wapi


---

### Post by lloyd_b on 2009-04-12
Okay, it looks like you have an actual "root" account enabled on that machine.

I really can't tell anything from that list of directories - run a "du" in that directory and see where that space is being used. 

Lloyd B.

---

### Post by MartinHansell on 2009-04-12
Am I doing this right?

1 -  I switched to root using sudo su
2 -  I did the listing below...

root@Mangostine:/# du > /home/mangoking/root.txt
du: cannot access `./proc/24448/task/24448/fd/3': No such file or directory
du: cannot access `./proc/24448/task/24448/fdinfo/3': No such file or directory
du: cannot access `./proc/24448/fd/3': No such file or directory
du: cannot access `./proc/24448/fdinfo/3': No such file or directory


and I got a massive list of files including many of  ./var/www/files and even old backups off another hard disk...?? See a small sample of the first chunk of lines attached as root2.txt

cheers.

---

### Post by MartinHansell on 2009-04-12
...did u get the attachment?

---

### Post by lloyd_b on 2009-04-13
First off, I didn't see any attachment.

Second - what I suggested you do is run "du" *while in the "/root" directory*(i.e., after doing a "cd /root"), so that you'd only see the files in that directory and below it.  It'll still be a fairly long list, though.

You could also do a "du -s" in that directory, and look for any subdirectories that are unusually large.  Then "cd" into that subdirectory, and repeat, until you find a directory with a large number of files or some exceptionally large individual files.

Lloyd B.

---

