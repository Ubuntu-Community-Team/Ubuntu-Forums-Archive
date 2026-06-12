---
title: "Lost codec support after upgrade to Dapper"
date: 2006-05-29
forum: Desktop Environments
---

### Post by cajunaggie on 2006-05-29
I did a command line upgrade of Dapper earlier this week, because I'm a nut for new toys. Everything went smoothly, no hitches, no indications of problems. However earlier today I fired up Xine to watch some TV episodes I BitTorrented, which are in avi format. Xine told me I was attemtping to use an unsupported codec. I tried using MPlayer thinking there was something wrong with Xine. Mplayer wouldn't even start up.

When using Xine, I can hear the audio track but I get no visual output. MP3 audio files still work fine, near as I can tell, and MPG seems to work okay.

I've tried reinstalling the w32codecs, according to the wiki-guide, with no luck. I also attempted to use Automatix, just to see what would happend, but all it did was reset my sources list to look at Breezy packages. I'm kinda lost at this point. Any tips or advice for me? ](*,)

---

### Post by Sutekh on 2006-05-30
Auotmatix isnt ready for Dapper, so I wouldnt use it to get the neccessary codecs.

Where did the w32 codecs fail?  Can you post the errors?

---

### Post by cajunaggie on 2006-05-30
I'm not entirely sure what you're asking but maybe this helps. When I try running Xine I get an error message: "The stream [then it gives the path to the file] uses an unsupported codec [then it names the codec]. Start playback anyway?"

So far I've gotten this for the XVID, DivX 5 (DX50), and Microsoft MPEG-4 v3 (DIV3) codecs.

What further data is required?

---

### Post by Sutekh on 2006-05-30
You said you installed the w32codecs with no luck.  Did you mean they dont install or they install but dont help?

---

### Post by Sutekh on 2006-05-30
Hang on, I don't think you need w32codecs for .avi only for .wmv etc.

Do you have the universe and multiverse repositories enabled?

Try installing these packages (you might want to copy and paste)
> sudo apt-get update
sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-gl gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse libxine-main1 libxine-extracodecs

---

### Post by cajunaggie on 2006-05-30
[QUOTE=Sutekh]You said you installed the w32codecs with no luck.  Did you mean they dont install or they install but dont help?[/QUOTE]
They've installed, but it's not helping.

---

### Post by cajunaggie on 2006-05-30
[QUOTE=Sutekh]Hang on, I don't think you need w32codecs for .avi only for .wmv etc.

Do you have the universe and multiverse repositories enabled?

Try installing these packages (you might want to copy and paste)[/QUOTE]

Tried with no change. I installed the packages but still nothing. I'm wondering if a fresh install might the way to go.

---

### Post by Sutekh on 2006-05-30
Double check the libxine-extracodecs?  They solved major issues for me.
[quote=cajunaggie]Tried with no change. I installed the packages but still nothing. I'm wondering if a fresh install might the way to go.[/quote]I'd love to say yes, because I'm always cautious and wary of dist-upgrades on systems that have been running a while.  

I don't want to say yes, because I can't be sure this will go away on a fresh install.  What do you think?  

The last thing I can think of is using Totem-xine or mplayer as the [Restricted Formats]("https://wiki.ubuntu.com/RestrictedFormats#head-51da8d49e45bfd7f114894931f0c16faaac6aea5") page reckons they are best support for DivX, XviD or FFmpeg MPEG-4, which is what you need.

```
sudo apt-get install totem-xine xine-ui mplayer 
```

---

### Post by cajunaggie on 2006-05-30
No dice. Looks like I'll have to go with a fresh install. :rolleyes:

---

### Post by Topper_H on 2006-06-03
Same problem here !

I've been testing dapper for months and since a few days totem-xine says it can't open most of my videos (codec is missing). That goes for Xvid, Divx and wmv files. All those files were playing nicely a few days ago !!!

Help !

---

### Post by hettar on 2006-06-03
I've had the same problem. if you run xine-check you will get an error about no input plugins. A bit of investigation has shown the the plugins have been installed to /usr/lib/xine/plugins/1.1.1 but xine is still looking for them in /usr/lib/xine/plugins
 a sudo ln -s *.so ../ fixed the problem for me, but it is a problem with the packages.

---

### Post by dunomous on 2006-06-08
elaborate on what you did again?

---

### Post by makoto149 on 2006-07-08
Now that I have installed libxine-extracodecs I can use Xine to play videos that wouldn't before.  Yeah!

---

