---
title: "Gnome-session takes a long time"
date: 2007-11-14
forum: Desktop Environments
---

### Post by Angafirith on 2007-11-14
I've read about issues similar to this one, but I didn't find anything exactly like what I'm experiencing.

Basically, I got a new laptop about a week ago. It's a Compaq Presario F712us or something along those lines. It's an AMD Athlon 64 X2 (dual-core) machine. When I boot my machine, the usplash phase of startup goes incredibly fast, faster than I've ever seen. When I login, the desktop comes up almost immediately, except for one exception: nm-applet and gnome-power-manager take at least a minute to load after I get to the desktop. I find this somewhat frustrating, and I'd like to resolve it somehow.

Originally, I thought that it was just that NetworkManager and HAL were taking a long time, but I noticed something odd. When I use Control + Alt + Backspace to end an X session and log back in, it still takes a long time for them to start, even when I know that NetworkManager is already running and has not crashed.

When I start nm-applet from a console, it starts immediately. In fact, I find that it is far faster to do this than to wait for it to start on its own.

Any ideas on what I can do about this?

---

### Post by Angafirith on 2007-11-15
I hate to double post, but does anyone have any ideas? It's kind of disheartening to see a thread sink like this.

---

### Post by Angafirith on 2007-11-19
Anyone? It's getting to be a sort of a problem for me: Screenlets (which are added to the gnome session) take so long to load that it seriously impacts their usefulness.

Even the slightest idea of where to look would be appreciated.

---

### Post by TeaSwigger on 2007-11-20
Well I honestly have no idea. I don't have a 64-bit unit, plus I use kubuntu. But to try and help... Let's see. 

Screenlets added to the gnome session? Not using gnome that much, what are they? Are they the problem? Can you disable them and check the boot? If it boots ok without 'em, that'd be where to look...

You're using the 32-bit version on a 64-bit laptop? Might that be related in some obscure way? That's certainly reaching, but there is a sub forum oriented to 64-bit support, and if you're really striking out, you may want to try there.

---

### Post by Angafirith on 2007-11-20
I appreciate your response. I've posted 4 or 5 threads on various support forums about various issues, with almost no responses.

Screenlets are best explained by [this website]("http://screenlets.org/index.php/Home"), I think.

The problems I'm experiencing are not really related to the screenlets, though. I've been having this problem all along, but only installed screenlets recently. It's that screenlets are negatively impacted by it. Anything in my gnome-session takes a long time to start, which includes the screenlets, nm-applet, gnome-power-manager, and more. I've tried disabling everything in my gnome startup, to no avail. Oddly enough, all the panel applets come up immediately.

I don't think it's because I'm using the 32-bit version instead of the 64-bit. It actually used to be recommended that people do this; Flash and Java didn't used to have reasonably good 64-bit versions.

---

### Post by frojnd on 2007-11-20
I have a similar problem :S  But this wasn't from the beginning. Before ubuntu goes to login manager there is a black screen and it says smth about sensor-limis [FAIL] and when I press my username and password it needs like 3mins to load all the icons (Gutsys's search manager and network-manager) And at the beginning when this icons finally loads if I press any program like terminal it takes more time as before. 

As before, cause I don't know when or why this started to happening.....

Here is my "sudo grep -R sensors /var/log" output:

```
/var/log/apt/term.log:Selecting previously deselected package lm-sensors.

/var/log/apt/term.log:Unpacking lm-sensors (from .../lm-sensors_1%3a2.10.4-1ubuntu1_i386.deb) ...

/var/log/apt/term.log:Setting up lm-sensors (1:2.10.4-1ubuntu1) ...

/var/log/apt/term.log:Creating config file /etc/sensors.conf with new version

/var/log/dpkg.log.1:2007-10-29 17:42:39 install libsensors3 <none> 1:2.10.4-1ubuntu1
/var/log/dpkg.log.1:2007-10-29 17:42:39 status half-installed libsensors3 1:2.10.4-1ubuntu1
/var/log/dpkg.log.1:2007-10-29 17:42:39 status unpacked libsensors3 1:2.10.4-1ubuntu1
/var/log/dpkg.log.1:2007-10-29 17:42:39 status unpacked libsensors3 1:2.10.4-1ubuntu1
/var/log/dpkg.log.1:2007-10-29 17:46:17 configure libsensors3 1:2.10.4-1ubuntu1 1:2.10.4-1ubuntu1
/var/log/dpkg.log.1:2007-10-29 17:46:17 status unpacked libsensors3 1:2.10.4-1ubuntu1
/var/log/dpkg.log.1:2007-10-29 17:46:17 status half-configured libsensors3 1:2.10.4-1ubuntu1
/var/log/dpkg.log.1:2007-10-29 17:46:17 status installed libsensors3 1:2.10.4-1ubuntu1
/var/log/dpkg.log:2007-11-02 14:55:04 install lm-sensors <none> 1:2.10.4-1ubuntu1
/var/log/dpkg.log:2007-11-02 14:55:04 status half-installed lm-sensors 1:2.10.4-1ubuntu1
/var/log/dpkg.log:2007-11-02 14:55:04 status unpacked lm-sensors 1:2.10.4-1ubuntu1
/var/log/dpkg.log:2007-11-02 14:55:04 status unpacked lm-sensors 1:2.10.4-1ubuntu1
/var/log/dpkg.log:2007-11-02 14:55:05 configure lm-sensors 1:2.10.4-1ubuntu1 1:2.10.4-1ubuntu1
/var/log/dpkg.log:2007-11-02 14:55:05 status unpacked lm-sensors 1:2.10.4-1ubuntu1
/var/log/dpkg.log:2007-11-02 14:55:05 status unpacked lm-sensors 1:2.10.4-1ubuntu1
/var/log/dpkg.log:2007-11-02 14:55:05 status unpacked lm-sensors 1:2.10.4-1ubuntu1
/var/log/dpkg.log:2007-11-02 14:55:05 status half-configured lm-sensors 1:2.10.4-1ubuntu1
/var/log/dpkg.log:2007-11-02 14:55:05 status installed lm-sensors 1:2.10.4-1ubuntu1
/var/log/auth.log:Nov 20 12:12:10 joze sudo:     joze : TTY=pts/0 ; PWD=/var/log ; USER=root ; COMMAND=/bin/grep -R sensors /var/log
/var/log/auth.log:Nov 20 12:12:59 joze sudo:     joze : TTY=pts/0 ; PWD=/var/log ; USER=root ; COMMAND=/bin/grep -R sensors /var/log
/var/log/installer/syslog:Oct 29 16:38:15 in-target:   libsensors3 libservlet2.4-java libsexy2 libshout3 libslp1 libsmbclient
/var/log/installer/syslog:Oct 29 16:38:15 in-target:   libapache-mod-perl librsvg2-bin libsane-doc libsane-extras hpoj lm-sensors
/var/log/installer/syslog:Oct 29 16:38:15 in-target:   libsensors3 libservlet2.4-java libsexy2 libshout3 libslp1 libsmbclient
/var/log/installer/syslog:Oct 29 16:42:39 in-target: Selecting previously deselected package libsensors3.
/var/log/installer/syslog:Oct 29 16:42:39 in-target: Unpacking libsensors3 (from .../libsensors3_2.10.4-1ubuntu1_i386.deb) ...
/var/log/installer/syslog:Oct 29 16:46:17 in-target: Setting up libsensors3 (1:2.10.4-1ubuntu1) ...
```

---

### Post by Angafirith on 2007-11-20
I don't have lm-sensors installed, so I don't think that's the problem that I'm having. I don't get any message about sensors failing. Also, my problem only effects things in the gnome-session: if I start an application as soon as I get to the desktop (really quickly), it will open before nm-applet or anything else in the gnome-session. I found a workaround to the wireless problem, which is starting nm-applet manually. I end up with two nm-applets when the session finally gets up, but I can get online immediately.

I do want to properly solve it, though.

As for the problem that you're having, the logs you've provided seem to say that you installed lm-sensors on October 29, 2007 and again on Novmber 2, 2007. Was this around when you started having your difficulties? Have you tried completely removing lm-sensors and seeing if it worked?

---

