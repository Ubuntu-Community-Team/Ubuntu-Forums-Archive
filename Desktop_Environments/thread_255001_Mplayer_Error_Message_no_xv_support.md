---
title: "Mplayer Error Message no xv support"
date: 2006-09-10
forum: Desktop Environments
---

### Post by JPMaximilian on 2006-09-10
I'm running 6.06 on an acer notebook with a Radeo 200M video card.  I get a message when I play .wmv movies in mplayer:

It seems there is no Xvideo support for your video card available.
Run 'xvinfo' to verify its Xv support and read DOCS/HTML/en/video.html#sv!
See 'mplayer -vo help' for other (non-xv) video out drivers.  Try - vo x11

I ran the command xvinfo, and there is "no adapters present."  The video still runs, albeit slightly distorted resolution wise.  Video ran fine without this error message before I installed the proprietary ati drivers.  Any help on how to fix this is appreciated.

---

### Post by JPMaximilian on 2006-09-10
i ran the cmnd:

sudo mplayer - vo xv

and now when I open Mplayer I get a new error message:

Error opening/initializing the selected video_out (-vo) device.

Again, any help would be appreciated.

---

### Post by kwalo on 2006-09-11
You probably don't have xv video out in your mplayer install. Run```
mplayer -vo help
```Too see if that's true. You can try any of theese options. I suggest using gl, gl2, sdl, x11 (in that order) to see which one satisfies you.
If you still want to run mplayer with xv video out, install **libxv1** package. And check again```
mplayer -vo help
```wether this option is available. If it isn't, try compiling mplayer from source. You'll need libxv-dev package to get xv output available. Of course you'll need to install build-essential and other -dev packages required by mplayer.

---

### Post by taurus on 2006-09-11
If xv is giving you an error, then use x11 instead!!!

---

### Post by JPMaximilian on 2006-09-11
How do I got about using x11 instead?

mplayer - vo x11  ?

Does that recompile mplayer using a different output driver?

---

### Post by kwalo on 2006-09-11
> **JPMaximilian said:**
> How do I got about using x11 instead?

mplayer - vo x11  ?

Does that recompile mplayer using a different output driver?

No. That just runs mplayer with video output set to x11. You have to give this option every time, you want to use mplayer with that option.

Alternatively you could save that option to your config file. Open, or create ~/.mplayer/config file and add the following line:```
vo=x11
```Now you don't have to specify -vo x11 option every time.

---

### Post by Yuzem on 2006-12-06
I have the same problem. Sudently i have no xv output on mplayer.
The thing is that with gmplayer xv output works.
I was traing to install mplayer rc1 when this happens.
I'm on edgy and I have AIGLX.
What can I do to have mplayer (no gmplayer) with xv video output?

Thanks in advance.

---

### Post by JPMaximilian on 2006-12-06
I since found a fix, I went to preferences->video you can choose a different output.  However, when playing .avi files I get an error:

Requested audio codec family [mp3] (afm=mp3lib) not available Enable it at compilation.


I didn't compile mplayer, what does that mean?

---

### Post by JPMaximilian on 2006-12-06
I get the same error for .mpeg files, but not .wmv files.

---

### Post by taurus on 2006-12-06
> **JPMaximilian said:**
> I since found a fix, I went to preferences->video you can choose a different output.  However, when playing .avi files I get an error:

Requested audio codec family [mp3] (afm=mp3lib) not available Enable it at compilation.


I didn't compile mplayer, what does that mean?

Applications -> Sound & Video -> MPlayer Movie Player -> Preferences -> Codecs & demux.  Make sure both "Video codec family" & "Audio codec family" are using the "FFmpeg's libavcodec codec family" & "FFmpeg/libavcodec audio decoders", respectively.

Then restart.

---

### Post by JPMaximilian on 2006-12-07
Taurus, awesome, that fixed it, thanks a bunch!

---

### Post by taurus on 2006-12-07
You're welcome.

---

### Post by Yuzem on 2006-12-08
Anyone knows why gmplayer works fine with xv output but mplayer doesn't?

---

### Post by Yuzem on 2006-12-28
I found the answer.
Just in case other have the same problem i will post the solution here.
My problem was that the xv output and the alsa output didn't work with mplayer-nogui. Even with -ao oss some files sounded very bad.
The rare thing was that gmplayer worked perfectly.

what i did was:
```
which mplayer
```
This gave me the location of the mplayer executable.
then:
```
sudo rm "the path to mplayer"
```

It happens that uninstalling mplayer rc1 didn't worked very well. Installing and uninstalling and installing again the official mplayer-nogui didn't fix it. Neither an automatix install and uninstall of mplayer worked.

---

