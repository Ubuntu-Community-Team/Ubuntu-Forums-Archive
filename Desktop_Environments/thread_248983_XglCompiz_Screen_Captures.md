---
title: "Xgl/Compiz Screen Captures"
date: 2006-09-01
forum: Desktop Environments
---

### Post by markthecarp on 2006-09-01
Hi All,

I have Xgl and Compiz working on my desktop machine. It is running dapper with a modified /etc/apt/sources.list following the wiki on installing Xgl/Compiz.

I would like to record my steps and current affects in some way. What are people using to make short videos for youtube or hotair?

I'm hooked on 3d desktops now!

-mark

---

### Post by methogen on 2006-09-02
That would be great! I am a new ubuntu user, I have been trying to get XGL to work for weeks. I have tried the howto all the way to scripts to install everything. I know my system will run it Kororaa ran it great. I have a 9800 pro ATI card and I am out of options.

---

### Post by ayoli on 2006-09-02
I know istanbul session recorder (but havent yet tested)
```
apt-cache show istanbul
``` says:
Description: Desktop session recorder
 Istanbul is a desktop session recorder for the Free Desktop.
 It records your session into an Ogg Theora video file.
 To start the recording, you click on its icon in the
 notification area. To stop you click its icon again.
 .
 It works on Gnome, KDE, XFCE and others.
 .
 Homepage: [http://zaheer.merali.org/mediawiki/index.php/Istanbul](http://zaheer.merali.org/mediawiki/index.php/Istanbul)
you may try this.
regards.

---

### Post by markthecarp on 2006-09-02
Thanks ayoli. I tried that first since it was in the ubuntu repos. It doesn't work very well. The mpeg's it produces only show the last couple of seconds of the capture. I slide that to the "to look at later" list.

I also found mentions of xvidcap on the Compiz [forum]("http://www.compiz.net/topic-2304-4.html").

[Xvidcap]("http://xvidcap.sourceforge.net/") works but I'm having to reduce my screen resolution to 1024x768 from 1280x1024 to get reasonable file sizes. Also no menu entry was created so for now I'm starting it from a command line. The deb package offered by the maintainer did not work on my system. The deb package available on sourceforge works on my system. If I can manage to make something half way decent I'll post it or a link.

methogen I followed the following wiki pages...
[https://help.ubuntu.com/community/CompositeManager]("https://help.ubuntu.com/community/CompositeManager")
[https://help.ubuntu.com/community/CompositeManager/Xgl]("https://help.ubuntu.com/community/CompositeManager/Xgl")
Method A
[https://help.ubuntu.com/community/CompositeManager/InstallingCompiz]("https://help.ubuntu.com/community/CompositeManager/InstallingCompiz")
Method A also
[https://help.ubuntu.com/community/CompositeManager/ConfiguringCompiz]("https://help.ubuntu.com/community/CompositeManager/ConfiguringCompiz")

Off to feed the spousal unit.

-mark

---

### Post by ayoli on 2006-09-02
yep i've already heard that istanbul doesnt work very well, i also forgot to mention xvidcap which seems to be quite old (last release two years ago). gld to hear that you get it working almost nice.
you might use alacarte menu edtor (in accessories menu) to create a menu entry.
regards.

---

### Post by markthecarp on 2006-09-02
> **ayoli said:**
> yep i've already heard that istanbul doesnt work very well, i also forgot to mention xvidcap which seems to be quite old (last release two years ago). gld to hear that you get it working almost nice.
you might use alacarte menu edtor (in accessories menu) to create a menu entry.
regards.

The 1.1.3 version is quite old, that's the one that did not work for me. The newer [one]("http://sourceforge.net/project/showfiles.php?group_id=81535") is 1.1.4rc1, dated 2006-08-27. That's the one that is working here. It's buggy, especially the gui.

At the 1280x1024 resolution I'm only capturing an average 3.8 fps, which is too slow for mpeg. Inadequate hardware at least at that resolution.

smokey is
AMD 2000+ 1.67 Ghz
512M ram
Nvidia GeForce2 MX/MX 400 
17" NEC AccuSync 70 CRT monitor
Dapper with the 2.6.15-26-k7 kernel

I am pushing the limits a bit. It works nice live but capturing is too much and I'm not sure what part of the hardware is the limiting factor. 

-mark

---

### Post by someguyouknow on 2006-09-03
Xvidcap isnt working too well for me. 
I am not getting anything but scrambled video.

---

### Post by markthecarp on 2006-09-03
> **someguyouknow said:**
> Xvidcap isnt working too well for me. 
I am not getting anything but scrambled video.

Hi someguy, cool nick btw, what does the info box that pops up at the end of a capture show? At my preferred screen resolution of 1280x1024 my machine can't do better than 3.8 fps. Mpeg requires at least 7.5 fps.

I'm about to put the goodies on another box that is quite a bit stronger than my workstation box (smokey). 

Test Box Specs (hostname=spinach):
P4 2.8Ghz dual core so kernel 2.6.15-26-686 shows 2 cpu's
nVidia Corporation NV18 [GeForce4 MX 4000 AGP 8x] (rev c1) unknown vram
1.5 G ram
same CRT monitor connected via a KVM switch

-mark

---

### Post by markthecarp on 2006-09-03
I've got to learn how to post process my screen captures. All this is working nicely live on two machines here. I plan to post to the success story thread soon. 

I've put a screenshot of xvidcap on [flickr]("http://www.flickr.com/photos/markthecarp/233296720/"). My captures are just too big so I'm looking into ways to make them smaller. Video editing is new to me.

-mark

---

### Post by someguyouknow on 2006-09-03
> **markthecarp said:**
> Hi someguy, cool nick btw, what does the info box that pops up at the end of a capture show? At my preferred screen resolution of 1280x1024 my machine can't do better than 3.8 fps. Mpeg requires at least 7.5 fps.


Yea, the highest i got was about 6 but that wasnt good enough.  I am looking into a new card soon since mine is pretty much crap (onboard 6200).  I am surprised XGL/Compiz runs as well as it does. Xvidcap along with it is prolly torture lol.

---

### Post by markthecarp on 2006-09-03
Did you try lowering your screen resolution?

I can get pretty good captures on spinach (see above) at 1024x768. I think that with some post processing, compression for web use in particular I may have some usable captures. I continue to learn about video and compression.

Note to xvidcap searchers: works nice in 2d as well, this needs to be in the ubuntu source tree. This being xvidcap.

-mark

---

### Post by distroman on 2006-09-03
I had some trouble with the GUI crashing, when I tried to capture in fullscreen (only in a xgl/compiz session btw) but if I launch xvidcap with-
```
xvidcap --cap_geometry=1024x768
```
Then it does a really nice job, in case that helps anyone.

Remember it's home video, just for fun. 
[http://www.youtube.com/watch?v=b6ZuxLFnP5A](http://www.youtube.com/watch?v=b6ZuxLFnP5A)

---

### Post by markthecarp on 2006-09-04
Great job distroman! That's the command I've been using as well. Usually I specify the file name too. Guess I'm going to have to get a youtube account ;-)

-mark

---

### Post by methogen on 2006-09-04
Ok I followed Method A on the install and I logged on the new XGL session, the screen had a checkerboard background and a X as the mouse pointer for about 4 seconds then logged on. Everything looks great, but when I move any windows or anything for that matter is looks real choppy. Also XGL is not working now eyecandy happening.

Can you help me with an idea what might be wrong? I followed the guide in the XGL about making it so your brand of video card will work. I have a ATI Radeon 9800 pro, I know XGL will work with it because Kororaa runs great thank you for your help :)

---

### Post by methogen on 2006-09-04
nevermind I got it running now just trying to get compize up so i can tone down some of this eyecandy lol! thank you so much you are the man!

---

### Post by someguyouknow on 2006-09-06
[http://www.debugmode.com/wink/download.php](http://www.debugmode.com/wink/download.php)

suppose to be one of the better ones.

---

