---
title: "Viewing Movie clips in Firefox  (Netflix.com)"
date: 2006-06-06
forum: Desktop Environments
---

### Post by irv on 2006-06-06
This problem is a carry-over from 5.10 to 6.06. I always get an error when trying to view a movie clip while on Netflix.com website in Firefox. First, here is a snapshot of my MediaPlayerConnectivity. (If the image doesn't show up, someone please tell me how to insert an image in a post?) I used the IMG tag but it doesn't show up in the preview post.
[IMG]http://wabasha-server.net/irv/images/Screenshot.png[/IMG]
The file ext. is .asf on Netflix, so I am not sure what program I should use to view them. I think I've tried them all?
Has anyone else had this problem?

edit:
My image shows up but you can't read it.

---

### Post by emperor on 2006-06-06
mplayer supports ASF

**Supported Input Formats**[LIST]
[*](S)VCD (Super Video CD)
[*]CDRwin's .bin image file
[*]DVD, including encrypted DVD
[*]MPEG-1/2 (ES/PS/PES/VOB)
[*]RIFF AVI file format
[*]ASF/WMV/WMA format
[*]QT/MOV/MP4 format
[*]RealAudio/RealVideo format
[*]Ogg/OGM files
[*]Matroska
[*][NUT]("http://www.nut.hu/")
[*]NSV (Nullsoft Streaming Video)
[*]VIVO format
[*]FLI format
[*]NuppelVideo format
[*]yuv4mpeg format
[*]FILM (.cpk) format
[*]RoQ format
[*]PVA format
[*]streaming via HTTP/FTP, RTP/RTSP, MMS/MMST, MPST, SDP
[*]TV grabbing[/LIST]http://www.mplayerhq.hu/homepage/design7/info.html

I would suggest that you uninstall the Firefox Media Connectivity extension and install the mplayer-plugin and check that all codecs are installed. 

See this site for codecs install package:
[http://wiki.ubuntu-fr.org/doc/plf]("http://wiki.ubuntu-fr.org/doc/plf")

Or get directly from mplayerhq.hu, you may need more than just the essential ones!

---

### Post by irv on 2006-06-07
I discovered that my problem is deeper that playing movies in firefox. I tried to run my mplayer from the applications menu and it error's out. (and error box pops up and goes away, doesn't tell me anything). I did a complete removeal and reinstalled it, but it still error's out. Has anyone got any ideas on what is causing this? I think if I can get mplayer to work this might fix my other problems.
Oh, one more thing! I have no idea on how to intall codecs?
Thanks

---

### Post by emperor on 2006-06-07
[quote=irv]Oh, one more thing! I have no idea on how to intall codecs?
Thanks[/quote] 
Download codecs and read the readme as indicated on the gmplayer website:

********
**Codecs**

       Our codec packages are unusable by normal Windows movie players     since they come without installer. Get the essential codec     package for Linux or choose from the other codec packages.     For installation instructions look at the README contained     in each package, the general     [README]("http://www.mplayerhq.hu/DOCS/README") or the     [installation section]("http://www.mplayerhq.hu/DOCS/HTML/en/install.html")     of the documentation.

[http://www.mplayerhq.hu/design7/dload.html]("http://www.mplayerhq.hu/design7/dload.html")

************

gmplayer will not do much without the codecs installed. They are NOT installed via synaptics unless you add the repository I mentioned in a previous post. However, you can download the codecs and do a manual install. There is more information in the forums concerning this subject.

Also, run gmplayer from a terminal session which should allow the errors messages to be printed to the console.

As I recall, the font package for mplayer must also be installed.

---

### Post by irv on 2006-06-07
[QUOTE=emperor]Download codecs and read the readme as indicated on the gmplayer website:

********
**Codecs**

       Our codec packages are unusable by normal Windows movie players     since they come without installer. Get the essential codec     package for Linux or choose from the other codec packages.     For installation instructions look at the README contained     in each package, the general     [README]("http://www.mplayerhq.hu/DOCS/README") or the     [installation section]("http://www.mplayerhq.hu/DOCS/HTML/en/install.html")     of the documentation.

[http://www.mplayerhq.hu/design7/dload.html]("http://www.mplayerhq.hu/design7/dload.html")

************

gmplayer will not do much without the codecs installed. They are NOT installed via synaptics unless you add the repository I mentioned in a previous post. However, you can download the codecs and do a manual install. There is more information in the forums concerning this subject.

Also, run gmplayer from a terminal session which should allow the errors messages to be printed to the console.

As I recall, the font package for mplayer must also be installed.[/QUOTE]

As far as running gmplayer in a terminal here is the error code:

irv@ubuntu:~$ gmplayer
MPlayer 2:0.99+1.0pre7try2+cvs20060117-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: Intel Pentium 4/Celeron 4 Northwood; Pentium 4 EE/Xeon Prestonia,Gallatin (Family: 15, Stepping: 9)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.



91 audio & 204 video codecs
Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.
[skin] file ( /usr/share/mplayer/Skin/default/skin ) not found.
Skin not found (default).
irv@ubuntu:~$
Is the line that has 91 audio & 204 video codecs telling me I have the codecs loaded? I am not sure what all the stuff about the Joystick is all about (I don't have a joystick installed). I see I am getting a connect to socket error plus opening LRC support. And the last thing it said was Skin not found.
Does this give you a clue what is going on.
Thank, Irv

---

### Post by emperor on 2006-06-07
Yes, there are some codecs installed. 

It appears the fatal problems is the the default skin for the player is not installed.
In dapper,  the skins may all be in a separate package called: mplayer-skins

here's what I have installed in the default skin directory:

emperors@realm:/usr/share/mplayer/Skin/default$ dir
about.png    barstop.png  main-silver.png  pos.png             stop.png
bareqb.png   barzoom.png  menu.png         preferences2.png    subblue.png
barexit.png  eqb.png      menus.png        prefs.png           subload.png
barffwd.png  exit.png     minimize.png     prev.png            symbols2.png
barfwd.png   font.fnt     mute.png         progres-long2c.png  symbols.fnt
barmute.png  font-pl.png  next.png         progres-long2d.png  symbolsg.fnt
barplay.png  forward.png  playbar.png      rev.png             zoom-3.png
barrev.png   load.png     playlist.png     skin
barrevv.png  main.png     play.png         skinb.png

---

### Post by irv on 2006-06-07
[QUOTE=emperor]Yes, there are some codecs installed. 

It appears the fatal problems is the the default skin for the player is not installed.
In dapper,  the skins may all be in a separate package called: mplayer-skins

here's what I have installed in the default skin directory:

emperors@realm:/usr/share/mplayer/Skin/default$ dir
about.png    barstop.png  main-silver.png  pos.png             stop.png
bareqb.png   barzoom.png  menu.png         preferences2.png    subblue.png
barexit.png  eqb.png      menus.png        prefs.png           subload.png
barffwd.png  exit.png     minimize.png     prev.png            symbols2.png
barfwd.png   font.fnt     mute.png         progres-long2c.png  symbols.fnt
barmute.png  font-pl.png  next.png         progres-long2d.png  symbolsg.fnt
barplay.png  forward.png  playbar.png      rev.png             zoom-3.png
barrev.png   load.png     playlist.png     skin
barrevv.png  main.png     play.png         skinb.png[/QUOTE]

Ok, here's where I am at. I downloaded the skins and put them in the default directory. Now the player starts up, but when I run it from within firefox, I get a codec error. “Cannot find codec matching selected -vo and video format 0x33564D57.” I have sound but no video.
I downloaded the essential codecs package and copied them to the default directory, “/usr/local/lib/codecs/”. This directory was not there I had to create it. In the readme file it had this:
“Put the files contained in this archive in a directory where MPlayer will find
them. The default directory is /usr/local/lib/codecs/ ($prefix/lib/codecs/) if
you are compiling from source, but you can change that value by passing the
'--with-codecsdir' option to './configure'.”

The last part I am not sure of: passing the '--with-codecsdir' option to './configure'. Do I have to change the configure somewhere?

---

### Post by emperor on 2006-06-07
[quote=irv]The last part I am not sure of: passing the '--with-codecsdir' option to './configure'. Do I have to change the configure somewhere?[/quote]

"./configure" is done prior to compiling from source, so this does not apply to your case.

I would recommend that you use the embedded mplayer plugin instead of the extension that tries to call the player. I had major problems with the firefox media extension and removed it.

There could also be a codec missing but shouldn't be according to the documentation at mplayerhq. It this problem resists it may take some further research to track it down.

---

### Post by emperor on 2006-06-07
You might try XINE in place of mplayer. I saw a post on the net where ASF file support was mentioned. You can install xine in addition to mplayer.  You'll need the Mozilla Media extension plugin in this case.

---

### Post by mgmiller on 2006-06-07
In your post you said:

I downloaded the essential codecs package and copied them to the default directory, “/usr/local/lib/codecs/”. This directory was not there I had to create it. In the readme file it had this:
“Put the files contained in this archive in a directory where MPlayer will find
them. The default directory is /usr/local/lib/codecs/ 


I know it says that, but it's wrong.  put the codecs into /usr/lib/codecs

This worked for me.

Ubuntu does some slighlty different things with file structure compared to stock debian.

Good Luck.

---

### Post by emperor on 2006-06-07
Codecs are in "/usr/lib/win32" on my laptop with Ubuntu 6.06 and mplayer works great!

---

### Post by irv on 2006-06-08
[QUOTE=mgmiller]In your post you said:

I downloaded the essential codecs package and copied them to the default directory, “/usr/local/lib/codecs/”. This directory was not there I had to create it. In the readme file it had this:
“Put the files contained in this archive in a directory where MPlayer will find
them. The default directory is /usr/local/lib/codecs/ 


I know it says that, but it's wrong.  put the codecs into /usr/lib/codecs

This worked for me.

Ubuntu does some slighlty different things with file structure compared to stock debian.

Good Luck.[/QUOTE]
I moved the codecs file from /usr/local/lib/codecs to /usr/lib/codecs and I still get the same error. I did restart firefox before trying. Also, I had to create the directory codecs under /usr/lib/. 
I am now starting to see if I can get xine to work. As I remember I moved away from it in 5.10 because I had some issues with it!

---

### Post by irv on 2006-06-08
[QUOTE=emperor]Codecs are in "/usr/lib/win32" on my laptop with Ubuntu 6.06 and mplayer works great![/QUOTE]
I don't even have the win32 directory in /usr/lib on my desktop!

---

### Post by WorLord on 2006-06-08
Create it.

---

### Post by emperor on 2006-06-08
[quote=irv]I don't even have the win32 directory in /usr/lib on my desktop![/quote]

Normally you will not have /usr/lib/win32.

You can either move them
sudo mv /usr/lib/codecs /usr/lib/win32

or leave them in the default location and create a symbolic link to where you
think they may need to be:

sudo ln -s /usr/lib/codecs /usr/lib/win32

Symbolic links are quite handy!

---

### Post by irv on 2006-06-09
[QUOTE=emperor]Normally you will not have /usr/lib/win32.

You can either move them
sudo mv /usr/lib/codecs /usr/lib/win32

or leave them in the default location and create a symbolic link to where you
think they may need to be:

sudo ln -s /usr/lib/codecs /usr/lib/win32

Symbolic links are quite handy![/QUOTE]
Seeing I have everything working I will leave them where they are and make the symbolic link.
In closing the way in got everything to work is to add the w32codecs. I continued to used mplayer
Thanks again for all your help.\\:D/

---

