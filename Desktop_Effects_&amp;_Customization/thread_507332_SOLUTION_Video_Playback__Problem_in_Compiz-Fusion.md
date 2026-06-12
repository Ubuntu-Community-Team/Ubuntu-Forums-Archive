---
title: "SOLUTION: Video Playback  Problem in Compiz-Fusion"
date: 2007-07-22
forum: Desktop Effects &amp; Customization
---

### Post by kevinmedina on 2007-07-22
SOLUTION: Video Playback Problem in Compiz-Fusion
I was searching high and low for a solution to a video playback problem while running Compiz-Fusion:

While running Compiz-Fusion, I wouldn't be able to see any video play while either moving the window, viewing desktops in expo, 3d cube, or any other cool effect for that matter; instead I would see a blue screen, including when viewing in full screen. After days of trying out all sorts of different things, I found the final solution! It is from Gremlinzzz, written in this thread: [http://ubuntuforums.org/showthread.php?t=480357](http://ubuntuforums.org/showthread.php?t=480357)

* GStreamer (The default video player in Ubuntu, totem-gstreamer, and any video player that is based on the gstreamer backend)
o Open a terminal and type "gstreamer-properties". Press Enter.
o Click the Video tab.
o Under Default Video Plugin select "X Window System (No Xv)".
o Click Test to verify that video playback is working (you should be able to see the standard TV testing colour stripes).
o Click Close

* VLC (VLC is not installed by default; you need to search in the package manager, then install)
o Start VLC and click on Settings, then Preferences.
o Expand Video and then expand Output modules. You will notice several options for output device.
o Select the item Output modules, and notice the checkbox at the bottom right that says Advanced options. Check the box, and now you have the option to select a different output device.
o Pick X11 video output
o Click on Save and you are set!

* MPlayer (Mplayer is not installed by default)
o Start Mplayer
o Right-click on the screen and select Preferences
o Select the Video tab and under Available Drivers select "X11 (XImage/Shm)"
o Click Save and restart the program for the setting to take effect.
+ Some users reported that MPlayer may not be able to show videos in full screen.

* Xine
o Start xine
o Click File, then Configure and then Preferences
o In experience_level select "Master Of The Known Universe" so that all available settings are visible.
o Select the tab for video.
o Under Driver select "xshm".
o Restart xine.
+ The same process enables Totem that has the totem-xine backend configured.
---

I'm posting this because this solution isn't advertised as being one for the blue screen problem that many people experience with Compiz Fusion but never find the solution to. I'm going to post this in a variety of other forums where I've found the problem posted. I hope this helps!!!!

---

### Post by ayoli on 2007-08-03
yay, that helped me, thx :)

---

### Post by PaulRay on 2007-09-08
I just wanted to second that big thank you! I thought I'd tried everything, but these solutions solved the problem perfectly.

---

### Post by NiceGuy on 2007-09-11
> **kevinmedina said:**
> 
+ The same process enables Totem that has the totem-xine backend configured.

Not quite true... The version of totem-xine which ships with gutsy (I haven't tried other versions) has it's own config file, xine_config, which you need to edit. This can be found in the .gnome2/Totem/ in your home folder.

Just find where it says:
```

# video driver to use
# string, default: auto
#video.driver:auto

```

and change it to:
```

# video driver to use
# string, default: auto
video.driver:xshm

```

---

### Post by TeagueSterling on 2007-09-22
Thanks for the tip Kevin.
I was not even able to open totem before this. To make the change in xine I had to temporarily load with a different drive by running ```
xine --video-driver xshm
``` I believe.
In order to get this to work with Totem in Feisty, I had to make this change manually in ```
~/.gnome2/totem_config
``` to get it to work. It was the same change NiceGuy noted above for Gusty, but in a slightly differently location.

Thanks Again!

---

### Post by DutchKillerBee on 2007-09-24
When I set the video playback to xshm my cpu is running constantly at 100 % when wachting a movie in full screen mode :(
When using the auto option only 25% but off course a blue screen when moving Totem.
I'll stick to the auto option :)
Just my 2 cents....

---

### Post by narx on 2007-09-29
thank goodness i found this thread..

been poking around for a week to find out how to make vlc work in compiz..

finally got it!! thanks man..

but now there is another problem, video quality is a little bit slack and there are sometimes delay in frames...

any idea?

thanks guys.

---

### Post by wnwek on 2007-09-30
Worked for me! Thanks!

Configuration: Ubuntu 7.04 Dell Latitude D520 512 MB RAM Intel Duo (Compiz Desktop Effects enabled)

---

### Post by msundman on 2007-10-19
It isn't really a realistic solution to use xshm. Or, well, it will show the video, but it will look worse than a baboon's behind (and eat 300-500 % as much CPU).

---

### Post by juamez. on 2007-10-21
I noticed that while X11 output in VLC gives certainty of watching the video ouput, it kind of disables (am I right?) the postprocessing that is usually done on mpeg4 encoded files, and makes it look really pixelated when maximized or in full screen. I would like another solution where this is not the case. Also the cpu usage is indeed quite high when the X11 output method is used.

---

### Post by msundman on 2007-10-21
> **juamez. said:**
> X11 output [...] disables (am I right?) the postprocessing that is usually done on mpeg4 encoded files, and makes it look really pixelated when maximized or in full screen.
I don't think it disables the postprocessing. AFAIK it just disables the nice and fast hardware-assisted interpolating scaling algorithms.

---

### Post by juamez. on 2007-10-26
> **msundman said:**
> I don't think it disables the postprocessing. AFAIK it just disables the nice and fast hardware-assisted interpolating scaling algorithms.
Whatever it may be, I would really like those fancy interpolating scaling algorithms to be applied to what I watch, please.

Anyone who knows how to fix this?

---

### Post by baldahin on 2007-10-26
works for me in Gutsy (ati-xorg, gstreamer), thanks!

and what about tvtime?

---

### Post by juamez. on 2007-10-31
I have found a way to have nice interpolated video output while still using compiz through feisty's desktop effects:

I use MPlayer with video driver X11/Xv, which delivers image with the postprocessing I was inquiring about. Also the subtitles have a nice font and outline. :)

Too bad MPlayer lacks some basic keyboard control.

/edit: I have to take back that last remark, I found that MPlayer actually has basic keyboard control: F for fullscreen switching, space for play/pause and the arrows for timewarping - which even VLC does not have. So to conclude: I'm satisfied. Yay at myself. =)

---

### Post by wnwek on 2007-11-24
What do you mean by time-warping? If you mean by keyboard-shortcuts for seeking/jumping  forwards or backwards for a video, VLC has a Ctrl+<Right>/<Left> for big jumps and Shift+<Right>/<Left> for small jumps.

This does not work for .flv videos though. I think it's because VLC is not able detect the length of the video in that case.

---

### Post by Arawn on 2007-11-24
I just want to thank kevinmedina for the solution. I use Ubuntu Gutsy and Linux Mint Daryna, and I got MPlayer working with Compiz with fglrx 8.42.3 in a Xpress 200M chipset. Big thx!! =D>

---

### Post by timseal on 2007-12-03
disclaimer: I've only tried this with one video, and not for long (I'm at work so I can't really do much testing)....  but - you might want to try the vidix driver, at [http://vidix.sourceforge.net](http://vidix.sourceforge.net)
It actually looks OK on full screen.  CPU is only at 5%.
I'm using:  Emerald, Compiz Fusion, xine (the latest version, I built it myself).

---

### Post by dakuran on 2007-12-22
THANK YOU!!!~!!!!!!!~1111 

worked like a charm, needless 2say =D

~dak

---

### Post by zubat on 2007-12-31
Thanks very much this is just what I needed!

---

### Post by armymil on 2008-01-01
Big thank you. I know its been 6 months but it worked for Gutsy. Thank you.

---

### Post by bixejo on 2008-03-04
I know it's not the ultimate solution, but it worked great for me and it's more than enough for the videos I usually play, despite of pixelation when enlarged or CPU load (which, by the way, is not too big for me).

So I must say many thanks!!

---

### Post by adityakavoor on 2008-03-04
Awsome. Thanks :popcorn:

kevinmedina U rock

---

### Post by tuxcanfly on 2008-03-06
Well yes the video is of poor quality in VLC but its certainly better in mplayer. I'll go with the solution as the blue screen is pretty irritating!

---

### Post by Alex&amp;Linux on 2008-03-06
Very Very Very helpful -it was a small annoyance, but it's relief makes things a bit easier!
I like to be able to "expo" out and glance at a music video and such.
Thanks again!

---

### Post by tuxcanfly on 2008-03-07
> **juamez. said:**
> I have found a way to have nice interpolated video output while still using compiz through feisty's desktop effects:

I use MPlayer with video driver X11/Xv, which delivers image with the postprocessing I was inquiring about. Also the subtitles have a nice font and outline. :)

Too bad MPlayer lacks some basic keyboard control.

/edit: I have to take back that last remark, I found that MPlayer actually has basic keyboard control: F for fullscreen switching, space for play/pause and the arrows for timewarping - which even VLC does not have. So to conclude: I'm satisfied. Yay at myself. =)

Hi there.....the X11/Xv driver doesnt work for me :(  Please tell me how you did it.....

I tried opening a video with 

mplayer -vo xv <file> 

The video played perfectly but didnt support transparency or effects....here's the output from terminal under section video:

```
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 352 x 240 (preferred colorspace: Mpeg PES)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try adding the scale filter, e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [libmpeg2] MPEG 1/2 Video decoder libmpeg2-v0.4.0b
Selected video codec: [mpeg12] vfm: libmpeg2 (MPEG-1 or 2 (libmpeg2))

```

---

### Post by genjosanzo on 2008-04-29
Hi all, I solved most of my problem following this guide but I still have a problem with miro. I supposed(since it utilizes gstreamer) that fixing gstreamer over totem was enough but I was wrong since miro still has the problem that totem had: no video and only audio. Anyone know how to change gstreamer option in miro?
Thanks in advance.

---

### Post by litmus on 2008-05-26
This is not a solution, but merely a by-pass of the original problem. By using the xo output you pass the responsibility of the video playback from your graphics card, to the cpu. the result is a non-overlay non-hardware scaled, pixelated video which is reminiscent of the late 90s. Im sorry but for me this is unacceptable. The solution would be to make these effects disappear whilst still using the XV extension. 
I don't mean to to say that the original poster did not do a good job on posting this by-pass. I just want to emphasize that this problem is NOT 'fixed'. So, the pursuit on trying to find a solution to the original problem should still go on.

---

