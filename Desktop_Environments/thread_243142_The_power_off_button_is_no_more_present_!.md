---
title: "The power off button is no more present !"
date: 2006-08-24
forum: Desktop Environments
---

### Post by The_Artist on 2006-08-24
Hello everybody,

I have a problem, when I quit Ubunu Dapper, the shut down button is no more present ! He was there before... Do you know why ?

Now i have to log off and come bach to the login screen... then choose shut down...


Then in advance for your help !

---

### Post by mdwuznik on 2006-08-24
Such things happen if you run more than one Xserver on your machine (e.g. Xgl started as "normal Xorg"sessiong, not Xgl from the very start). Could you post the result of "ps aux |grep X" from "just before willing to shutdown "?

---

### Post by The_Artist on 2006-08-25
So that's the answer for your command :

```
angelo@shuttle:~$ ps aux |grep X
root      4417  0.5  2.7  17744 14100 tty7     SLs+ 07:31   0:00 /usr/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
angelo    4887  5.7 12.1  70408 62780 ?        SL   07:31   0:07 Xgl -fullscreen :1 -ac -accel glx:pbuffer -accel xv:pbuffer
angelo    5264  0.0  0.1   2932   828 pts/0    S+   07:33   0:00 grep X
angelo@shuttle:~$

```

I specially start my PC this morning to do this task... so it would be curious to find several X sessions...

Thanks in advance !

---

### Post by The_Artist on 2006-08-25
Something very strange :
I usually use a XGL session, the one with I have this problem.

Just to try, i log on a normal gnome session, and yet the shut down button is there... ??!!! That's the result for the command in this case :

```
angelo@shuttle:~$ ps aux |grep X
root      4417  1.3  3.9  25032 20240 tty7     SLs+ 07:31   0:06 /usr/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
angelo    5940  0.0  0.0   1632   508 pts/0    R+   07:39   0:00 grep X
angelo@shuttle:~$

```

---

### Post by The_Artist on 2006-08-25
You seems to be right, there is one more session with the XGL case, and now, what can I do ?

---

### Post by mdwuznik on 2006-08-25
Have a look at /etc/gdm/gdm.conf-custom. 
Do you have :
0=Standard
1=Xgl 
there ?(and [servers-Xgl]section below), or you launch Xgl the other way round ?

---

### Post by tribaal on 2006-08-25
Same problem here when using Xgl.

I've been looking around but cannot seem to find a definitive workaround. Is there a way to tell Ubuntu to start only XGL or only X, and to never start both at the same time? That seems to be the issue, from what I gathered from other threads.

Help :)

- trib'

---

### Post by mdwuznik on 2006-08-25
Yes, there is, I start Xgl only on my machine.
(gdm.conf-custom way, starting only 0=Xgl server)

---

### Post by tribaal on 2006-08-25
Could you please post me your gdm.conf-custom?

Mine is kind of... empty. I mean there is stuff written in it but nothing about xgl (mostly style and colors and stuff).

Thanks a lot!

- trib'

---

### Post by The_Artist on 2006-08-25
So, that's my gdm.conf-custom file :

```
# GDM Configuration Customization file.
#
# This file is the appropriate place for specifying your customizations to the
# GDM configuration.   If you run gdmsetup, it will automatically edit this
# file for you and will cause the daemon and any running GDM GUI programs to
# automatically update with the new configuration.  Not all configuration
# options are supported by gdmsetup, so to modify some values it may be
# necessary to modify this file directly by hand.
#
# To hand-edit this file, simply add or modify the key=value combination in
# the appropriate section in the template below.  Refer to the comments in the
# gdm.conf file for information about each option.  Also refer to the reference
# documentation.
#
# If you hand edit a GDM configuration file, you should run the following
# command to get the GDM daemon to notice the change.  Any running GDM GUI
# programs will also be notified to update with the new configuration.
#
# gdmflexiserver --command="UPDATE_CONFIG <configuration key>"
#
# For example, the "Enable" key in the "[debug]" section would be specified by
# "debug/Enable".
#
# You can also run gdm-restart or gdm-safe-restart to cause GDM to restart and
# re-read the new configuration settings.  You can also restart GDM by sending
# a HUP or USR1 signal to the daemon.  HUP behaves like gdm-restart and causes
# any user session started by GDM to exit immediately while USR1 behaves like
# gdm-safe-restart and will wait until all users log out before restarting GDM.
#
# For full reference documentation see the gnome help browser under
# GNOME|System category.  You can also find the docs in HTML form on
# http://www.gnome.org/projects/gdm/
#
# NOTE: Lines that begin with "#" are considered comments.
#
# Have fun!

[daemon]
AutomaticLoginEnable=true
AutomaticLogin=angelo

[security]

[xdmcp]

[gui]

[greeter]

[chooser]

[debug]

[servers]


```

---

### Post by tribaal on 2006-08-25
Hum so where is the 0= Xgl thing? I'm confused now :(

- trib'

---

### Post by The_Artist on 2006-08-25
Mdwuznik : The two lines you are asking for don't appear in this file...

I have installed XGL with a french wiki, and this method allow me to choose wich graphic engine i want to start... Maybe is it the source of my problem ?

---

### Post by tribaal on 2006-08-25
Do you have a link to that? (oui, je parle français) :)

- trib'

---

### Post by mdwuznik on 2006-08-25
No, I won't post mine, there's more than plenty of them here :).
The thread I was trying to give you a hint to is:
[http://www.ubuntuforums.org/showthread.php?t=131267](http://www.ubuntuforums.org/showthread.php?t=131267) 
You'll find proper gdm.conf-custom there (mine's the same).
With that, you'll have Xgl as default (and only running Xserver if you  log in to _normal_ session, not the special Xgl one, which you probably created and use it nested inside Xorg)

Good luck:)

Micha&#322;

---

### Post by mdwuznik on 2006-08-25
tribaal:Another way of launching Xgl, which existed in some guides was creating a separate _session_, where you start normal Xorg where gdm lives, and login into a nested Xgl server with gnome-session in it.There's no 0=Xgl line than, and there's no power button there due to two Xservers running :)
This wiki shows this way:
[http://www.tectonic.co.za/view.php?id=916](http://www.tectonic.co.za/view.php?id=916) (sorry, I do not have time to dig into the forums for equivalent...)
If you did so, I think that creating the gdm.conf-custom the XGL way and logging into _normal_ session, not the custom-created one on :1 display will get the power button back for our unlucky colleague.

---

### Post by The_Artist on 2006-08-28
Thanks Tribaal.

The french url I use to learn about XGL installation :
[http://doc.ubuntu-fr.org/applications/xgl/gnome]("http://doc.ubuntu-fr.org/applications/xgl/gnome")

---

### Post by tribaal on 2006-08-28
[Here is]("http://ubuntuforums.org/showthread.php?t=245152") the thread that helped me sort out everything.

Hope this 'll help someone.

- trib'

---

### Post by The_Artist on 2006-08-28
OK, thanks Tribaal I try and keep you informed !

---

### Post by The_Artist on 2006-08-28
OK, I have a look on the tutorial that you quoted, tribaal, but that doesn't help me solving my problem... :-(

I precise I have a gdm config that allows me to choose between a normal Gnome session or a XGL one...

So I used something like the etap 2 when I installed XGL (my tutorial was in fact a traduction it seems), but these lines doesn't help me to solve my problem... I always start with two X sessions... root and my user...

"that helped me sort out everything." => Could you say more, please ?

Thanks in advance... and if someone has an idea, don't hesitate... thanks in advance !!!

---

