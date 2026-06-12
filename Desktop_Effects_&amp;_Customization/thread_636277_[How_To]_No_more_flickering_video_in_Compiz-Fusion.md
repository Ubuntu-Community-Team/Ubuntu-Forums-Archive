---
title: "[How To] No more flickering video in Compiz-Fusion"
date: 2007-12-09
forum: Desktop Effects &amp; Customization
---

### Post by macaholic on 2007-12-09
[SIZE="3"]**The patch now will actually download, if you were getting failed patch errors, re-download the patch and then try applying it again.**[/SIZE]
This is a how to for getting video playback to work via the Video Playback plugin, MPlayer, and a patch.
**Step 0: Uninstalling**
Make sure you don't have an older version of mplayer installed from the repos, to uninstall it type ```
sudo apt-get remove mplayer
```

**Step 1: Dependencies**
First you will need some basic dependencies for building the MPlayer source.  intltool, libtool, automake, autoconf, gcc, gettex, wget.
Simply type ```
sudo apt-get install intltool libtool automake1.9 autoconf gcc-4.2-base gettext wget 
``` then
```
sudo apt-get build-dep mplayer
```
**Step 2: Downloading/Compiling the source**
```
mkdir mplayer_install && cd mplayer_install
wget http://www3.mplayerhq.hu/MPlayer/releases/MPlayer-1.0rc2.tar.bz2
tar xvjf MPlayer-1.0rc2.tar.bz2
cd MPlayer-1.0rc2/libvo
wget http://www.fileden.com/files/2007/12/10/1637237/mplayrepatch.patch
patch -p0 vo_xv.c mplayrepatch.patch
cd ..
./configure --enable-gui 
(if you want a gui)
make 
sudo make install
```
**Step 3: Installing a skin**
You will need to install a skin also, which can be found at [http://www.mplayerhq.hu/design7/dload.html](http://www.mplayerhq.hu/design7/dload.html), here is an example of how to install one.
In the same terminal window type:
```
wget http://www.mplayerhq.hu/MPlayer/skins/Ater-1.2.tar.bz2
tar xvjf Ater-1.2.tar.bz2
```
Change the folder name to "default" by doing
```
mv Ater default
```
Then to install it enter
```
sudo cp -a default /usr/local/share/mplayer/skins/
```
**Step 4: Running**
At this point you will have mplayer and can run it via gmplayer in terminal, and, it should have created a shortcut in Applications > Sound & Video Enjoy your flickerless video! To view in fullscreen, I suggest using the zoom plugin, because for some reason mplayer's fullscreen mode doesen't really work, and wen you zoom, unlike in other cases, the quality stays the same as if it were in fullscreen.
Here is a test file, download/run it w/ the following
```
wget http://www.fileden.com/files/2007/12/10/1637237/test_video.mp4
gmplayer test_video.mp4
```
If it plays and the video doesn't flicker, you have successfully installed it.
**Step 5: Clean up**
If you want, you can get rid of all the files downloaded by typing ```
cd ~ && rm -r mplayer_install
```
**If you encounter problems, or if it worked for you please post below.**

Credits: patch section (and a good compiz blog) from [http://smspillaz.wordpress.com](http://smspillaz.wordpress.com)

---

### Post by blazercist on 2007-12-09
Uhm, why would you do all that when you can just change from XV output to X11 and the video will stop flickering.  You can do this with each and every media player app you have like VLC and mplayer and xine and whatever.   Just switch the video driver to X11.

X11 uses more CPU, but its easy and it works.  To get a real fix we'll just have to wait for ATI to get their act together, but that may take a while.

---

### Post by macaholic on 2007-12-09
> **blazercist said:**
> Uhm, why would you do all that when you can just change from XV output to X11 and the video will stop flickering.  You can do this with each and every media player app you have like VLC and mplayer and xine and whatever.   Just switch the video driver to X11.

X11 uses more CPU, but its easy and it works.  To get a real fix we'll just have to wait for ATI to get their act together, but that may take a while.
That doesen't always work in all cases, mine for example. I forgot why...

---

### Post by craigyjack on 2007-12-09
I do not have flickering video - i have absolutely no video when in compiz - where the video should be is just a scambled static picture of green lines and crap.
I do not know what the problem is. changing to X11 video output did not help at all. and i'd rather not install a patched mplayer to use, as i prefer totem or vlc and they worked perfect before.
-craig

---

### Post by macaholic on 2007-12-10
Well, then you are out of luck for now. I know someone is working on a patch for vlc and other players, but installing the patched mplayer might work for you, always worth a shot.

---

### Post by hanzomon4 on 2007-12-10
Should I uninstall mplayer from the repos first?

---

### Post by hanzomon4 on 2007-12-10
I get this when applying the patch```
patch unexpectedly ends in middle of line
patch: **** Only garbage was found in the patch input.

```

---

### Post by macaholic on 2007-12-11
> **hanzomon4 said:**
> I get this when applying the patch```
patch unexpectedly ends in middle of line
patch: **** Only garbage was found in the patch input.

```
re-download the patch file via wget. Should fix that.

---

### Post by macaholic on 2007-12-11
Fixed various problems, typos, file locations etc.
Also changed the manual rename to a command.

---

### Post by macaholic on 2007-12-11
Added a test video, that should test that the audio/video works.

---

### Post by hanzomon4 on 2007-12-11
That is so freaking neat dude!!!

---

### Post by macaholic on 2007-12-11
What is? Did it work?

---

### Post by doublethink on 2007-12-11
TY the whole thing worked with no problems!!! :)

---

### Post by the.ant on 2007-12-11
> **macaholic said:**
> 

```
sudo apt-get install build-dep mplayer
```


What's the install for? I get an error message with it. It seems to work when I drop it.

---

### Post by macaholic on 2007-12-11
Most cases you won't need it, but it is the build dependencies for mplayer, since this is a blanket how to, I added it just in case. And I fixed the problem, you have to type it in its own line. BTW, did your install work?

---

### Post by the.ant on 2007-12-11
Thanks for the howto, worked like a charm! 

just switching to X11 didn't work for me either, besides, i prefer mplayer over vlc anyways

---

### Post by hanzomon4 on 2007-12-12
> **the.ant said:**
> What's the install for? I get an error message with it. It seems to work when I drop it.

That should be ```
sudo apt-get build-dep mplayer
```

---

### Post by macaholic on 2007-12-12
Thank you, fixed that.

---

### Post by VictorGavrish on 2007-12-24
Already posted this at compiz-fusion forums, but repeating here:

I've done everything like you said, and everything seems to have worked (no mistakes), but mplayer doesn't preserve aspect ratio anymore. When I do 'metacity --replace', everything is fine again, but once I return to 'compiz --replace', the video is always the size and shape of the window. Can it be rectified somehow?

Besides, the patch doesn't seem to have worked. How can I check?

I'm using Intel/AIGLX, Ubuntu 7.10 and its default compiz.

---

### Post by glantucan on 2007-12-30
> **craigyjack said:**
> I do not have flickering video - i have absolutely no video when in compiz - where the video should be is just a scambled static picture of green lines and crap.
I do not know what the problem is. changing to X11 video output did not help at all. and i'd rather not install a patched mplayer to use, as i prefer totem or vlc and they worked perfect before.
-craig

Well actually some people in this thread is completely wrong :p  You can use vlc, and other players I guess, as long as they don't use opengl(xgl) for video output. 

In vlc you can change video output in Options->Preferences->Video->Output Modules-> and then change from OpenGL video output to X11 video Output.

It does work on my system smoothly and without glitches or patches. :popcorn:

Have fun

---

### Post by Clouds® on 2008-01-02
macaholic, thanks a lot, worked very nice!

At first I feared the 'make' command wasn't going so well (lot of warnings, long execution time) but your instructions made my flickering go away!

Thanks again!

--
Clouds

---

### Post by CypherHackz on 2008-01-04
i got this error when i startup mplayer

> New_Face failed. Maybe the font path is wrong. 
Please supply the text font file (~./.mplayer/subfont.ttf)

and when i play a video another error appear.

> [AO_ALSA] Unable to find simple control 'PCM',0.

so how to fix those problems? thank you very much.

-cypher/

---

### Post by shareMenaPeace on 2008-01-09
> **glantucan said:**
> Well actually some people in this thread is completely wrong :p  You can use vlc, and other players I guess, as long as they don't use opengl(xgl) for video output. 

In vlc you can change video output in Options->Preferences->Video->Output Modules-> and then change from OpenGL video output to X11 video Output.

It does work on my system smoothly and without glitches or patches. :popcorn:

Have fun

Setting this option to x11 fixed it, thanx

---

### Post by Ace2016 on 2008-03-01
Very nice patch, now mplayer works perfectly

Interesting, the size of the video on the screen doesn't seem to have much of an effect on the performance, i tested with a 1280x720 video file i got off stage6 just before it closed

Thank you very much :)

---

### Post by kommissar on 2008-03-24
Wonderful, this worked for me with xv output.  It even scales my video when I go fullscreen!

---

### Post by c4v3m4n on 2008-04-20
> **craigyjack said:**
> I do not have flickering video - i have absolutely no video when in compiz - where the video should be is just a scambled static picture of green lines and crap.
I do not know what the problem is. changing to X11 video output did not help at all. and i'd rather not install a patched mplayer to use, as i prefer totem or vlc and they worked perfect before.
-craig

I just install totem movie player and change to X11 video output.  that helped me, just type gstreamer-properties to get to the settings to change it.

---

### Post by jsa on 2008-04-21
The reason why people go through all this trouble instead of just using X11 output is the video quality and GPU acceleration. X11 video looks just horrible. You can test it by reverting back to Metacity and comparing video quality between X11 and Xv. This is why I use Xv even though some video cards (including mine) have some problems with it with compiz fusion enabled.

I sure am glad some work is being done to address the problem. Things seem to look a little brighter for us Intel users at the moment: [http://hoegsberg.blogspot.com/2008/03/i-just-committed-last-bit-of-dri2-work.html](http://hoegsberg.blogspot.com/2008/03/i-just-committed-last-bit-of-dri2-work.html)

---

### Post by fatfatwolf on 2008-06-15
It fixes the flickering problem, yet the full screen no longer works now... Full screen is just blank screen...lol

---

### Post by Tristan_F on 2008-07-23
Well, it works for me but I also cannot have the video playback full screen. None of video output works if I specify one of them. Would anyone have any trick to be able to have the video full screen even using some compiz plugins?

---

