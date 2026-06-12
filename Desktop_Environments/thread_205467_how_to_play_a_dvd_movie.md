---
title: "how to play a dvd movie"
date: 2006-06-28
forum: Desktop Environments
---

### Post by jordilin on 2006-06-28
When I insert a DVD movie and try to play it through mplayer I get a pop up window that says **failed to open dvd://1**  I've followed the instructions given in [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats) and no help (I've installed libdvdcss2 and totem-xine)
[IMG]http://personal.telefonica.terra.es/web/personalinfo/failedtoopen.png[/IMG]
Any help? thanks

---

### Post by Al3xanR0 on 2006-06-28
[QUOTE=jordilin]When I insert a DVD movie and try to play it through mplayer I get a pop up window that says **failed to open dvd://1**  I've followed the instructions given in [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats) and no help (I've installed libdvdcss2 and totem-xine)
[IMG]http://personal.telefonica.terra.es/web/personalinfo/failedtoopen.png[/IMG]
Any help? thanks[/QUOTE]

you will also need  

libdvdread
libdvdplay
libdvdnav (for navigation)
win32codecs (optional)

---

### Post by jordilin on 2006-06-28
[QUOTE=Al3xanR0]you will also need  

libdvdread
libdvdplay
libdvdnav (for navigation)
win32codecs (optional)[/QUOTE]

I have them installed and I continue with the same problem: Failed to open dvd://1. It seems as if the place where mplayer goes to find the dvd is wrong dvd://1

---

### Post by evil_elman on 2006-06-28
Similar problem for me... Whenever trying to play a DVD Totem says there are plugins missing... Have got the libraries as mentioned by jordilin.

I can select individual .ts or .vob files and get a still picture but it won't play and gives the error message again...

Any ideas?

---

### Post by jordilin on 2006-06-28
Nobody else has experienced the same problem? I think this is a major issue. If you are not able to play dvd movies with your OS, what a nasty problem.

---

### Post by giacomolg on 2006-06-29
I get the same error (can play vob but not reproduce the DVD), as evil_elman is experiencing.
I've noticed there's a gstreamer-dvd package for verion 0.8 of gstreamer. Do we need something similar for v. 1?
With Mplayer the dvd playback works (no menus...)

---

### Post by jordilin on 2006-06-29
The problem is where is mplayer looking for the dvd once it is inserted. If I get the message **Failed to open dvd://1**, then it means that the location dvd://1 doesn't exist. Should be sth like /mnt/cdrom? Where can I change this setting?

---

### Post by ardchoille on 2006-06-29
[QUOTE=jordilin]The problem is where is mplayer looking for the dvd once it is inserted. If I get the message **Failed to open dvd://1**, then it means that the location dvd://1 doesn't exist. Should be sth like /mnt/cdrom? Where can I change this setting?[/QUOTE]
I've had the same problem in MPlayer and Xine. And, believe it or not, a reboot fixes it. That might help you track down the problem.

---

### Post by giacomolg on 2006-06-29
[QUOTE=giacomolg]I get the same error (can play vob but not reproduce the DVD), as evil_elman is experiencing.
I've noticed there's a gstreamer-dvd package for verion 0.8 of gstreamer. Do we need something similar for v. 1?
With Mplayer the dvd playback works (no menus...)[/QUOTE]
Emmm, my issue was solved by swapping tote-gstreamer with totem-xine. You can *probably* use gstreamer to play encrypted dvds with menus, but is a bit more complex

---

### Post by jordilin on 2006-06-29
Well, I've had a look at /var/log/messages and that's what I get when I insert a dvd movie:

Jun 29 16:32:54 lamacchina kernel: [4296999.072000] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
Jun 29 16:32:54 lamacchina kernel: [4296999.072000] hdc: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
Jun 29 16:32:54 lamacchina kernel: [4296999.072000] ide: failed opcode was: unknown
Jun 29 16:32:54 lamacchina kernel: [4296999.072000] end_request: I/O error, dev hdc, sector 1380264
Jun 29 16:32:54 lamacchina kernel: [4296999.072000] printk: 26 messages suppressed.
Jun 29 16:32:54 lamacchina kernel: [4296999.086000] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
Jun 29 16:32:54 lamacchina kernel: [4296999.086000] hdc: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
Jun 29 16:32:54 lamacchina kernel: [4296999.086000] ide: failed opcode was: unknown
Jun 29 16:32:54 lamacchina kernel: [4296999.086000] end_request: I/O error, dev hdc, sector 1380268
Jun 29 16:32:54 lamacchina kernel: [4296999.153000] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
Jun 29 16:32:54 lamacchina kernel: [4296999.154000] hdc: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
Jun 29 16:32:54 lamacchina kernel: [4296999.154000] ide: failed opcode was: unknown
Jun 29 16:32:54 lamacchina kernel: [4296999.154000] end_request: I/O error, dev hdc, sector 1380272
Jun 29 16:32:54 lamacchina kernel: [4296999.220000] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
Jun 29 16:32:54 lamacchina kernel: [4296999.220000] hdc: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
Jun 29 16:32:54 lamacchina kernel: [4296999.220000] ide: failed opcode was: unknown
Jun 29 16:32:54 lamacchina kernel: [4296999.220000] end_request: I/O error, dev hdc, sector 1380276

---

### Post by jordilin on 2006-07-01
I'm unable to figure out what's going on in this issue. Either I will have to file a bug or simply switch to M$ windows in order to see dvd videos. 
It's curious, so many people in this forum, and nobody else is experiencing this issue???

---

### Post by Lord Illidan on 2006-07-01
Try installing xine and VLC to play movies, their setup seems much easier.

From there, use their options screen to change the DVD path to /dev/hdc or wherever your DVD drive is.

---

### Post by fvs on 2006-07-01
I have xine and have the same problems, It opens and if I select play DVD, 
"You don't have enough rights for this, or source don't contain data (e.g: not disc in drive)" The disc I have plays very well on same machine with Fedora. Any idea's.
Thanks.:confused:  fvs

---

### Post by jordilin on 2006-07-02
Yes, in Fedora I haven't any problem to play dvd videos...

---

### Post by Denis on 2006-07-15
Have you tried to change the location where mplayer looks for the DVD. 
It's in Preferences > Misc, below there is the "DVD device". try changing this to /dev/cdrom (which should be the location of your CD drive). 

Is the DVD mounted when it is inserted (does it show up on your desktop)?

If Mplayer doesn't do it, try some other players like Gxine, VLC, or Totem.

---

### Post by Lord Illidan on 2006-07-15
I don't know if mplayer is really worth it... Xine and Vlc beat it hands down in functionality.

---

### Post by jordilin on 2006-07-15
> **Denis said:**
> Have you tried to change the location where mplayer looks for the DVD. 
It's in Preferences > Misc, below there is the "DVD device". try changing this to /dev/cdrom (which should be the location of your CD drive). 

Is the DVD mounted when it is inserted (does it show up on your desktop)?

If Mplayer doesn't do it, try some other players like Gxine, VLC, or Totem.

Yes, I've tried to change it to /dev/cdrom and I still get the same pop up window Failed to open dvd://1. I've tried other players like VLC or Gxine with no success. I think I'll leave it as impossible, and I'll have to switch to win in order to play commercial dvd movies :(. Incredible, but true.

---

### Post by Lord Illidan on 2006-07-15
Where is the location of your dvd drive? Normally it is /dev/hd , followed by a letter.. like /dev/hda /dev/hdb, etc.

Mind if you post your /etc/fstab so we can find it for you?

---

### Post by jordilin on 2006-07-15
> **Lord Illidan said:**
> Where is the location of your dvd drive? Normally it is /dev/hd , followed by a letter.. like /dev/hda /dev/hdb, etc.

Mind if you post your /etc/fstab so we can find it for you?
This is my fstab:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /boot           ext3    defaults        0       2
/dev/hda3       /home           ext3    defaults        0       2
/dev/hda4       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by Teo on 2006-08-03
> **evil_elman said:**
> Similar problem for me... Whenever trying to play a DVD Totem says there are plugins missing... Have got the libraries as mentioned by jordilin.

I can select individual .ts or .vob files and get a still picture but it won't play and gives the error message again...

Same here. Totem says no plugins, MPlayer hangs when playing DVDs.

Got all libs mentioned earlier in this topic and MPlayer is setup correctly. Also tried to setup MPlayer for searching DVD in /dev/cdrom, /media/cdrom0, /dev/hdc, etc... no success (/dev/hdc and /media/cdrom0 - got this in /etc/fstab for mine DVD player).

---

### Post by aceracer24 on 2006-08-04
I am having the same problem as of today and I THINK I know what the problem is although not tested yet. I did a search for Mplayer on my drives to see if I could force the config to go to the drive my DVD player is and came across teh mplayer .deb file. So I cliked it to reinstall and the package installer complains that mozilla-mplayer plugin conflics with normal Mplayer. I will attempt to un install the plugin later and see if that is infact the problem or not. If someone else does this before me please update here.

---

### Post by Tamihania on 2006-08-06
:cry:I am really deeply sorry but yesterday I made dist-upgrade and now I am in exactly the same situation as the creator of the thread... I cannot play any DVD. I even reinstalled the system...installed codecs through Automatix...No help!
My fstab is as follows:
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       /home           ext3    defaults        0       2
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
 
...can anybody help? I will be very grateful...

tami

PS. The rest of the system works perfectly...I can play movie from the net and the files I've got from my work (short instructional videoclips in .wmv format...) I really have no idea what has happened - I am too much of the newbie...:oops:

---

### Post by jjworthy on 2006-08-09
Greeting all,

I've had the same problem as most in this thread... my only difference from the other posters is that I'm using Gentoo, but the same problem none the less. I thought I would share my solution and see if it helps the rest of you.

I use KDE 3.5 as a normal (non-root) user and could not play DVDs, how ever I could as root. At first I got mplayer to work as a user when I set the SUID special permission (I think I just did ```
chmod 7777 /usr/bin/mplayer
```, just turning it ALL on!).  Then mplayer worked through the command line. The GUI gave me a GTK security warning that SUID was not permissible. I searched around with little luck and then decided to check the permissions of my /dev/dvd which pointed to /dev/hdc (check local listing for your locations) I saw the group owner of /dev/hdc was the CDROM group. I added my normal user to this group and it worked perfectly after that.

I don't know what, if any, the security repercussions of this are and don't care too much since I'm the only user.

I hope this helps!
Good luck.

---

### Post by Kub on 2006-08-15
Do you have 2 dvd drives installed in your computer? I've encountered exactly the same problem as you had, the same error message and all, and I was quite puzzled until I inserted the dvd to my second drive and voila - it worked just fine :)

It's a dumb answer from my part, I know, but sometimes most obvious solution is hardest to find...

---

### Post by Tamihania on 2006-08-15
> **Kub said:**
> Do you have 2 dvd drives installed in your computer? I've encountered exactly the same problem as you had, the same error message and all, and I was quite puzzled until I inserted the dvd to my second drive and voila - it worked just fine :)

It's a dumb answer from my part, I know, but sometimes most obvious solution is hardest to find...

I know that the question was not directed to me - but having the same problem I would like to answer... I do not have 2 dvd drives...In fact I have just one cdrom drive: QSI CD-RW/DVD-ROM SBW242B... And having it I can play all CD's, burning and reading data CD's but - it's impossible to read any DVD's (luckily it's not DVD burner...lol)

Anyway - thank you for your trials Kub :)

tami

---

### Post by Kub on 2006-08-15
> **Tamihania said:**
> I know that the question was not directed to me - but having the same problem I would like to answer... I do not have 2 dvd drives...In fact I have just one cdrom drive: QSI CD-RW/DVD-ROM SBW242B... And having it I can play all CD's, burning and reading data CD's but - it's impossible to read any DVD's (luckily it's not DVD burner...lol)

If it was dvd burner, you could check something in xine (for example):

settings > setup > media > device used for DVD playback

... and if there's /dev/dvd change it to /dev/dvdrw. 

That was it in my case. I'm wondering if changing it to /dev/cdrw would work in your case.

---

### Post by DirtDawg on 2006-08-16
I was having the same trouble. Here's how I fixed it.

In Mplayer, under PREFRENCES>>MISC , at the bottom is a location for DVD device. I changed that path from **/dev/dvd** to **/media/cdrom**.

Works like a champ now! 

Hope this helps another lost soul somewhere.

---

### Post by akshaysrinivasan on 2006-08-16
i installed all the codecs and mplayer seems to work fine.totem is stupid,it never works!

---

### Post by Tamihania on 2006-08-16
For the first - big thank you for trying to help to you Kub and you DirtDwag - it cheers me up a bit...I am trying to intuitively solve the problem for more than 10 days now.

I tried your advices ( to change the settings in video players - both mplayer and and xine...) - unfortunately without any success:( You see - my dvd part of cdrom drive does not mount! at all...

After reading all possible treads (both on Ubuntu forum and Gentoo - following the advice of my son...lol) on the subject I have just two ideas:

- either my dvd laser is borked - it means I have to invest in another drive in the far future...:cry:

- or something is wrong with the kernel (after reading the advice of parminder [here)]("http://forums.gentoo.org/viewtopic-t-416550-highlight-parminder.html")

I did not try out the advice given in Gentoo Forum by parminder because: 1. their structure of directories is different to ours, 2. I am afraid that it will bork my system... which despite of dvd works perfect.

Sorry for such a long answer - but I really appreciate any help I could get here... and still wait for any advices and tips..

Many friendly regards,

tami

PS. I can play CD's and write data CD's on the same drive - it's just problem with DVD's...on my QSI CD-RW/DVD-ROM SBW242B...

---

### Post by Krzysztof on 2006-08-16
I had the same problem that is:
1. some DVD movies were played by mplayer and VLC
2. some DVD movies were not played by any player with different error codes (cannot open dvd://1 in VLC)

I installed whatever applied to video as described here:
[https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")

I believe that windows codecs and playing encrypted DVDs helped finally.
I also checked my region code with regionset but it was ok (2 for me)
Now I can play all dvds including menus with VLC which is just fine for me.

However, totem still does not work (I don't understand why it is included in the distribution since it never works :confused: ). Gxine does not work for all movies.

---

### Post by fuzzmo on 2006-08-16
had exactly the same problem (checked path, checked regionset etc.) - I double checked that I had libdvdcss2 installed - which of course I didn't.  Installed and everything runs fine.  

I know you guys are pretty sure that everything is installed - but then again so was I.  All I can say is double/triple check that you have everything installed.

---

### Post by lemix on 2006-08-27
a lot of people are offering a lot help in this thread but there is a simple command that you can enter that i have used that is somewhere in this forum. the trouble is finding it. it had something to do with the libdvdcss2, and after you update it, it fails.

my problem was only with certain types of dvd's. since im running dapper im garunteed to be running the new libdvdcss2 or whatever...

Ill find it and repost it in this forum

---

### Post by lemix on 2006-08-27
found my solution again finally after an hour of searching...

Hope this helps all!
> sudo /usr/share/doc/libdvdread3/examples/install-css.sh
enter that and it should fix it, just run after every update or dont update the libdvdcss file

-lemix

---

### Post by barranco on 2006-08-27
I can only play DVDs I booted the system with, so I guess there is something maybe on how the DVD mounts at boot time than when I insert the disc once ubuntu is running.

anyone had something similar?

---

### Post by dentaku65 on 2006-08-27
try to install Ogle and launch it from the console... usually is one of the best dvd player (yet very basic) and very good for debugging...

---

### Post by altonbr on 2006-08-29
> **jordilin said:**
> When I insert a DVD movie and try to play it through mplayer I get a pop up window that says **failed to open dvd://1**  I've followed the instructions given in [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats) and no help (I've installed libdvdcss2 and totem-xine)
[IMG]http://personal.telefonica.terra.es/web/personalinfo/failedtoopen.png[/IMG]
Any help? thanks

I had the same problem with MPlayer... so I installed totem-xine and that program seems to work.. I don't like how I have to have two movie players though... totem plays DVDs MPlayer plays AVIs and MPGs.

---

### Post by Feanor on 2006-08-30
> **lemix said:**
> found my solution again finally after an hour of searching...

Hope this helps all!

enter that and it should fix it, just run after every update or dont update the libdvdcss file

-lemix

This works for me ;) 
Many thanks, I've got the problem on kaffeine (with xine engine) and all other players, but now is solved.

---

### Post by dangledoof on 2006-09-17
I have installed Easyubuntu, but DVD:s won't run. I've tried Kaffeine, Totem-Gstreamer, Totem-Xine, VLC, Mplayer and Codeine, but all I get is 'DVD not mounted' or 'No plugin installed'. Only player which somewhat worked was VLC. It tries to open the disc and even manages to do so, but when I press "play" there is no video. I also tried to do this: 
     sudo /usr/share/doc/libdvdread3/examples/install-css.sh

but with no results.

---

### Post by dpoole on 2006-09-17
Meanwhile, if you want to play your DVD now and fix this problem at leasure. I downloaded Geexbox Open Media Centre, is only 6.8 mb, is an iso. Create the 7 mb operating system CD. Load it, restart computer, it loads itself into ram,and ejects, put your DvD in and it plays, does for me. I am also looking at your advice howto play in ubuntu.

---

### Post by C00P88 on 2007-10-31
I've been unable to play dvd's on Ubuntu for well over a week now. I've installed libdvdcss2, tried totem with the xine backend, mplayer,vlc,  blah blah blah. I popped in an unencrypted DVD and it plays fine in Totem/xine. However, I still get the "failed to open dvd://1" no matter how much I mess with the settings. I've decieded mplayer is good for streaming certain internet media, and that's about it.

---

### Post by zaphod777 on 2007-10-31
Gutsy has automatic codec installation. It has made it a breeze to play any media. SOme may consider upgrading but it may cause more problems than good since some people are having problems but it works great for me.

---

### Post by odysseusjak on 2007-10-31
I had to ditch totem altogether and go with mplayer.  I also use VLC.  What I did was open a terminal and typed sudu cd /usr/share/doc/libdvdread3.  Then, after typing in my password, I typed ./install-css.sh.  After that, DVDs worked just fine.

---

### Post by lgambett on 2007-11-01
Hi all,
I installed from scratch Kubuntu Gutsy then launched the script from [http://users.piuha.net/martti/comp/ubuntu/en/install.html](http://users.piuha.net/martti/comp/ubuntu/en/install.html)
(it means also installing Medibuntu). After this DVDs played regularly in VLC, but not in Kaffeine. Then I installed dvdrip, and voilà, also Kaffeine worked perfectly. I suspect that the missing dependency was libxine-ffmpeg, but I am not so sure... dvdrip installs a lot of dependencies.
Hope that helps,
Luca

---

### Post by carlos1992 on 2007-11-01
i just install restricted drivers (add/remove) and also i use VLC i think VLC doesn't need the drivers but i don't know it works just fine

---

### Post by odysseusjak on 2007-11-30
Okay, I have to change my message.  Open a terminal and type cd /usr/share/doc/libdvdread3.  THEN you type sudo ./install-css.sh

That should work now.

---

### Post by Znort_Ubern00b on 2007-12-01
> **jordilin said:**
> Nobody else has experienced the same problem? I think this is a major issue. If you are not able to play dvd movies with your OS, what a nasty problem.


i have this problem [see here]("http://ubuntuforums.org/showthread.php?t=510615&highlight=dvd+play")

---

