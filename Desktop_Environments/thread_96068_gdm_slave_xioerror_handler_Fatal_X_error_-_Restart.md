---
title: "gdm_slave_xioerror_handler: Fatal X error - Restarting :0"
date: 2005-11-28
forum: Desktop Environments
---

### Post by discord on 2005-11-28
Hi,

I've been having gnome restart when I've been using firefox. Looking around in diffierent logs i found..

Nov 27 23:40:56 localhost gconfd (discord-9510): Received signal 15, shutting down cleanly
Nov 27 23:40:56 localhost gconfd (discord-9510): Exiting
Nov 27 23:40:56 localhost gdm[9442]: gdm_slave_xioerror_handler: Fatal X error - Restarting :0

I am using the nvidia proprietary driver. I googled around and saw some other people were having a similar issue but with laptops and they had troubles with Xscreensaver. So far Xscreensaver seems to work fine for me. I am using an hp d325 desktop with integrated GF4MX video.

---

### Post by discord on 2005-12-02
Well since no one has responded should I file a bug report? 10 views on this thread... thats pathetic... :(

---

### Post by AAUU on 2006-01-13
I've had a very similar issue.  I've posted about it in another thread as I thought it was strictly a gconfd issue.
```

Jan 12 11:51:27 localhost gconfd (root-14468): Resolved address "xml:readonly:/usr/share/gconf/local.mandatory" to a read-only configuration source at position 1
Jan 12 11:51:27 localhost gconfd (root-14468): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 2
Jan 12 11:51:27 localhost gconfd (root-14468): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 3
Jan 12 11:51:27 localhost gconfd (root-14468): Resolved address "xml:readonly:/usr/share/gconf/local.defaults" to a read-only configuration source at position 4
Jan 12 11:51:27 localhost gconfd (root-14468): Resolved address "xml:readonly:/usr/share/gconf/cdd.defaults" to a read-only configuration source at position 5
Jan 12 11:51:27 localhost gconfd (root-14468): Resolved address "xml:readonly:/usr/share/gconf/debian.defaults" to a read-only configuration source at position 6
Jan 12 11:51:27 localhost gconfd (root-14468): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 7
Jan 12 11:51:27 localhost gconfd (root-14468): GConf server is not in use, shutting down.
Jan 12 11:51:27 localhost gconfd (root-14468): Exiting
Jan 12 11:52:26 localhost gconfd (user-8014): Received signal 15, shutting down cleanly
Jan 12 11:52:26 localhost gconfd (user-8014): Exiting
Jan 12 11:52:26 localhost gdm[7486]: gdm_slave_xioerror_handler: Fatal X error - Restarting :0
Jan 12 11:52:38 localhost gconfd (user-14786): starting (version 2.12.0), pid 14786 user 'user'
Jan 12 11:52:38 localhost gconfd (user-14786): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Jan 12 11:52:38 localhost gconfd (user-14786): Resolved address "xml:readonly:/usr/share/gconf/local.mandatory" to a read-only configuration source at position 1
Jan 12 11:52:38 localhost gconfd (user-14786): Resolved address "xml:readwrite:/home/user/.gconf" to a writable configuration source at position 2
Jan 12 11:52:38 localhost gconfd (user-14786): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 3
Jan 12 11:52:38 localhost gconfd (user-14786): Resolved address "xml:readonly:/usr/share/gconf/local.defaults" to a read-only configuration source at position 4
Jan 12 11:52:38 localhost gconfd (user-14786): Resolved address "xml:readonly:/usr/share/gconf/cdd.defaults" to a read-only configuration source at position 5
Jan 12 11:52:38 localhost gconfd (user-14786): Resolved address "xml:readonly:/usr/share/gconf/debian.defaults" to a read-only configuration source at position 6
Jan 12 11:52:38 localhost gconfd (user-14786): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 7
Jan 12 11:52:42 localhost gconfd (user-14786): Resolved address "xml:readwrite:/home/user/.gconf" to a writable configuration source at position 0
Jan 12 11:53:20 localhost gconfd (root-14901): starting (version 2.12.0), pid 14901 user 'root'
Jan 12 11:53:20 localhost gconfd (root-14901): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Jan 12 11:53:20 localhost gconfd (root-14901): Resolved address "xml:readonly:/usr/share/gconf/local.mandatory" to a read-only configuration source at position 1
Jan 12 11:53:20 localhost gconfd (root-14901): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 2
Jan 12 11:53:20 localhost gconfd (root-14901): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 3
Jan 12 11:53:20 localhost gconfd (root-14901): Resolved address "xml:readonly:/usr/share/gconf/local.defaults" to a read-only configuration source at position 4
Jan 12 11:53:20 localhost gconfd (root-14901): Resolved address "xml:readonly:/usr/share/gconf/cdd.defaults" to a read-only configuration source at position 5
Jan 12 11:53:20 localhost gconfd (root-14901): Resolved address "xml:readonly:/usr/share/gconf/debian.defaults" to a read-only configuration source at position 6
Jan 12 11:53:20 localhost gconfd (root-14901): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 7
Jan 12 11:53:50 localhost gconfd (root-14901): GConf server is not in use, shutting down.
Jan 12 11:53:50 localhost gconfd (root-14901): Exiting
```
I'm hoping someone will be able to explain to me what the gconfd error was all about.  It would appear that it's directly related to the gdm error for me.  Do you also have gconfd errors?

---

### Post by bridgkick on 2006-10-02
For what it's worth I'm getting the same thing: random Gnome restarts when using Firefox and/or Thunderbird (not sure if it's one or both causing this). 
Here's my Xorg.0.log output:
---
Oct  2 10:57:03 localhost gconfd (eric-4858): Received signal 15, shutting down cleanly
Oct  2 10:57:03 localhost gconfd (eric-4858): Exiting
Oct  2 10:57:05 localhost kernel: [17181507.408000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
Oct  2 10:57:05 localhost kernel: [17181507.408000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
Oct  2 10:57:05 localhost kernel: [17181507.408000] agpgart: Putting AGP V2 device at 0000:02:00.0 into 4x mode
Oct  2 10:57:12 localhost gconfd (eric-5932): starting (version 2.14.0), pid 5932 user 'eric'
---
Nothing weird before the signal 15.
I'm on a Shuttle SN41G2 with the nVidia GeForce 400 card.

---

### Post by hapee on 2006-10-26
Interesting, I have the same error using KDE and Firefox:

---

Oct 26 15:46:03 localhost gconfd (hapee-15671): Received signal 15, shutting down cleanly
Oct 26 15:46:03 localhost gconfd (hapee-15671): Exiting

---

I do not want to run gconfd but apperently it is. What is firefox doing in this story?

---

### Post by hairuo on 2007-06-05
me too! but just  Firefox under Gnome

> **hapee said:**
> Interesting, I have the same error using KDE and Firefox:

---

Oct 26 15:46:03 localhost gconfd (hapee-15671): Received signal 15, shutting down cleanly
Oct 26 15:46:03 localhost gconfd (hapee-15671): Exiting

---

I do not want to run gconfd but apperently it is. What is firefox doing in this story?

---

### Post by midnightToker on 2007-06-16
I've been getting the same thing.  I installed Feisty Dawn 64bit running on an Acer laptop with a Radeon Xpress 200M.  I'm running Gnome with Compiz, I haven't changed anything other than the background, theme, etc.  Here's the error:

Jun 16 14:02:12 mcbuntu gconfd (mcd-5400): Received signal 15, shutting down cleanly
Jun 16 14:02:12 mcbuntu gconfd (mcd-5400): Exiting
Jun 16 14:02:12 mcbuntu gdm[4936]: gdm_slave_xioerror_handler: Fatal X error - Restarting :0
Jun 16 14:02:15 mcbuntu kernel: [ 1583.640345] [fglrx] PCIe has already been initialized. Reinitializing ...
Jun 16 14:02:33 mcbuntu gconfd (mcd-7575): starting (version 2.18.0.1), pid 7575 user 'mcd'


I was using Firefox, then I used Galeon for a while, now I'm using Epiphany.  It usually happens when I'm using a browser, but it has also happened when no browser is open, so I don't think it's related to the browser.  Sometimes it will happen 3 times in 10 minutes, sometimes I can use the computer for hours or even days without any problem.

---

### Post by gavilanes on 2007-06-18
I am having the same problem...
Jun 18 14:04:26 mcgyverlin gconfd (gavilanes-5411): Received signal 15, shutting down cleanly
Jun 18 14:04:28 mcgyverlin gconfd (gavilanes-5411): Exiting
Jun 18 14:04:28 mcgyverlin gdm[4714]: gdm_slave_xioerror_handler: Fatal X error - Restarting :0

Well I guess this X crash started to happen since I installed last update (kernel includes) But I really don't remember which things it installed, any ideas of a way to know exactly?

Thank you all!
Gavilanes

---

### Post by gavilanes on 2007-06-18
By the way, it almost allways happens when using firefox, clicking something, closing a tab, or clicking on "Back" button; But it is not the only case, it also happened when using a virtual my machine, Which I have been using for a week without problems.

Also I am running Feisty on an AMD 64 Turion on an Acer Laptop, which initially experimented hangs until the first kernel update arrived. from that time on, worked just ok until 3 days ago...
well. thats all for the moment.

---

### Post by Tobblo on 2007-06-24
I'm having problem with this too. Runnings 64-bit Feisty Fawn, latest kernel update and with nvidia drivers. It seems to occur sometimes when xscreensaver is supposed to start, but instead this "fatal x error" is happening. Otherwise it never happens to me.

---

### Post by modafokaxx on 2007-06-27
> Sometimes it will happen 3 times in 10 minutes, sometimes I can use the computer for hours or even days without any problem.

same thing here... highly highly annoying.
I use Opera, and it happens with or withour the browser open.

It tends to happen when I put the box under heavy load.. but sometimes just happens out of the blue.

I'm the first to admit I probably don't have the cleanest Ubuntu install out there, having updated from Dapper along the way and adding and removing bits, modifying some files here and there, but overall things work.

I'm using Ubuntu "Feisty Fawn" 7.04 on a 1.33ghz AMD athlon with 384 mb of RAM and a GeForce2MX, using proprietary drivers.

I'm must admit I'm not all that impressed with Feisty so far, Edgy seemed more stable to me (maybe only because of this issue).

I hope a solution to this will be seen, otherwise I might feel like reinstalling (uhh sounds like a pain) and might try another distro then (Debian of Gentoo, just to see a bit of countryside)

---

### Post by AntonGardner on 2007-08-27
Same error to me. Using Gnome and Kile (Latex editor for KDE). Once X restarted when I tried to unmount the cdrom... strange...

---

### Post by SiMoNsAyS on 2007-09-02
same here, first it was on feisty, then format + gutsy tribe5 without luck.

can any1 help please?! :(

---

### Post by ambar.amarelo on 2007-09-16
I get the same error:


Whe i try to run a opengl/c++ simple program, the xserver crash !
or when i use firefox for 64bits.

the log message is:

cat /var/log/syslog
Sep 16 22:45:52 brazil gconfd (myloginr-5125): Received signal 15, shutting down cleanly
Sep 16 22:45:52 brazil gconfd (mylogin-5125): Exiting
Sep 16 22:45:52 brazil gdm[4712]: gdm_slave_xioerror_handler: Fatal X error - Restarting :0




My system is: amd64 with xubuntu for 64bits

cat /proc/cpuinfo
AMD Sempron(tm) Processor 2800+

cat /proc/version
Linux version 2.6.20-15-generic (root@yellow) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 06:17:24 UTC 2007



i dont know what this is... :confused:

this is a 64bits ubuntu bug ?

---

### Post by AntonGardner on 2007-09-18
I don't guess it's only a 64bit issue... I use Ubuntu 32bit...

My processor is a Pentium4.

---

### Post by Jouke74 on 2007-10-08
Actually it is a Gnome - Firefox issue that makes the X-server crash (and that is nasty). Also people post the X-server exiting point of their error log, however that is the consequence, not the cause. 

Something goes wrong with writing to gconfd, the question is why firefox wants to write to Gconfd?? That is a root job and not a user job. Maybe some firefox add-on which want to do more than it should (guessing here).

---

### Post by kef1 on 2007-10-11
Hello. Yes, I am having the same problem as many of you. However, I don't think Firefox has to do with it since this happened to me a few times while Firefox was closed.

Here's the log:

Oct 11 22:49:30 oblivion gdm[5002]: gdm_slave_xioerror_handler: Fatal X error - Restarting :0
Oct 11 22:49:33 oblivion gdm[6382]: gdm_slave_xioerror_handler: Fatal X error - Restarting :0
Oct 11 22:49:38 oblivion gdm[6392]: gdm_slave_xioerror_handler: Fatal X error - Restarting :0
Oct 11 22:49:43 oblivion gdm[6402]: gdm_slave_xioerror_handler: Fatal X error - Restarting :0
Oct 11 22:49:43 oblivion gdm[5001]: deal_with_x_crashes: Running the XKeepsCrashing scripts.
Oct 11 23:32:54 oblivion init: tty4 main process (4405) killed by TERM signal
Oct 11 23:32:54 oblivion init: tty5 main process (4406) killed by TERM signal
Oct 11 23:32:54 oblivion init: tty2 main process (4411) killed by TERM signal
Oct 11 23:32:54 oblivion init: tty3 main process (4412) killed by TERM signal
Oct 11 23:32:54 oblivion init: tty1 main process (4413) killed by TERM signal
Oct 11 23:32:54 oblivion init: tty6 main process (4414) killed by TERM signal
Oct 11 23:32:55 oblivion gdm[5001]: Failed to start X server several times in a short time period; disabling display :0
Oct 11 23:32:57 oblivion rpc.statd[5146]: Caught signal 15, un-registering and exiting.

This happens to me when switching from a full-screen game to normal and vice versa (Quake 2, Unreal Tournament and even XGalaga but not with Totem nor Mplayer).

If you require more information about the problem and/or my machine let me know.

---

### Post by attunezero on 2007-10-30
The same is happening to me. Same log output. Random crashes, sometimes days apart, sometimes seconds apart... Happened on an old install and a fresh install. Don't think it has anything to do with firefox as it has crashed many times while nothing at all is running, although firefox does crash alot even on the live cd. There seem to be a lot of posts and bugs about this error but nobody seems to know anything about it =(

---

### Post by aztektum on 2007-11-01
It happens to me but only if I leave the system sitting idle for a little bit.

If I walk away for more than say, 20 mins, I come back to the login screen. I haven't had it happen while I'm workin' at the computer (it's happening on an IBM X41 non-tablet and Dell D520)

Most recent session I had Evolution, Firefox with some tabs, Pidgin, a Gnome Terminal session open and after a few mins Xscreensaver runs. No desktop fx *coughwasteofsystemresourcescough*

---

### Post by thecrius on 2007-11-15
Same problem here.
As many others i've notice that the restart happen even if firefox isn't open.
But for the most this event occur when you try to interact with some flash contents.

My distro is 32bit. Do not attach log cause is the same of all the others.

Anyone have reported this till now? (don't know where to post the bug report....)

---

### Post by tipsqueal on 2007-11-24
I've been having the same gdm_slave_xioerror_handler problem for about a week or so now. It only occurs when my computer goes idle and goes to the screensaver. The only thing I ever keep running when this happens is Pidgin. No Firefox, no Evolution (though I do use them), nothing but Pidgin running in the background. I'm going to try disabling the screen saver I'm using. Any other help would be nice.

Thanks,
Tipsqueal.

---

### Post by ubuntu-freak on 2007-11-29
I'm having the same error in Debian, so it's not a Ubuntu issue. I suspect it's xorg as it's only happening since I changed to the exa driver instead of xaa. It happens when I view divx.com movies with the mplayer plugin in firefox. Doesn't happen to me with any other streaming site or the xscreensaver. Perhaps it's an xorg/exa/mplayer/compiz fusion issue :)

Try this command in the terminal: dpkg-reconfigure xserver-xorg

It will automatically setup your xorg.conf and often fixes problems. It's made my system faster and more stable.

---

### Post by tayhe on 2007-12-02
this problem is posted as a bug: Bug #140554 on 2007-09-17, but isn't confirmed indeed till today&#12290;

the same problem random affect my computer ,which fresh installed gutsy&#65292;for a long time.
it is as noticed above, not reproducible reliably. and it is mostly relate the open and close of firefox, the switch between workspaces.

on my computer:
nvidia6200 with nvidia-glx-new
even though compiz-fusion is closed

---

### Post by jesushero on 2007-12-14
I've been having similar problems and found a few different variations of this problem. Everyone else seems to be getting a signal 15, while I'm not!

Have a look here [http://ubuntuforums.org/showthread.php?t=640105]("http://ubuntuforums.org/showthread.php?t=640105")

I've noticed that ALMOST EVERYONE has this problem when using video stuff such as flash or other web-related apps, or games. Also, ALMOST EVERYONE, including myself, is using nvidia graphics cards. 

Could it have to do with nvidia?? I have not installed the restricted nvidia driver, I've been using the default one as installed on the Gutsy install. I've checked everything I could think of such as filesystems, harddrives, ram.... Nothing wrong there! 

Also, it seems to be a problem in many different versions of ubuntu and other distributions, i think I saw it on the redhat forums.

---

### Post by Visitor.Q on 2008-01-03
I also have this problem on my desktop system (AMD XP 2100+/1GB/NVidiaTi4600). I have the restricted NVidia driver enabled (96.43.01), using Ubuntu Gutsy Gibbon 7.10, and regularly using Firefox/Pidgin/Gnome terminal. And Compiz fusion is running. Everything smoothly, so there seems to be no reason for an X server crash.. This has happened a few times now in 3 days.

Oh, and I cannot find a gconfd error message in the logs... Should I turn logging on for gconfd somewhere or would it log strange behavior automatically?


Syslog:
Jan  3 10:48:18 my-desktop gdm[5398]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0

---

### Post by Visitor.Q on 2008-01-04
In the last hour I have had this problem twice, both times I was working on a remote machine via ssh (using nautilus to browse my remote files). A large .LOG file (text) was opened with Gedit and then (because the file is quite large) a progress bar of the file loading is shown. About half-way this progress bar, the x server crashed. A few moments later, the x server crashed again also while loading a remote file into gedit. Although I can open some large files with gedit via SSH (it doesnt happens always), this looks a bit suspicious to me... Copying files via nautilus has not shown these problems (yet).

Is there already a bug report filed? How do I reach it? It would be better if we could see some more log activities to pinpoint the problem, so if someone has a tip on how to set this I'm curious :)

---

### Post by odor on 2008-01-14
It is not a nvidia issue. I am using intel 915 opensource drive. Similair problems. I get X crashes whenever I try to type in Gvim od Gedit. I can quit reliably confirm that. I can run my machine for days, an the moment i turn on gvim and open a document to start typing X crashes, in a matter of seconds. Weird.

---

### Post by odor on 2008-01-14
Thought I cannot confirm it beyond doubt, I think i have solved the issue in my particular case. I reverted my video driver to standard VESA.  I ran ```
sudo dpkg-reconfigure xserver-xorg
``` and chose VESA driver. 4 hours have passed and no X crashes yet (i usually got one in the first 10 minutes of my gvim session)

---

### Post by birddawg on 2008-01-19
> **odor said:**
> Thought I cannot confirm it beyond doubt, I think i have solved the issue in my particular case. I reverted my video driver to standard VESA.  I ran ```
sudo dpkg-reconfigure xserver-xorg
``` and chose VESA driver. 4 hours have passed and no X crashes yet (i usually got one in the first 10 minutes of my gvim session)


I tried this, reverted to the VESA driver and I still experienced the same problems.

Thanks,

---

### Post by Maxymillion on 2008-01-21
This is the error im constantly getting trying to install drivers for my agp 6600GT video card. Clean install 32bit or 64bit of Gutsy, enable driver in restricted driver manager, reboot, 

WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0
CRITICAL: gdm_config_value_get_bool: assertion value->type == GDM_CONFIG_VALUE_BOOL ' failed

3 times as X tries to load and it reverts to safe graphics mode

---

### Post by gobion on 2008-02-02
I had the similar problem and I managed to work out what was causing it. I have Gutsy with an ATI graphics card (X1400) on an Acer Laptop (fresh install from a week ago)

The install was all fine until I installed Emerald on top of Compiz.

Gnome worked fine until I tried to resize a window then it ground to a halt. I had a think about what packages I had recently installed and Emerald was the only one that co-incided with the slowdown (gdm_slave_xioerror_handler: Fatal X error - Restarting :0), and when I uninstalled Emerald everything went back to normal.

I got the impression that Emerald was getting stuck in a processing loop trying to figure out the rendering, but that is just a hunch.

Anyway if you have Gutsy, a reasonable graphics card, are running Compiz and Emerald and your machine start slowing down majorly, try uninstalling Emerald.

Also - if it helps I found that the X slowdown went away when all the apps were minimized.

HTH

(Oh and I just wanted to say, that the Ubuntu community seems very helpful - this thread and others really helped me isolate and fix the problem which in turn made me want to share any insights I had, so thanks!)

Gobion

---

### Post by sstalpers on 2008-02-02
I had the same problem. It turns out my NVIDIA-Linux-x86-169.07 proprietry driver was causing it. They have posted a new driver [here]("http://www.nvidia.com/object/linux_display_ia32_169.09.html") which **"Fixed a bug that caused the X driver to crash if the X.Org GLX extension module was loaded instead of NVIDIA&#8217;s**". I installed the new driver and I get no more errors! 

You have to stop the Gnome Display Manager before installing the driver:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo /etc/init.d/gdm stop

#press <ctrl><alt>F2

sudo sh NVIDIA-Linux-x86-169.09-pkg1.run
sudo /etc/init.d/gdm start
```

(For some reason I had to install it twice - first time I got an error that /usr/lib/xorg/modules/extensions/libglx.so is not a symbolic link, but the second time it worked fine)

I have a GeForce 6200 card, and got the gdm_slave_xioerror_handler error when using advanced desktop effects (e.g. desktop cube) and also when running some games  (e.g. Chromium). I was not running Emerald.

I hope this helps all of you with proprietry NVidia drivers! And thanks to all of you that posted in this thread!

UPDATE: this nvidia driver did not solve the problem; see my post below made on the 10th of March.

---

### Post by Ethric on 2008-02-04
Hi,

I had the same problems since I updated yesterday (new packages among others: xserver-xorg-core (2:1.2.0-3ubuntu8) to 2:1.2.0-3ubuntu8.3, xserver-xorg-dev (2:1.2.0-3ubuntu8) to 2:1.2.0-3ubuntu8.3).

After that, the xserver crashed repeatably when I wanted to start the EVE Online client. Firefox worked well.

I could solve the problem with simply reinstalling my old download of the nvidia driver (version 100.14.11). I did in fact get the same warning as sstalpers (libglx.so is not a symbolic link), but it works anyhow.

Thanks to everyone in this thread for pointing at the driver issue.

-Ethric

---

### Post by MeduZa on 2008-02-10
> **tipsqueal said:**
> I've been having the same gdm_slave_xioerror_handler problem for about a week or so now. It only occurs when my computer goes idle and goes to the screensaver. The only thing I ever keep running when this happens is Pidgin. No Firefox, no Evolution (though I do use them), nothing but Pidgin running in the background. I'm going to try disabling the screen saver I'm using. Any other help would be nice.

Thanks,
Tipsqueal.

mmm, Same problem here, for about a weeks when I open a new X to play a game (X :3 ) , the X :0 restarst when go idle normally, and I got:
Feb 10 19:13:30 Xenoid gdm[4576]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 
I have FF, Seamonkey, Pidgin and Rhythmbox normaly opened.
If I'm playing a game on X: 3 and the X :0 have compiz on, HAPPEND
If I'm working (X :0 ) and I leave the computer for a while, normally happend (not always)

My Ubuntus is 7.10 with Linux 2.6.23.1 #2 SMP PREEMPT Fri Dec 21 13:27:28 EST 2007 i686 GNU/Linux kernel running on a AMD 64 x2 4600+ 1gb of ram and a NVIDIA 7900gs

Appear to be an emerald problem!! never happend with metacity

Salutes!!!

---

### Post by sstalpers on 2008-03-10
I was a bit too premature in my previous post: the new Nvidia driver does not solve the problem. 

I got the same problems two times again, each time after running an update (Gutsy, Feb. 10th and 27th; the last update included the libqt4-core, libqt4-gui and xserver-xorg-video-intel packages). I fixed the problem each time by following Etheric's suggestion to reinstall my existing download of the nvidia driver (ver x86-169.09). The last update (Mar. 10th) did not give any problems. 

Does anyone know what might be causing the problem? Could updates of x-windows-related components be resetting something that is fixed by re-installing the nvidia driver?

---

### Post by militanz on 2008-05-04
Same problem here,
i have a Dell Latitude ATG D630, with an "Intel Corporation Mobile GM965/GL960". The issue started after upgraded to hardy, last week. With gutsy everything was fine. It happen when i play with "Urban Terror" (3D game). If i play only 10-15 minutes, an then I restart X, i'm able to play again for another 10-15 minutes, and then restart, and so on... but if i try to play for more than 10-15 minutes all at once, my display crashes and no way to get out (well, only the acpi way :-| ).
Here is my syslog:

> May  3 14:07:17 militanz-laptop gdm[5767]: WARNING: gdm_slave_xioerror_handler: errore fatale di X. Riavvio di :0 in corso 


So i exclude an Nvidia issue, and/or a gnome-with-firefox issue.

Cross your fingers...

---

### Post by HoudiniWater on 2008-05-09
Same stooped problem!!!
I lost a lot of data!
Ubuntu 64 bit 8.04 all uptodate
GeForce 8800 gt
intel q6600

So what is the problem?

---

### Post by ubuntu-freak on 2008-05-10
Seems to be Xorg and some graphics drivers not playing nice together, both open and proprietary drivers. Major crashes are nearly always graphics driver related. The Xorg in Hardy is a pre-release apparently.
 
Here's a couple of recent bug reports:
 
[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/152648](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/152648)
 
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/220019](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/220019)
 
Nathan

---

### Post by uzi09 on 2008-06-09
I'm just curious, but does everyone who is having this problem running (k/x)ubuntu 8.04 hardy heron?

I am thinking about maybe switching to a previous release or something, but if the problem is occuring there too, I guess it wouldn't be worth all the effort.

Thanks

---

### Post by Visitor.Q on 2008-06-16
> **uzi09 said:**
> I'm just curious, but does everyone who is having this problem running (k/x)ubuntu 8.04 hardy heron?

I am thinking about maybe switching to a previous release or something, but if the problem is occuring there too, I guess it wouldn't be worth all the effort.

Thanks

No, I've had this in previous editions as well. Actually, I am pretty happy with 8.04 as it seems to crash less often than previous versions. Having said that, I'm sure it'll crash tonight :)

---

### Post by Robsteranium on 2008-07-06
Same error in syslog.

Xubuntu 8.10
VGA compatible controller: Silicon Integrated Systems [SiS] 65x/M650/740 PCI/AGP VGA Display Adapter

Afaik, that means this isn't an NVIDIA problem.  Perhaps it's not hardware specific.

I have also just changed my desktop themes.  I think this has something to do with compositing.

There again I've never really settled on an xorg config anyway - could be any number of settings I've tinkered with in there.

---

### Post by khughitt on 2008-07-07
I've started running into the same problem after updating my Kernel this morning. I'm running Ubuntu 8.04 with NVIDIA proprietary drivers.

More Info:

[INDENT]Nvidia Drivers: Linux-x86 173.14.05
X.org:          1.4.0.90 (10400090)
Kernel:         2.6.24-19-generic
$compiz --version
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:01d1 (rev a1) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (3520x1200) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
compiz 0.7.4[/INDENT]

---

### Post by khughitt on 2008-07-08
Tried reinstalling NVIDIA drivers but still no luck. Everything runs very slowly under compiz now so I've switched to using metacity for the time being.

---

### Post by Ac1D on 2008-07-12
I have exactly the same problem.

Tried almost everything, compiz on/off, new and old nvidia drivers, setting my effects to none.

Nothing seems to help, my system will crash randomly mostly it takes about 4hours.

I'm running Hardy.

/edit
Hmm was looking further and I found something weird in the user.log at the exact same time my x server crashes.

Jul 12 13:11:48 rob-desktop pulseaudio[7411]: pid.c: Stale PID file, overwriting.
Jul 12 19:23:18 rob-desktop pulseaudio[21961]: pid.c: Stale PID file, overwriting.

---

### Post by xfodder on 2008-07-12
> **Ac1D said:**
> I have exactly the same problem.

Tried almost everything, compiz on/off, new and old nvidia drivers, setting my effects to none.

Nothing seems to help, my system will crash randomly mostly it takes about 4hours.

I'm running Hardy.

/edit
Hmm was looking further and I found something weird in the user.log at the exact same time my x server crashes.

Jul 12 13:11:48 rob-desktop pulseaudio[7411]: pid.c: Stale PID file, overwriting.
Jul 12 19:23:18 rob-desktop pulseaudio[21961]: pid.c: Stale PID file, overwriting.

This is exactly the same for me ... not only do i have the error about gdm_slave i also get the pulseaudio errors as above and i also get 3 agpgart errors ... here are my errors

```
Jul 13 05:39:28 jesse-ubuntu gdm[14073]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 
Jul 13 05:39:31 jesse-ubuntu kernel: [16886.022396] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
Jul 13 05:39:31 jesse-ubuntu kernel: [16886.022411] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
Jul 13 05:39:31 jesse-ubuntu kernel: [16886.022433] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
Jul 13 05:39:45 jesse-ubuntu pulseaudio[22632]: pid.c: Stale PID file, overwriting.
Jul 13 05:39:45 jesse-ubuntu pulseaudio[22632]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
Jul 13 05:39:45 jesse-ubuntu pulseaudio[22632]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
```

---

### Post by Execute_Method on 2008-07-12
I'm getting the same thing recently. Mine has restarted GDM 3 times over 2 days..... I'm not sure what's going on but I don't like it. :(

I have made changes to pulseaudio,jack,firefox, and flash right before. *As well as all updates to hardy*.

I'm running:
xserver 2:1.4.99 from git
OpenGL version string: 1.3 Mesa 7.1 rc1
xserver-video-ati 1:6.8.0 from git

compiz 1:0.76

ubuntu studio 8.04

pulseaudio 0.9.10
firefox 3
flash10 beta

Until 3 days ago this was working flawlessly (about 1 1/2mo.)


If anyone can help it would be greatly appreciated.

```
Jul 12 10:20:22 ubuntu kernel: [42600.175643] [drm] Num pipes: 1
Jul 12 10:20:22 ubuntu gdm[5880]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 
Jul 12 10:20:24 ubuntu kernel: [42602.238846] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
Jul 12 10:20:24 ubuntu kernel: [42602.239235] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
Jul 12 10:20:24 ubuntu kernel: [42602.239439] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
Jul 12 10:20:24 ubuntu kernel: [42602.254443] [drm] Setting GART location based on new memory map
Jul 12 10:20:24 ubuntu kernel: [42602.254663] [drm] Loading R500 Microcode
Jul 12 10:20:24 ubuntu kernel: [42602.254835] [drm] Num pipes: 1
Jul 12 10:20:24 ubuntu kernel: [42602.254940] [drm] writeback test succeeded in 1 usecs
```

```
Jul 12 19:56:53 ubuntu gdm[5888]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 
Jul 12 19:56:55 ubuntu kernel: [17902.570171] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
Jul 12 19:56:55 ubuntu kernel: [17902.570418] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
Jul 12 19:56:55 ubuntu kernel: [17902.570609] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
Jul 12 19:56:55 ubuntu kernel: [17902.585549] [drm] Setting GART location based on new memory map
Jul 12 19:56:55 ubuntu kernel: [17902.585794] [drm] Loading R500 Microcode
Jul 12 19:56:55 ubuntu kernel: [17902.585964] [drm] Num pipes: 1
Jul 12 19:56:55 ubuntu kernel: [17902.586068] [drm] writeback test succeeded in 1 usecs
Jul 12 19:57:08 ubuntu pulseaudio[10510]: pid.c: Stale PID file, overwriting.
Jul 12 19:57:09 ubuntu pulseaudio[10510]: socket-server.c: socket(PF_INET6): Address family not supported by protocol
Jul 12 19:57:09 ubuntu pulseaudio[10510]: socket-server.c: socket(PF_INET6): Address family not supported by protocol
```

---

### Post by Execute_Method on 2008-07-13
bump it up.

---

### Post by khughitt on 2008-07-14
Turning off Avant-Window-Navigator seems to have returned stability to my machine for the time being. I don't imagine that is the only reason people are having this problem though. More likely a compiz/driver-related issue.

---

### Post by Ac1D on 2008-07-14
> **pwnedd said:**
> Turning off Avant-Window-Navigator seems to have returned stability to my machine for the time being. I don't imagine that is the only reason people are having this problem though. More likely a compiz/driver-related issue.

I don't use Compiz or AWN at this time, just to check if they caused the problems. I also tried different nvidia drivers.
None of it seems to solve the problems.

It's really an annoying problem.

---

### Post by Ac1D on 2008-07-16
just a bump.

Can anyone give me some ideas what about to try next or which information I should gather?

---

### Post by parabolee on 2008-07-22
I am also having this issue. I though that I had messed something up since I had installed and uninstalled a lot of things. So I did a fresh install of Ubuntu 8.04 a few days ago. Everything was working great and I just had my first crash 15 mins ago. Seems to crash when I am file browsing, I have Firefox open at all times but I don't think that is the cause.

I have a Dell Inspiron 6400 laptop with ATI Radeon Mobility 1400.

Here is my crash log up to 10 mins before the restart -

Jul 22 10:49:04 lee-laptop-ub-linux avahi-daemon[5202]: Invalid legacy unicast query packet.
Jul 22 10:49:04 lee-laptop-ub-linux avahi-daemon[5202]: Received response with invalid source port 41127 on interface 'eth0.0'
Jul 22 10:49:04 lee-laptop-ub-linux avahi-daemon[5202]: Invalid legacy unicast query packet.
Jul 22 10:49:04 lee-laptop-ub-linux avahi-daemon[5202]: Invalid legacy unicast query packet.
Jul 22 10:49:05 lee-laptop-ub-linux avahi-daemon[5202]: Received response with invalid source port 41127 on interface 'eth0.0'
Jul 22 10:49:35 lee-laptop-ub-linux last message repeated 6 times
Jul 22 10:50:07 lee-laptop-ub-linux avahi-daemon[5202]: Received response with invalid source port 41127 on interface 'eth0.0'
**Jul 22 10:58:07 lee-laptop-ub-linux gdm[5715]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 **
Jul 22 10:58:11 lee-laptop-ub-linux kernel: [ 7057.412875] [fglrx] PCIe has already been initialized. Reinitializing ...

---

