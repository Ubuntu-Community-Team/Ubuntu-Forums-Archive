---
title: "Can't play an h264 *.mkv file well."
date: 2006-04-13
forum: Desktop Environments
---

### Post by YourSurrogateGod on 2006-04-13
I have all of the codecs installed. When I do play it, the only thing that happens is that I can hear the audio, but no video. My player is xine, but I don't think that matters since I've tried it with totem as well. Anyone have a similar problem with the same file type?

---

### Post by macbuff on 2006-04-13
Have you tried VLC ([http://www.videolan.org/)](http://www.videolan.org/)), it works for me with Apple videos with h264 video and aac audio.

J

---

### Post by YourSurrogateGod on 2006-04-13
[QUOTE=macbuff]Have you tried VLC ([http://www.videolan.org/)](http://www.videolan.org/)), it works for me with Apple videos with h264 video and aac audio.

J[/QUOTE]
I just installed that. I tried to open the .mkv file and play it, but that didn't work, absolutely nothing happened. Do I need to tweak some settings?

---

### Post by apjone on 2006-04-13
[QUOTE=YourSurrogateGod]I just installed that. I tried to open the .mkv file and play it, but that didn't work, absolutely nothing happened. Do I need to tweak some settings?[/QUOTE]


try mplayer !!

---

### Post by YourSurrogateGod on 2006-04-13
[QUOTE=apjone]try mplayer !![/QUOTE]
I just did. There's video (but only a small shot of it) and no sound.

---

### Post by apjone on 2006-04-13
check mplayers preferances as you may need to adjust plaugins

---

### Post by YourSurrogateGod on 2006-04-13
[QUOTE=apjone]check mplayers preferances as you may need to adjust plaugins[/QUOTE]
Which ones specifically?

---

### Post by YourSurrogateGod on 2006-04-18
I'm stumped... anyone with an idea of what might be wrong?

---

### Post by psychicdragon on 2006-04-18
Check out [bored2k's guide]("http://ubuntuforums.org/showthread.php?t=85190&highlight=mplayer") to compiling the latest mplayer from cvs.

After you run the configure script, make sure it's finding all the required codecs (divx4linux etc.) before you compile.

If you get stuck anywhere, ask bored2k. :mrgreen:

---

### Post by YourSurrogateGod on 2006-04-18
[QUOTE=psychicdragon]Check out [bored2k's guide]("http://ubuntuforums.org/showthread.php?t=85190&highlight=mplayer") to compiling the latest mplayer from cvs.

After you run the configure script, make sure it's finding all the required codecs (divx4linux etc.) before you compile.

If you get stuck anywhere, ask bored2k. :mrgreen:[/QUOTE]
Thanks, I'll try that when I have time.

---

### Post by YourSurrogateGod on 2006-04-20
Is there a simpler/easier way to play these files without having to compile mplayer?

---

### Post by CompShrink on 2006-04-27
Yes, look on the first page of the thread for compiling MPlayer from CVS, there are links several posts down, on the first page, for the .deb files. Those you simply download and in a terminal type in:

sudo dpkg -i /path/to/mplayer*.deb 

and it will install it, that's it.

---

### Post by yoshic on 2006-06-23
well.. if you are using dapper drake release.. all you need to do is:

```
sudo apt-get install gstreamer0.10-ffmpeg 
```

and you'll enjoy this excellent codec, of course you need all the repo enabled ;)

---

### Post by YourSurrogateGod on 2006-06-23
[QUOTE=yoshic]well.. if you are using dapper drake release.. all you need to do is:

```
sudo apt-get install gstreamer0.10-ffmpeg 
```

and you'll enjoy this excellent codec, of course you need all the repo enabled ;)[/QUOTE]
Yes, I've done that before and when it didn't work, I posted.

It seems to be working now though... for some reason.

---

### Post by Stabicron on 2006-07-05
I also have problems with an h264 .mkv except in my case it refuses to show the subtitles. I have ffmpeg installed. I have tried the following players: VLC, xine, totem, mplayer. Mplayer fails to show the subs, vlc will not play the file back right at all, lots of graphical curruption that isn't there in mplayers playback, the other two fail altogether. Is h264 support in linux really that far behind windows *I ask because I can play it back easily there*?

Any suggestions would be nice and so far doubt just compiling a cvs of mplayer will fix it as I am one of the few that doesn't use mplayer from the command line *this is one of the few things I require a gui on and I wish mplayers gui was better, my biggest gripe there is its complete lack of being able to change audio/subtitle streams in say a .ogm or .mkv from the gui*.

---

