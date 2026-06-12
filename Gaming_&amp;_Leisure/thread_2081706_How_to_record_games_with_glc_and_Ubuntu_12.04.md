---
title: "How to record games with glc and Ubuntu 12.04"
date: 2012-11-07
forum: Gaming &amp; Leisure
---

### Post by leal1 on 2012-11-07
**1. Install glc** 

[https://github.com/nullkey/glc/wiki/Install](https://github.com/nullkey/glc/wiki/Install)

And mencoder for encoding the video.

```
sudo apt-get install mencoder
```**2. Start recording **

```
glc-capture [COLOR=DarkGreen]-n [COLOR=RoyalBlue]--disable-audio[/COLOR][/COLOR] [COLOR=Navy]java -jar minecraft.jar[/COLOR]
```[COLOR=Navy]java -jar minecraft.jar[COLOR=Black] = Game
[/COLOR][/COLOR]
[COLOR=DarkGreen]-n [COLOR=Black]= Optional. Lock game[/COLOR][/COLOR]'s fps to video's fps (default 30). Makes video quality better for me.

[COLOR=DarkGreen][COLOR=DarkOrange][COLOR=RoyalBlue]--disable-audio[/COLOR] [COLOR=Black]= Optional. Disables glc's audio recording. It's maeby better to use this if you don't use glc's sound recording.[/COLOR][/COLOR][/COLOR]

Start/Stop video recording **Sift+F8 **

**3. Encode video**

```
glc-play **input_filename.glc** -o - -y 1 | mencoder -demuxer y4m - -nosound -ovc x264 -x264encopts qp=18:pass=1 -of avi -o **output_filename.avi**
```[B]Audio recording

[/B]glc's audio recording don't work for me, so I use **Audacity** and **Gnome sound recorder**. With **pavucontrol** you can choose which program record game sounds and microphone.


**Additional info and tips:**

[https://github.com/nullkey/glc/wiki](https://github.com/nullkey/glc/wiki)

[http://ubuntuforums.org/showthread.php?t=587935](http://ubuntuforums.org/showthread.php?t=587935) 

[http://www.dedoimedo.com/computers/glc.html](http://www.dedoimedo.com/computers/glc.html)

---

### Post by holastickboy on 2012-11-07
Excellent tutorial.  GLC can be a little daunting, and I find that I have all sorts of issues with it, particularly if my recording is long.  I found this "cast.sh" file on a YouTube tutorial some time back, and it's what I use to record my gaming now.  It uses FFMPEG, and records the game as well as the audio automatically, and the video size is not too large (though quality is good).

Essentially you open a terminal and type "sh cast.sh" to run it, and then you open the game you want to record.  It runs in the background, and when you want to stop the recording, you do a "Ctrl-c" in the terminal window to stop it.  It places the file in your HOME/capture folder (you actually have to make the capture folder first or it gives you an error).

You can download this file from my website at [http://popularpariah.com/cast.sh](http://popularpariah.com/cast.sh)

Or make your own file and use the code below and make it executable afterwards (open a terminal and type "chmod +x cast.sh"). I did not create this code, but I left the authors name in the comments.

Here is the contents of the file if you wish to create it yourself:

```

#ffmpeg script
#--------------------------------------------------------------------------------------
#sample:ffmpeg -f alsa -ac 2 -i hw:0,1 -f x11grab -r 30 -s 1280x1024 -i :0.0 -acodec pcm_s16le -vcodec libx264 -vpre lossless_ultrafast -threads 0 output.avi
#sample2:avconv -f alsa -i pulse -f x11grab -r 25 -s 1920x1080 -i :0.0 -vcodec mpeg4 -b 12000k -g 300 -bf 2 -acodec libmp3lame -ab 256k Screencast.avi
#----------------------------------------------------------------------------------------
#script by Xpander
#----------------------------------------------------------------------------------------
#date function
DATE=`which date`

#How many threads used (0 for automatic)
THREADS=0
#Resolution
RESO=1920x1080
#Audio Device
AUDIO=alsa
#Channels
CHANNELS=2
#SoundCard
SOUNDCARD=pulse
#Frames per second
FPS=25
#Directory where your video is gonna be saved.(include / at the end)
DIRECTORY=$HOME/capture/
#File name
FILENAME=videocast`$DATE +%d%m%Y_%H.%M.%S`.avi

#script
avconv -f $AUDIO -ac $CHANNELS -i $SOUNDCARD -f x11grab -r $FPS -s $RESO -i :0.0 -vcodec mpeg4 -b 10000k -g 300 -bf 2 -acodec libmp3lame -ab 128k -threads $THREADS $DIRECTORY$FILENAME
```

If you find that it gives an mp3 error, you may need to apt-get the ffmpeg with MP3 support.  This file has been excellent, and I recently recorded a 2hr+ psychonauts session with no slowdown or hiccups!

---

### Post by dannyboy79 on 2012-11-07
i've used that script before. Note, change the RESO to match whatever screen resolutions you're playing the game in.

---

