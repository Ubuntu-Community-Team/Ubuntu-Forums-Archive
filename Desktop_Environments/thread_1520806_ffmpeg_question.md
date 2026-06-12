---
title: "ffmpeg question"
date: 2010-06-30
forum: Desktop Environments
---

### Post by Amy_1990 on 2010-06-30
I am using ubuntu 10.04lts Searching on google i found a way to turn youtube video's into mp3's .ogg avi and mpeg using ffmpeg so i installed it using FakeOutdoorsman guide but i don't know how to convert them.Can someone help me.
Please thank you

---

### Post by claracc on 2010-06-30
This link can help you: [http://www.catonmat.net/blog/converting-youtube-flvs-to-a-better-format-with-ffmpeg/](http://www.catonmat.net/blog/converting-youtube-flvs-to-a-better-format-with-ffmpeg/)

---

### Post by nothingspecial on 2010-06-30
Open gedit (the text editor in the accessories menu) and copy and paste this
```

#convert flv to mp4
for f in *.flv 
    do 
    ffmpeg -i "$f" -acodec libfaac -ab 128kb -vcodec mpeg4 -b 1200kb -mbd 2 \
    -flags +4mv -trellis 2  -cmp 2 -subcmp 2 -s 320x180 -metadata title="${f%.flv}.mp4" \
    "${f%.flv}.mp4"

done;
```Save it as flv2mp4.sh in your home directory
In a terminal type ```
chmod +x flv2mp4.sh
```Download loads of youtube videos to your home directory
type ./flv2mp4.sh
Go make a cup of coffee, drink it, then come back and all the youtube videos will have an mp4 version too.

---

### Post by Detonate on 2010-06-30
There is a GUI frontend for ffmpeg named winff.  It does not offer all of the features of ffmpeg but it should be able to do a simple conversion.  Also see man ffmpeg.

---

### Post by Amy_1990 on 2010-06-30
Thank you all

I installed winff looks cool but it gives some kind of error.I was converting from flv to mp3.I haven't  done a flv to avi using winff yet i am going to try the command line next then i will post the errors if that doesn't work or i get mix up.

---

### Post by Amy_1990 on 2010-06-30
The command line didn't work and winff is giving this error even after i installed a new ffmpeg using FakeOutdoorsman guide 

NULL @ 0x9ea5830] [Eval @ 0xbfb96aec] Invalid chars 'b' at the end of expression '160kb'
[NULL @ 0x9ea5830] Unable to parse option value "160kb"

Here is the terminal output when i type ffmpeg just in case it is needed

FFmpeg version SVN-r23904, Copyright (c) 2000-2010 the FFmpeg developers
  built on Jun 30 2010 14:16:45 with gcc 4.4.1
  configuration: --enable-libmp3lame --enable-libtheora --enable-libopenjpeg --enable-libx264 --enable-postproc --enable-libxvid --enable-libfaac --enable-pthreads --enable-libvorbis --enable-vdpau --enable-gpl --enable-libgsm --enable-libspeex --enable-libvpx --enable-libschroedinger --enable-libdirac --enable-avfilter --enable-avfilter-lavf --enable-libdc1394 --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libnut --enable-zlib --enable-bzlib --enable-version3 --enable-nonfree --enable-x11grab --enable-swscale
  libavutil     50.19. 0 / 50.19. 0
  libavcodec    52.78. 0 / 52.78. 0
  libavformat   52.71. 0 / 52.71. 0
  libavdevice   52. 2. 0 / 52. 2. 0
  libavfilter    1.20. 1 /  1.20. 1
  libswscale     0.11. 0 /  0.11. 0
  libpostproc   51. 2. 0 / 51. 2. 0
Hyper fast Audio and Video encoder


I don't know what else to try any idea's anybody?
I like the winff it seems to be just what i was looking for to start with if i could get it working.

---

### Post by FakeOutdoorsman on 2010-06-30
Did you compile FFmpeg or did you install it from the Ubuntu repository? The default WinFF presets are outdated when using a compiled FFmpeg.  You can either update the presets or use an older FFmpeg.

To update your presets open a Terminal and enter:
```
cp /usr/share/winff/presets-libavcodec52-v5.xml ~/.winff/presets.xml
```
Or you can open your file browser (called Nautilus I think), show all directories with *ctrl + h*, and use the file browser to move the file.  Now open *presets.xml* with Applications > Accessories > gedit Text Editor. It will be in the *.winff* directory in your home folder. Alternatively, if you prefer command-line you can open a Terminal and enter:
```
gedit ~/.winff/presets.xml
```

In gedit replace "kb " with "k " (notice the space). Save and now WinFF should probably work.  There may be some more recent WinFF presets at the WinFF site but I'm not sure.

If you prefer to use the older FFmpeg from the Ubuntu repository instead of updating the WinFF presets see:
[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)

---

### Post by nothingspecial on 2010-06-30
The command line should have worked. You seem to have everything necessary compiled in.

That said, I will leave you now `cause you`ve got the master himself helping.

Cheers.

---

### Post by FakeOutdoorsman on 2010-06-30
> **nothingspecial said:**
> That said, I will leave you now `cause you`ve got the master himself helping.

Thanks, but I'm still learning!

---

### Post by Amy_1990 on 2010-06-30
Thank you all very much

FakeOutdoorsman i used your guide to compile and install ffmpeg thank you for that I don't think i would have got this far without it.Now when i replace the kb with k is that for all of them because i am just trying to turn a you tube into a avi or mpeg but i like the fact that i could turn one into mp3 format that would be a very nice feature.After i did a google search and found that ffmpeg would do all this stuff so the avi,mpeg and mp3 are what i would like to be able to convert.Once again thank you i can see why ubuntu is the #1 linux distribution

---

### Post by FakeOutdoorsman on 2010-06-30
> **Amy_1990 said:**
> ...Now when i replace the kb with k is that for all of them...

Yes, replace all instances of "kb " with "k ", because your version of FFmpeg does not accept any command or preset that uses *kb*.

---

### Post by Amy_1990 on 2010-06-30
Thank you

I am starting right now i will post the results back as soon as i test it out.

---

### Post by Amy_1990 on 2010-06-30
ok changing the kb to k and it worked but i also had to take the v out of 4mv so i did that and it fixed the flv to avi and now when i convert to ipod i get this error.

[libx264 @ 0xa1ba130] broken ffmpeg default settings detected
[libx264 @ 0xa1ba130] use an encoding preset (vpre)

but i don't see me using this as i don't have a ipod.I had one more but it was about the same error and it was on one of the phone video's so i don't think i would use this.

Thanks you

---

