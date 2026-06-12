---
title: "glc - OpenGL &amp; ALSA video capture tool (testers wanted)"
date: 2007-10-23
forum: Gaming &amp; Leisure
---

### Post by nullkey on 2007-10-23
Similar to [yukon](http://www.neopsis.com/projects/yukon/) and [Fraps](http://en.wikipedia.org/wiki/Fraps) **[glc](http://nullkey.ath.cx/~stuff/glc)** is a real-time video capture tool designed to capture OpenGL applications (=games) efficiently. It is a relatively new project and needs testing.

Since I'm unable to provide .debs (gentoo here), I've made a simple [build script](http://nullkey.ath.cx/~stuff/glc/scripts/glc-build.sh) which should do everyting from downloading sources to installing the compiled application (and even bugs about missing dependencies...). If someone is willing to maintain .debs I would gladly put 'em to [the official homepage](http://nullkey.ath.cx/~stuff/glc).

Bug reports and feature requests are welcome!

---

### Post by TidusBlade on 2007-10-23
I wouldn.t mind helping :) Been looking for a video capturer on linux :p Dunno how to make .debs but I can do testing.

---

### Post by nullkey on 2007-10-23
> **TidusBlade said:**
> I wouldn.t mind helping :) Been looking for a video capturer on linux :p Dunno how to make .debs but I can do testing.
Testing it is fairly simple, just
```
wget http://nullkey.ath.cx/~stuff/glc/scripts/glc-build.sh
chmod a+x glc-build.sh
./glc-build.sh
```
If you choose to install it to your home directory, remember to add PATH=... and LD_LIBRARY_PATH=... variables to your .bashrc like the script says and reload it (source ~/.bashrc). There is information how to capture at the homepage (or run "glc-play -h" and "glc-capture -h").

---

### Post by TidusBlade on 2007-10-24
Ill do that when I got time, pretty new to linux aswell so I gotta figure out how to do what you posted :p

---

### Post by BeholdMyGlory on 2008-04-14
Oh. Glad I found this thread. I've been looking for something like this. As for the testing, it worked flawlessly for me. Just wanted to say thanks for the application ^^

---

### Post by cycloptivity on 2008-05-21
Has anyone continued to have problems after going from gutsy to hardy?

Cheers,

Kahn

---

### Post by Vadi on 2008-05-21
No, works on hardy.

Still can't figure out how to encode the .glc file properly though.

---

### Post by nullkey on 2008-05-21
> **Vadi said:**
> No, works on hardy.

Still can't figure out how to encode the .glc file properly though.
[This guide]("http://nullkey.ath.cx/projects/glc/wiki/HowtoEncode") should help with encoding. Just make sure you have mplayer and lame installed.

---

### Post by Ferrat on 2008-08-11
Been trying out glc, looking pretty good, a bit more system loss then yukon but with the working install file and 64 to 32bit fixes I can live with it.

Recording Guild Wars worked like a charm thru wine on my 64bit system :) but a 50-75% drop in FPS might not be so fun on other games that are more FPS dependent or if you don't have a high FPS to start with. 

testing a few settings out to see if I can't fix that, the resize function worked pretty well but loss of quality with the 0.5 reduction was a bit high to use for anything but perhaps youtube vids. 

But over all very nice, hope you keep up the good work, Linux really needs a dependable and stable recording app.

---

### Post by Ferrat on 2008-08-26
Done some tweaking with glc now due to yukon hating pulseaudio and uninstalling it and installing esound mess up my gnome :S 

Capturing is good but more often than not my recordings starts to become jumpy after a minute or so, but Guild Wars is still pumping out more than playable FPS, is there anyway to make glc to be more aggresive in taking the frames it needs? 

Right now when recording I get about ~40-50FPS on GW and recording in 25FPS but GLC after a little while starts to record like 1-5FPS instead of 25 but GW FPS is still the same, I don't ming GW FPS going down to 20-25FPS if that means I capture almost every frame.


EDIT;
the -n switch helped a bit :)

---

### Post by nullkey on 2008-08-26
> **Ferrat said:**
> Capturing is good but more often than not my recordings starts to become jumpy after a minute or so, but Guild Wars is still pumping out more than playable FPS, is there anyway to make glc to be more aggresive in taking the frames it needs?
```

$ glc-capture --lock-fps ...

```

When capture frame rate is dropping dramatically it is usually a hard-disk speed issue. Your HD can't keep up with data rate and glc throttles itself.

---

### Post by Ferrat on 2008-08-26
Yeah found the -n switch, helped and trying to use another hard-drive :)

---

### Post by LaLLi on 2008-11-15
The video capture seems to work great, but I can't get the audio..I'll have to look into it later on. Im running Ubuntu 64bit Ibex.

EDIT: Now that I think about it I don't need audio. I'll just put some Rock'n'Roll in for the audio.

---

### Post by LaLLi on 2008-11-28
Yesterday I recorded a 25min video of World of Warcraft. It is a 640*512 resolution 20fps video = 15GB. I started encoding it with mencoder using "&#8722;ovc lavc &#8722;lavcopts vcodec=mpeg4:vbitrate=800". I came back later to see how it was doing and it had encoded over 15000s of video?!? I cancelled the encoding and checked the video. It was ok to 25min mark but after that the image stopped and the video kept going for 5h.

Am I doing something wrong or is there a problem with glc-play?

---

### Post by crazyfuturamanoob on 2008-11-28
Exactly what I was looking for! 

I want to make gameplay videos about Doom3, Urban Terror, and Dark Reign 2, but gtk-recordmydesktop can't capture sound, because
*malfunctioning jack drivers* = *only one program can use them, which is either the game or gtk-recordmydesktop*

But I have ALSA & PulseAudio working so this should work. I'll try it when I get time.

---

### Post by 569874123 on 2009-02-08
I get 5 fps in urban terror with glc and before that i got 90. 
Any solutions?

---

### Post by Emanuele_Z on 2009-04-02
Hello all,

Yesterday I used **glc** with WoW via wine.
```

glc-rec wine Wow.exe -opengl

```
in 640x480 (default parameters - I use glc-rec that is a script I wrote to use my own compiled).
It works very well, but sometimes (most of all when you start a PvP fight and probably new graphcis/sounds are loaded) it cripples me down a bit (start fight --> cripple, rest of fight --> no issues).

I'm using an Asus G2S (my disk probably is not very fast) with 2 GB of ram and a 8500GT Mobile (512 MB VRam).

What do you suggest to add as options?
Maybe should I decrease captured FPS to 20?

I have an external USB 2.0 disk. Should I write the video file over there?

What software is available to convert movies from **glc** format to others like MPEG4?

What should I use as an alternative to Adobe Premiere to assemble my videos?

**glc** is very good, at least for me and actually the sources are very well written.
Should someone probably add support for MJPEG format (MJPEG actually can be seen as a serie of jpeg images plus audio...that should be a better compression than the current YCbCr + zip schema)?

Thanks in advance,
Regards,

Ps. I had a look at the sources to add the YCbCr color space but I found out everything is already implemented (I missed the command line argument so I went straight after the sources... what a jacka*s I am)!

---

### Post by Vadi on 2009-04-02
There is an encode.sh or something like that script provided that encodes for you. I found it rather hard to use though.

Was tinkering with the idea of making a GUI for glc (capture + convert, and upload) but I don't have enough technical expertise to interface with it.

---

### Post by Emanuele_Z on 2009-04-02
Tested glc with my esternal HD USB...isn't good :(
I'll have to use my internal HD (which isn't very fast because I use a notebook).

Any software like Adobe Premiere?

Cheers,

---

### Post by Emanuele_Z on 2009-04-03
So, any suggestions?

---

### Post by R33D3M33R on 2009-04-03
Just tried it in OpenArena and its great! It captures sound and graphics properly. There is just one problem: the video is too dark. How to fix this? The in-game brightness looks ok.

---

### Post by Vadi on 2009-04-03
Adobe Premiere? No, nothing like that unless you work in Hollywood.

Best thing atm I'd say are Kino and PiTiVi.

---

### Post by Emanuele_Z on 2009-04-03
> **R33D3M33R said:**
> Just tried it in OpenArena and its great! It captures sound and graphics properly. There is just one problem: the video is too dark. How to fix this? The in-game brightness looks ok.

I have the same issue when converting movies...anyone has any idea why?

Cheers,

---

### Post by robertobech on 2009-04-24
Thanks a lot! I've been looking for a way to record gaming videos for months. 

The encode script wasn't working for me, it's probably related to a codec missing or something like that, so I've created a small script that extracts the audio and merge it with the video, like this:

```
#!/bin/bash
AUDIOFILE=$(echo $1 | sed 's/.glc/.mp3/')
RESULTFILE=$(echo $1 | sed 's/.glc/.avi/')

# Extract audio
glc-play $1 -o - -a 1 | lame -hV2 - $AUDIOFILE

# merge audio with .glc video file
glc-play $1 -o - -y 1 | mencoder -demuxer y4m - -audiofile $AUDIOFILE -oac copy -ovc x264 -x264encopts qp=18:pass=1 -of avi -o $RESULTFILE
```

---

### Post by LaLLi on 2009-04-24
For those who have dark video problems you could use robertobechs encoding script and add some gamma with mencoder.

```
# merge audio with .glc video file
glc-play $1 -o - -y 1 | mencoder -demuxer y4m - -audiofile $AUDIOFILE -oac copy -ovc x264 -x264encopts qp=18:pass=1 **-vf eq2=1.5** -of avi -o $RESULTFILE
```

---

### Post by Ron Overdrive on 2009-06-01
Ok I have an interesting problem. When converting the GLC file to an mp4 using the following command line:

```
glc-play [stream file] -o - -y NUM | mencoder -demuxer y4m - -nosound -ovc x264 -x264encopts qp=0:threads=auto -of lavf -o video.mp4

```

I get some strange video corruption that appears in every player except for mplayer. It resembles what a scrambled TV channel looks like.

Here's what it looks like (if you can't tell its Nexuiz 2.5): [http://www.youtube.com/watch?v=bgZV-DVXXPM]("http://www.youtube.com/watch?v=bgZV-DVXXPM")

Any ideas what the issue is?

---

### Post by kihjin on 2009-06-06
This is a FANTASTIC program! It took some effort to get it to do what I wanted, but I'm absolutely ecstatic about it.

If you are having trouble capturing your opengl stream (output is a black screen) with this application, make sure you are running in windowed mode! I was unable to capture full screen ogl. The result was a black screen. Once I went to windowed mode, (--pbo also helped) everything worked great! 

Also note that the raw output files are GIANT. The program generated 2448941096 bytes for maybe a minute of recording (1440x900 @ 30fps).

---

### Post by Psy-Q on 2009-08-12
What are your options for capturing audio? I'm trying on Jaunty, but it seems neither hw:0,0 nor the channel names (e.g. "front") work for capturing in-game audio in WINE.

I know it must be possible, since there is someone who recorded Aquaria in WINE with sound (it's on YouTube).

---

### Post by 569874123 on 2009-08-12
I have no idea on what to put in this part(since i want audio).
> -a, --record-audio=CONFIG ¶

Record specified ALSA devices. CONFIG format is device,rate,channels;device2....


---

### Post by doorknob60 on 2009-08-12
Holy crap great program. Seems to work about as good as Fraps. The problem is my encoding is taking ages with the script I got from a few posts up. It takes a few times longer than the length of the video, actually. Is there a better way to encode it, or a way to just use the glc file directly in a video editor and let it handle the encoding (like fraps, it saves an uncompressed avi and you can just stick it in Movie Maker or whatever).

EDIT: BTW I tried it with CoD2 in Wine and sound also worked with no extra configuration. Also the gameplay got slightly laggy (like Fraps), but still playable, and the video actually has better FPS than the gameplay, which is nice (Fraps does that too sometimes). Aside from the long encoding, this is amazing.

EDIT2: Okay, I think I see how I can just output the raw video/audio and then put it in to an editor. I'll try that once it's done encoding (still going...)

Finally got a good video up, think I got the hang of it (and Kdenlive :P) now finally. [http://www.youtube.com/watch?v=Bt22w1dwbM4](http://www.youtube.com/watch?v=Bt22w1dwbM4)

---

### Post by Aperion on 2009-11-06
Just a heads up, got working pretty easily, except some of the prerequisite uninstantiated the nvidia dev packages.

Also since this is compiling the app why is there a requirement for 32bit libraries?

---

### Post by kvarley on 2010-01-05
For ubuntu! apt-url for your site! This will download the dependencies automatically, use as a url!

> apt://libx11-dev%2Clibxxf86vm-dev%2Clibxxf86vm-dev%2Clibgl1-mesa-dev%2Clibasound2-dev%2Clibpng12-dev%2Ccmake%2Cgcc-multilib%2Cgit-core/

---

### Post by berot3 on 2010-01-19
hey,
alright i tried it with my all-time-favorite ut2004 (unreal tournament 2004)!

1st problem was ofc the fps... i want to play at high resolution, 1680x1050 or above, so is there any way to speed this up? i mean i have a dual-core, so it should work, i guess.
it really does look like the writing to disk causes this. so is there a way to speed the disk up? for example use the ram? i have 4 gig ram and ut2004 itself doesnt use much so can i use "glc-capture -o /tmp/%d" ??? i know 4 gig isnt much for glc ^^ but it should be enough for a few minutes AND be able to play at high fps, am i right? or isnt that possible? 
(maybe its possible to record to ram, and as soon the ram is full, glc automatically cuts the output and moves it to HDD and than continues with recording to ram. so there would be only a short time of fps-droping)

2nd was the sound, i have pulseaudio-enabled openal, so how do i tell glc to record from pulse?

and does yukon work better with fps? and does recordmydesktop even work with opengl at higher fps???

---

### Post by NimbleRabit on 2010-05-23
I'm wondering if anybody around here can help me troubleshoot some sound problems.  I'm trying to capture a game, and the video is working great (flawlessly in fact, really superb), but no matter what I try I can't seem to get the sound to record.

Here's what my output looks like when I try setting the alsa device to hw:2, which is the card I use:

```
[   0.00s       util  info ] version 0.5.8
[   0.06s gl_capture  info ] capturing at 30.000000 fps
[   0.06s gl_capture  info ] reading frames from GL_FRONT
[   0.06s gl_capture  info ] reading data as dword aligned
[   0.06s       util  info ] system information
  threads hint = 2
[   0.06s       util  info ] stream information
  signature    = 0x00434c47
  version      = 0x04
  flags        = 0
  fps          = 30.000000
  pid          = 17282
  name         = /home/nimblerabit/games/HoN/hon-x86_64
  date         = Sun May 23 20:25:44 2010
[   0.06s       main  info ] glc initialized
[  12.01s       main  info ] starting glc
[  12.01s       file  info ] opening /media/streams/hon-x86_64-17282-0.glc for writing stream (no sync)
[  12.02s       pack  info ] compressing using QuickLZ
[  12.02s gl_capture  info ] reading frames in GL_BGRA format
[  12.04s       main  info ] glc running
[  12.04s alsa_capture warning ] device hw:2 already started
[  12.04s  alsa_hook  info ] 0x118ce660: opened device "hw:2" with mode is 0x00 (async=no, nonblock=no)
[  12.06s  alsa_hook  info ] 0x118ce660: initializing stream 2
[  12.06s  alsa_hook  info ] starting capturing
[  12.06s gl_capture  info ] starting capturing
[  12.06s gl_capture  info ] refreshing color correction
[  12.06s       main  info ] started capturing
[  12.07s gl_capture  info ] creating/updating configuration for video 1
[  24.72s alsa_capture  info ] starting device hw:2
[  24.72s  alsa_hook  info ] stopping capturing
[  24.72s gl_capture  info ] stopping capturing
[  24.72s       main  info ] stopped capturing
[  29.14s       main  info ] closing glc

```

I'm guessing the problem might have to do with the line "[  12.04s alsa_capture warning ] device hw:2 already started", but I don't know what to do about it.

I've tried leaving it as default (no -a options), but since that isn't the card I use, it doesn't work.  There are no errors when I do that, but on playback there is no audio.

While I'm here I'll also ask: does anybody know how I might go about using GLC to livestream?  I can do the encoding on another computer, and I have a great connection, so I'd love to give that a try.

---

### Post by Anariaq on 2010-08-06
Hey

I know this is old topic. But I have to ask. Have any one manage to fix the capture with sound. No matter what I do I cant capture with sound. It happened after I upgraded to 10.04. Before that. There where no problems.

Hope there is a solution.

Anariaq

---

### Post by Veenn on 2010-09-05
> **Anariaq said:**
> Hey

I know this is old topic. But I have to ask. Have any one manage to fix the capture with sound. No matter what I do I cant capture with sound. It happened after I upgraded to 10.04. Before that. There where no problems.

Hope there is a solution.

Anariaq

Same problem here! 

I even tried multiple sound cards but to no avail. 

Any help with this would be **greatly** appreciated

---

### Post by J.K.Makowka on 2010-09-06
Same problem... I guess it's pulse audio related. In fact if I install the pulseaudio volume control, where you can usually enable recording applications, glc does not show up in the list of recording programs :(

---

### Post by BOYerchen on 2010-09-07
The sound is bugging me as well.

---

### Post by portets on 2010-09-07
yeah, affects me as well. i first used it in ubuntu 9.10 and it didn't capture sound there either.

---

### Post by alexandrius on 2010-09-07
Ok, i captured audio from Doom3 but it was not synced poorly (nearly 5 secs delay), then tried amnesia didn't capture audio at all :(
This seems really good application but needs to be fixed up :)

---

### Post by LinuxGameCast on 2010-09-21
It works just fine under 10.04 using the -a option + 3.5mm M-M cable with the proper line settings. Tested with Sound Blaster and integrated.

---

### Post by J.K.Makowka on 2010-09-21
Strangely enough it seems to capture some games's audio without problems. I just recorded this for our blog:
[http://www.youtube.com/watch?v=5YLowDQBpq8](http://www.youtube.com/watch?v=5YLowDQBpq8)
And much to my surprise the audio works flawlessly.

---

### Post by LinuxGameCast on 2010-09-21
> **J.K.Makowka said:**
> Strangely enough it seems to capture some games's audio without problems. I just recorded this for our blog:
[http://www.youtube.com/watch?v=5YLowDQBpq8](http://www.youtube.com/watch?v=5YLowDQBpq8)
And much to my surprise the audio works flawlessly.

Found that feeding the speaker audio into the MIC input fixed the sound issues. Recorded a few demos in 720 with no problem. Sometimes glc will not auto generate the glc file but -o takes care of that.

---

### Post by Rypervenche on 2010-10-19
It would be nice if someone could figure out exactly what you need to type after "-a" for it to get the audio working just right. My glc-capture works fine by default, but I would like to record my video game's audio as well as my headset's mic. I have tried many different combinations but to no avail. I have managed to get my mic to work some times with "-a hw:1,44100,1" but I can't seem to find the right combination for what my default audio is, nor can I get it to record two tracks at the same time, which the website says it can do.

Any help here? I may open a new thread for this if no one answers...

---

### Post by Anariaq on 2010-10-19
Hey just want to report my findings so far. Glc dos not record sound with Nexuiz-sdl but it dos record sound with Nexuiz-glx. Think it has to do with pulseaudio? Though when using glc-play the sound is out of sync. When I then encode it with mp3 format. It still will be out of sync. My findings so far is that when encoding with wav instead of mp3 it will sync up with the video. Even though glc-play is out of sync.
Hopefully this is an understandable babble.

Got another question.
I encode with
```
glc-play [stream file] -y 1 -o - | mencoder -demuxer y4m - -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=6000 -audiofile audio.wav -oac mp3lame -o video.avi
``` Its really dark anyway to make it brighter with this encode? Did see that I could use robertobechs encoding script. But I'm a very impatient guy :rolleyes:

Anariaq

---

### Post by LaLLi on 2010-10-22
> Got another question.
I encode with
```
glc-play [stream file] -y 1 -o - | mencoder -demuxer y4m - -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=6000 -audiofile audio.wav -oac mp3lame -o video.avi
``` Its really dark anyway to make it brighter with this encode? Did see that I could use robertobechs encoding script. But I'm a very impatient guy :rolleyes:

Anariaq
You could have just read the entire 5 pages of this thread..
[http://ubuntuforums.org/showpost.php?p=7136514&postcount=25](http://ubuntuforums.org/showpost.php?p=7136514&postcount=25)

---

### Post by Anariaq on 2010-10-25
> **LaLLi said:**
> You could have just read the entire 5 pages of this thread..
[http://ubuntuforums.org/showpost.php?p=7136514&postcount=25](http://ubuntuforums.org/showpost.php?p=7136514&postcount=25)

Thanks! have read the entire 5 page. I just did not know with part of the code I needed to use.

Anariaq

---

### Post by Rypervenche on 2010-10-31
> **NimbleRabit said:**
> I'm wondering if anybody around here can help me troubleshoot some sound problems.  I'm trying to capture a game, and the video is working great (flawlessly in fact, really superb), but no matter what I try I can't seem to get the sound to record.

Here's what my output looks like when I try setting the alsa device to hw:2, which is the card I use:

```
[   0.00s       util  info ] version 0.5.8
[   0.06s gl_capture  info ] capturing at 30.000000 fps
[   0.06s gl_capture  info ] reading frames from GL_FRONT
[   0.06s gl_capture  info ] reading data as dword aligned
[   0.06s       util  info ] system information
  threads hint = 2
[   0.06s       util  info ] stream information
  signature    = 0x00434c47
  version      = 0x04
  flags        = 0
  fps          = 30.000000
  pid          = 17282
  name         = /home/nimblerabit/games/HoN/hon-x86_64
  date         = Sun May 23 20:25:44 2010
[   0.06s       main  info ] glc initialized
[  12.01s       main  info ] starting glc
[  12.01s       file  info ] opening /media/streams/hon-x86_64-17282-0.glc for writing stream (no sync)
[  12.02s       pack  info ] compressing using QuickLZ
[  12.02s gl_capture  info ] reading frames in GL_BGRA format
[  12.04s       main  info ] glc running
[  12.04s alsa_capture warning ] device hw:2 already started
[  12.04s  alsa_hook  info ] 0x118ce660: opened device "hw:2" with mode is 0x00 (async=no, nonblock=no)
[  12.06s  alsa_hook  info ] 0x118ce660: initializing stream 2
[  12.06s  alsa_hook  info ] starting capturing
[  12.06s gl_capture  info ] starting capturing
[  12.06s gl_capture  info ] refreshing color correction
[  12.06s       main  info ] started capturing
[  12.07s gl_capture  info ] creating/updating configuration for video 1
[  24.72s alsa_capture  info ] starting device hw:2
[  24.72s  alsa_hook  info ] stopping capturing
[  24.72s gl_capture  info ] stopping capturing
[  24.72s       main  info ] stopped capturing
[  29.14s       main  info ] closing glc

```

I'm guessing the problem might have to do with the line "[  12.04s alsa_capture warning ] device hw:2 already started", but I don't know what to do about it.

I've tried leaving it as default (no -a options), but since that isn't the card I use, it doesn't work.  There are no errors when I do that, but on playback there is no audio.

While I'm here I'll also ask: does anybody know how I might go about using GLC to livestream?  I can do the encoding on another computer, and I have a great connection, so I'd love to give that a try.

Good news! you already figured it out. The audio is recording just fine. Use "glc-play -a" then use 1, 2, or 3. When I set my USB headset as hw:2, my in-game sound is -a 1 and my headset is -a 3 (-a 2 is nothing for me)

I haven't gotten the pause feature to work with it yet, but that's a minor problem.

---

### Post by Wilbefast on 2010-11-07
Hi there, been trying to use glc to get some good quality footage of [my game]("http://wilbefast.com/showcase/bugger/"):

```
william@SATAN:~$ cd Desktop/
william@SATAN:~$ glc-capture ./Bugger
```I'm having similar problems to many other people: no sound is being captured: 

```
william@SATAN:~/Desktop$ glc-play ./Bugger-8339-0.glc -i 1
[   0.00s] video stream 1
[ 188.59s] end of stream
video stream 1
  frames      = 5312
  fps         = 28.17
  bytes       = 7.60 GiB
  bps         = 41.26 MiB
```In other words, there just isn't an audio stream present in the output file. Any idea how I can get this to work?

edit: oh, I forgot  - system is Ubuntu 10.04 64 bit ;-)

cheers,

William

---

### Post by Rypervenche on 2010-11-07
> **Wilbefast said:**
> In other words, there just isn't an audio stream present in the output file. Any idea how I can get this to work?

Did you try 
```
glc-play filename -a 1 -o test1.wav
glc-play filename -a 2 -o test2.wav
glc-play filename -a 3 -o test3.wav
```

Try all 3 of these and see if you get any wav files that work. Also make sure you're watching the terminal when you hit <Shift>F8 to see if the audio is capturing or if you are getting error messages.

The program is far from complete, so it does have bugs and problems in it that will not get fixed. We really need a new program or someone to take over its programming.

---

### Post by Wilbefast on 2010-11-07
> **Rypervenche said:**
> Did you try 
```
glc-play filename -a 1 -o test1.wav
glc-play filename -a 2 -o test2.wav
glc-play filename -a 3 -o test3.wav
```Try all 3 of these and see if you get any wav files that work. Also make sure you're watching the terminal when you hit <Shift>F8 to see if the audio is capturing or if you are getting error messages.

Actually I did this first while trying to encode the video, and only later realised that the resulting file had no audio because no wav file was being created, and that no wav file was being created simply because the glc had no audio channel (neither 1,2 or 3). If there was audio then I'd be getting something like this:

```
glc-play filename.glc -i 1
[   0.00s] video stream 1
[   0.00s] audio stream 1
[  54.87s] end of stream
video stream 1
  frames      = 2469
  fps         = 45.00
  bytes       = 1.13 GiB
  bps         = 21.09 MiB
audio stream 1
  packets     = 2570
  pps         = 46.84
  bytes       = 9.22 MiB
  bps         = 171.98 KiB
```rather than this:

```
william@SATAN:~/Desktop$ glc-play Bugger-2976-0.glc -i 1
[   0.00s] video stream 1
[   4.47s] end of stream
video stream 1
  frames      = 123
  fps         = 27.51
  bytes       = 180.18 MiB
  bps         = 40.29 MiB
```I ran in (very) verbose mode to see what was going on:

```
glc-capture -v 6 ./Bugger
```and the following came out:
```
[   0.00s       util  info ] version 0.5.8
[   0.00s       util   dbg ] Nov  7 2010 14:49:18, 4.4.3
[   0.08s     opengl   dbg ] initializing
[   0.08s gl_capture  info ] capturing at 30.000000 fps
[   0.08s gl_capture  info ] reading frames from GL_FRONT
[   0.08s gl_capture  info ] reading data as dword aligned
[   0.08s       alsa   dbg ] initializing
[   0.08s       util  info ] system information
  threads hint = 2
[   0.08s       util  info ] stream information
  signature    = 0x00434c47
  version      = 0x04
  flags        = 0
  fps          = 30.000000
  pid          = 2976
  name         = /home/william/Desktop/Bugger
  date         = Sun Nov  7 20:43:53 2010
[   0.08s       main  info ] glc initialized
[   0.08s       main   dbg ] LD_PRELOAD=libglc-hook.so
[   3.24s       main  info ] starting glc
[   3.24s       file  info ] opening /home/william/Desktop/Bugger-2976-0.glc for writing stream (no sync)
[   3.25s       pack  info ] compressing using QuickLZ
[   3.25s gl_capture  info ] reading frames in GL_BGRA format
[   3.28s       main  info ] glc running
[   3.28s  alsa_hook  info ] starting capturing
[   3.28s gl_capture  info ] starting capturing
[   3.28s gl_capture  info ] refreshing color correction
[   3.28s      state   dbg ] applying 3202600 usec time difference
[   3.28s       main  info ] started capturing
[   3.28s gl_capture   dbg ] calculated capture area for video 1 is 1280x800+0+0
[   3.28s gl_capture  info ] creating/updating configuration for video 1
[   3.28s gl_capture   dbg ] video 1: 1280x800 (1280x800), 0x01 flags
[   7.69s  alsa_hook  info ] stopping capturing
[   7.69s gl_capture  info ] stopping capturing
[   7.69s       main  info ] stopped capturing
[   8.25s       main  info ] closing glc
[   8.25s       alsa   dbg ] closing
[   8.25s     opengl   dbg ] closing
```

There don't seem to be any errors, but again there's just no audio stream in the resulting file :confused:

Video quality is very impressive though, compared to FFMPEG which had all these wierd vertical bars...

William

---

### Post by Rypervenche on 2010-11-07
> **Wilbefast said:**
> There don't seem to be any errors, but again there's just no audio stream in the resulting file :confused:

Did you try typing those 3 lines or did you assume they wouldn't work? Try doing them. It shows that your alsa_hook is capturing, so it should be working. You seem to be using "-i 1" which I think is your problem. Try what I wrote and if it works, we can go from there. If it doesn't then we'll....go from there.

---

### Post by hakermania on 2010-11-07
I think it would be better to inform you about all the missing dependencies when running the script!

---

### Post by Wilbefast on 2010-11-08
> **Rypervenche said:**
> Did you try typing those 3 lines or did you assume they wouldn't work? Try doing them. It shows that your alsa_hook is capturing, so it should be working. You seem to be using "-i 1" which I think is your problem. Try what I wrote and if it works, we can go from there. If it doesn't then we'll....go from there.
Don't you trust me? :(

I did run the code (-a 2 and -a 3 that is, I'd already tried -a 1), and unless it's creating the WAV in a different directory from the working one then it doesn't seem to do anything. The fact that no audio streams are listed and no sound plays when I stream the glc seems to suggest that there's nothing there to read, but extracting audio in verbose mode (glc-play -a 1 -v 6 ... etc) doesn't show any errors.

I should really try this with a different applications... will do so tonight when I'm back at home.

edit: yeah, same problems across the board - Aquaria for instance, which was used to show off GLC, doesn't have any sound when I play back the capture.

In case it helps, rig is a Dell Vostro 1510.

Thanks for looking into this,


William

---

### Post by mocha on 2010-11-10
Can anyone help with setting up Pulseaudio to route audio from the application to the glc capture?  I tried to setup my .asoundrc file and specify pulse as the default type, then I tried to use "-a default, 44100, 2" but it just crashes.  The only thing that doesn't crash glc is to use an actual Alsa device name such as hw:0.

Pulseaudio has the ability to load null sinks and loopback devices, and then route audio around as needed.  Something like this:

```
pactl load-module module-null-sink sink_name=somesink
pactl load-module module-loopback source=alsa_output.xxxxxxx sink=somesink
pactl load-module module-loopback source=alsa_input.xxxxxx sink=somesink
```

I tried a few things but I'm not getting it right.  Maybe someone else can help figure it out.

---

### Post by Wilbefast on 2010-11-12
Bump!

Maybe I can do the same thing as Mocha - somebody help Mocha solve his/her problem :P

---

### Post by Rypervenche on 2010-11-12
> **mocha said:**
> Can anyone help with setting up Pulseaudio to route audio from the application to the glc capture?  I tried to setup my .asoundrc file and specify pulse as the default type, then I tried to use "-a default, 44100, 2" but it just crashes.  The only thing that doesn't crash glc is to use an actual Alsa device name such as hw:0.

Pulseaudio has the ability to load null sinks and loopback devices, and then route audio around as needed.  Something like this:

```
pactl load-module module-null-sink sink_name=somesink
pactl load-module module-loopback source=alsa_output.xxxxxxx sink=somesink
pactl load-module module-loopback source=alsa_input.xxxxxx sink=somesink
```

I tried a few things but I'm not getting it right.  Maybe someone else can help figure it out.

Because the application was never finished and there are bugs, you may never get it to work. However, I found that I too was unable to use "default" and I had to use the actual hw:0 or hw:2 to get it to work. Also, the audio tracks are often messed up, so you may have to try this to get the audio track from it...
```
glc-play file.glc -a 1 -o audio1.wav
glc-play file.glc -a 2 -o audio2.wav
glc-play file.glc -a 3 -o audio3.wav
```
and maybe even a 4th one. Try it out and see if you have any luck.

I hope this helps.

---

### Post by Tobzi on 2010-11-20
Hi

I have installed ecerything and recording works but i get 

```
MEncoder 1.0rc4-4.4.5 (C) 2000-2010 MPlayer Team
Reading from stdin...
success: format: 0  data: 0x0 - 0x0
============ Sorry, this file format is not recognized/supported =============
=== If this file is an AVI, ASF or MPEG stream, please contact the author! ===
Cannot open demuxer.

Exiting...

```when i do

```
glc-play savage2.bin-3494-0.glc -o - -y NUM | mencoder -demuxer y4m - -nosound -ovc x264 -x264encopts qp=0:threads=auto -of lavf -o video.mp4
```
also when i do:

/glc-play avage2.bin-3494-0.glc

nothing happens.

I have Ubuntu 10.10

best regards Tobzi

---

### Post by kyle6513 on 2010-12-22
> **Tobzi said:**
> Hi

I have installed ecerything and recording works but i get 

```
MEncoder 1.0rc4-4.4.5 (C) 2000-2010 MPlayer Team
Reading from stdin...
success: format: 0  data: 0x0 - 0x0
============ Sorry, this file format is not recognized/supported =============
=== If this file is an AVI, ASF or MPEG stream, please contact the author! ===
Cannot open demuxer.

Exiting...

```when i do

```
glc-play savage2.bin-3494-0.glc -o - -y NUM | mencoder -demuxer y4m - -nosound -ovc x264 -x264encopts qp=0:threads=auto -of lavf -o video.mp4
```also when i do:

/glc-play avage2.bin-3494-0.glc

nothing happens.

I have Ubuntu 10.10

best regards Tobzi


Sorry for bumping this but it is an issue I'm having right now. Anyone?

---

### Post by NCLI on 2011-01-26
Is this project dead?

---

### Post by Sealbhach on 2011-02-08
glc still works for me in Ubuntu 10.10. Not sure if it's still being supported though.

.

---

### Post by ubudog on 2011-07-27
Works great in 10.10, I love it!

---

### Post by chrispepper1989 on 2011-08-01
can anyone who still has the binaries /source for this provide it? I cant get it anywhere! and i really need something to record openGL applications!

Thank you, Chris

---

### Post by ubudog on 2011-08-01
> **chrispepper1989 said:**
> can anyone who still has the binaries /source for this provide it? I cant get it anywhere! and i really need something to record openGL applications!

Thank you, Chris

Have you tried installing it from the repositories?

```
sudo apt-get install glc
```

---

### Post by chrispepper1989 on 2011-08-02
Hi Ubudog, 

Im very sorry i have a naughty confession to make, i posted without taking note of which specific forum i was on, im actually running fedora 14 on the machine im trying to get glc on, so i do apologise for my faux pas. I suppose i could try and get it through 

sudo apt-get install glc 
on my ubunto machine and possibly bring it across??

-Thanks, Chris

---

### Post by doorknob60 on 2011-08-02
By the way, this project was moved to github a while back since the old site is down: [https://github.com/nullkey/glc/wiki](https://github.com/nullkey/glc/wiki) It seems to be fairly inactive, but not completely dead (still a little activity)

---

### Post by ubudog on 2011-08-02
> **chrispepper1989 said:**
> Hi Ubudog, 

Im very sorry i have a naughty confession to make, i posted without taking note of which specific forum i was on, im actually running fedora 14 on the machine im trying to get glc on, so i do apologise for my faux pas. I suppose i could try and get it through 

sudo apt-get install glc 
on my ubunto machine and possibly bring it across??

-Thanks, Chris

Oh, I do that sometimes.  :rolleyes:

Anyway, you can probably get it on Fedora using this command:
```
su -l; yum update; yum install glc
```

---

### Post by Wilbefast on 2011-08-03
I installed it on my previous Ubuntu installation, but I couldn't seem to get FFMPEG to encode anything. Something about missing encoders - tried [recompiling FFMPEG]("http://ubuntuforums.org/showthread.php?t=786095"), it didn't work and effectively stopped me from using GLC anymore :(

I'd be interested in any news - when it worked it was simply fantastic :)

---

### Post by piratec on 2011-10-31
Works great on my 11.10 64 bits. I'm using the GIT script to install it from [https://github.com/nullkey/glc/wiki/Install](https://github.com/nullkey/glc/wiki/Install)

;)

---

### Post by ubudog on 2011-10-31
> **ubudog said:**
> Oh, I do that sometimes.  :rolleyes:

Anyway, you can probably get it on Fedora using this command:
```
su -l; yum update; yum install glc
```

Actually better command (I believe, it's been a while since working with Fedora/Red Hat) would be: 
```

su -c 'yum update; yum install glc'

```

---

### Post by User3264 on 2011-12-16
You can tell openAL to use alsa by default by adding
```
drivers = alsa
```
to ~/.alsoftrc.

---

### Post by mocha on 2011-12-29
> **User3264 said:**
> You can tell openAL to use alsa by default by adding
```
drivers = alsa
```
to ~/.alsoftrc.

I'm still not getting audio recorded.  Below is an example command line I'm using along with your suggestion to the .alsoftrc file.

```
glc-capture -f 60 -a hw:0,44100,2 -z quicklz -v 3 -l log -o output.glc xxxxxx
```

"xxxxx" is the OpenGL application I'm trying to get video and audio to record from.  The glc log says:

```
[   3.58s alsa_capture warning ] device hw:0 already started
[   3.58s  alsa_hook  info ] 0xadf0e530: opened device "hw:0" with mode is 0x00 (async=no, nonblock=no)
[   3.58s  alsa_hook  info ] 0xadf0e530: initializing stream 2
[   3.58s  alsa_hook  info ] starting capturing
[   3.58s gl_capture  info ] starting capturing
[   3.58s gl_capture  info ] refreshing color correction
[   3.58s       main  info ] started capturing
[   3.58s gl_capture  info ] creating/updating configuration for video 1
[   9.12s       main  info ] closing glc
[   9.12s  alsa_hook  info ] stopping capturing
[   9.12s gl_capture  info ] stopping capturing
[   9.13s        log  info ] log closed
```

I assume the message about the alsa device already being started has something to do with the audio not being captured, but I'm not sure how to proceed.  Any suggestions would be appreciated.

---

### Post by leal1 on 2012-11-07
Any clue what would do this to the video: [http://youtu.be/nHQ8K7Ta5II?t=17m48s](http://youtu.be/nHQ8K7Ta5II?t=17m48s)

Bug in glc? Minecraft and glc run's from sparate hard drives.

Specs:
AMD Athlon(tm) 7750 Dual-Core Processor
AMD Radeon HD 4770
4Gt RAM
Ubuntu 12.04

---

