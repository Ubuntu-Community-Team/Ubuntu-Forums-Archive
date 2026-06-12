---
title: "Videos Play but without video, need help"
date: 2005-12-14
forum: General Help
---

### Post by Mike Eckman on 2005-12-14
I am relatively new to Linux, but not new to computers.  I installed Ubuntu 5.1 AMD64 (I realize there is an AMD64 forum, but I dont know if my problem relates to that).

I can play MP3s and audio files with no problem, and like I said, I can hear the audio from the videos I play.  I am almost positive I downlaoded the W32 codecs everyone is talking about, along with all the MPEG codecs that you should use for MPLAYER, Totem, Xine, and Kaffeine.

I cant get any of them to work.

Xine, and Kaffeine will load up the file and play the audio, but I'll just have a black video screen with no errors.

MPLAYER is the only one that gives me an error and it is the "MPlayer interrupted by signal 11 in modile: decode_video".  Then I get a bunch of other stuff telling me about bad usage of CPU/FPU/RAM.  I can post the whole message if someone thinks it will help.  

I searched the forum and the only posts that I found that were similar to mine in MPLAYER all were in the audio decoding of DVDs.  These are just regular MPEG1 and MPEG2 videos from the net.

I've tried Totem also, but it wont even load.  It comes up and immediately closes, with no errors.  It even does it this if I load the program directly without trying to launch something.

Like I said, I am using the AMD64 build, so that might have something to do with it, I just dont know.

If anyone has any suggestions, I'd like to hear them.  And I am looking forward to being here and conversing with you all as this seems to be a great place for info!

-Mike

---

### Post by RAOF on 2005-12-14
I remember helping someone with a similar problem, and it turned out that it was the graphics driver (becuase video programs use a specific X feature to display video smoothly).  Shall we start there?  What graphics card do you have?

Edit: "Help" is perhaps the wrong word ;)  But here's [the thread]("http://www.ubuntuforums.org/showthread.php?t=82154"), anyway.

---

### Post by Mike Eckman on 2005-12-14
I have a Nvidia GeForce 6600 GT 128MB PCIexpress.

I never had to load any drivers under Ubuntu when it installed, so I have no idea if its the most recent ones.  Under windows, I have the 81.85 (I think) drivers and never had a problem playing videos.

---

### Post by RAOF on 2005-12-14
In that case might I suggest running the following from a terminal:
```
sudo apt-get install nvidia-glx nvidia-settings
sudo nvidia-glx-config enable
```
And then pressing Ctrl-Alt-Backspace.  Warning!  Ctrl-Alt-Backspace will stop the X server and log you out, without saving all your work.  Save everything first! :)

Once you've done that, try playing videos again.

---

### Post by Zonkle on 2005-12-14
I installed W32codec (I can see it installed in Synp), but when I try to run MP3 using Totem it says some error that it can't play. Also tried to open Divx,WMA,RM, and they didn't work.

Also downloaded Realplayer 10 .. but it says error when trying to deploy the .deb that I don't have libstdc++ :? .... and that I don't C compiler, but I do have the gcc 3.4.

Also I tried to install the libdvdcss, and when I was trying to do "make install" it says command "make" not found or unknown ,, I forgot :?

---

### Post by Perfect Storm on 2005-12-14
Make sure you have these:

```

sudo apt-get install gstreamer0.8-plugins
sudo apt-get install gstreamer0.8-lame
sudo apt-get install gstreamer0.8-ffmpeg
sudo apt-get install w32codecs
sudo apt-get install avifile-divx-plugin
sudo apt-get install lame
sudo apt-get install sox
sudo apt-get install ffmpeg
sudo apt-get install mjpegtools
sudo apt-get install vorbis-tools

```

For playback DVD:

```

sudo apt-get install libdvdcss2

```

NOTE: Some of the files needs that you have enable specific repo paths in your repository or getting them some where else (due to license issue).
Another Note: Get Mplayer or VLC as movieplayer they are much better.

For Realplayer issue:
```

sudo apt-get install build-essential
sudo apt-get install libstdc++5

```

---

### Post by Perfect Storm on 2005-12-14
To get **libdvdcss2** (same goes for  w32codecs) you to put this in the repo:

```

 sudo gedit  /etc/apt/sources.list

```


## Penguin Liberation Front 
deb [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free
deb-src [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free

---

### Post by Zonkle on 2005-12-14
Thanks AI,

But the problem is that I don't have broadband :? ... so these will take years to be downloaded from my home, but I have ADSL access some where else where I can download the packages from

So how can I download these seperately and install them?

Thanks ;)

---

### Post by Perfect Storm on 2005-12-14
Can you go get broadband for you linux OS NOW! :D 

save these
[ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/pool/non-free/w32codecs/w32codecs_20050412-1plf4_i386.deb](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/pool/non-free/w32codecs/w32codecs_20050412-1plf4_i386.deb)
[http://download.videolan.org/pub/videolan/debian/pool/libdvdcss/1.2.8/libdvdcss2_1.2.8-1_i386.deb](http://download.videolan.org/pub/videolan/debian/pool/libdvdcss/1.2.8/libdvdcss2_1.2.8-1_i386.deb)

save them and burn, when you want to install them, save them on your hard-drive and

```

sudo dpkg -i /where/the/package/is/XXXXXXXXXXXX.deb

```
where XXXXX is the name of the package.

---

### Post by Zonkle on 2005-12-14
[QUOTE=Artificial Intelligence]Can you go get broadband for you linux OS NOW! :D [/QUOTE]

Hopefully next month :( ... 256Kbps ADSL(With proxy filtering all services) here costs $75 a month ;)

Thanks for the links. So after deploying the Multimedia will works ? Mp3,Divx,RM,WMV,Wma,DVD ....etc ?

---

### Post by Perfect Storm on 2005-12-14
It should. But drop Totem and get VLC instead for playing DVDs and movie-files. It's a lot better IMHO.

---

### Post by Mike Eckman on 2005-12-14
[QUOTE=RAOF]In that case might I suggest running the following from a terminal:
```
sudo apt-get install nvidia-glx nvidia-settings
sudo nvidia-glx-config enable
```
And then pressing Ctrl-Alt-Backspace.  Warning!  Ctrl-Alt-Backspace will stop the X server and log you out, without saving all your work.  Save everything first! :)

Once you've done that, try playing videos again.[/QUOTE]

No luck, same thing.  When I pasted that into my terminal, it said I already had the latest version of both of those apps.

Any other suggestions.  I am fairly certain it is not a codec issue as I cannot play ANY video file of any format.  You'd think if I just had a missing codec, others would play okay.

Is it possible that I need something newer than the v77 Nvidia drivers or that because I am using the AMD64 build, its not working?

---

### Post by RAOF on 2005-12-14
Just a final check: running 
```
glxinfo | grep -i nvidia
```
returns something like:
```
server glx vendor string: NVIDIA Corporation
client glx vendor string: NVIDIA Corporation
OpenGL vendor string: NVIDIA Corporation
OpenGL version string: 2.0.0 NVIDIA 76.67
```
yes?  That just confirms that your graphics drivers are working.

If your graphics drivers are working, then we need to look elsewhere.  Can we try totem-xine?  That's what I use for my DVD playing needs, & I'm on AMD64, too.  Just apt-get install totem-xine, and try totem again.  If you aren't already using totem-xine, of course.

---

### Post by Mike Eckman on 2005-12-14
[QUOTE=RAOF]Just a final check: running 
```
glxinfo | grep -i nvidia
```
returns something like:
```
server glx vendor string: NVIDIA Corporation
client glx vendor string: NVIDIA Corporation
OpenGL vendor string: NVIDIA Corporation
OpenGL version string: 2.0.0 NVIDIA 76.67
```
yes?  That just confirms that your graphics drivers are working.

If your graphics drivers are working, then we need to look elsewhere.  Can we try totem-xine?  That's what I use for my DVD playing needs, & I'm on AMD64, too.  Just apt-get install totem-xine, and try totem again.  If you aren't already using totem-xine, of course.[/QUOTE]

I think you are onto something.  When I did that, this is what I got:

```
mike@linux64:~$ glxinfo | grep -i nvidia
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

```

---

### Post by RAOF on 2005-12-14
Have you actually run "sudo nvidia-glx-config enable"?  Although you've got the drivers installed, you need to run this command to tell X to actually **use** those drivers :)

---

### Post by Mike Eckman on 2005-12-14
[QUOTE=RAOF]Have you actually run "sudo nvidia-glx-config enable"?  Although you've got the drivers installed, you need to run this command to tell X to actually **use** those drivers :)[/QUOTE]

Aaah, I got it.  Yes, I did type that command like you said, but I didnt pay attention to what the terminal was telling me.  I dont have it in front of me anymore, but it was saying something to the effect that my X Server had changed and that I needed to type in some command to accept the changes before I could continue.

I dont pretend to completely understand all of this yet, but when I when I typed in your command, the error message contained the command I needed to type.  When I did that, and then redid your command, and restarted X Server, it worked!

Thanks a million for your help.  This completes all my necessary requires for making my WIndows to Linux transition complete! :D

---

