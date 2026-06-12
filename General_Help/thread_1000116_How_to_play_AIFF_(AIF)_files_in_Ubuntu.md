---
title: "How to play AIFF (AIF) files in Ubuntu"
date: 2008-12-02
forum: General Help
---

### Post by mjpatey on 2008-12-02
Hi, group-

I searched the forums here and finally found a post describing how to play AIFF (or AIF) files.  I wanted to post a confirmation that it does indeed work, and thank the person who posted the solution, but the thread is old and in the archives.

So I'm starting a new one!  Here's the solution:

```
sudo apt-get install sox
```

Then at the command line, simply navigate to the directory that your AIFF file lives in, and convert it to another format, like .WAV:

```
sox mysoundfile.aif mysoundfile.wav
```

If you have a boatload of AIFF files to convert in one directory, simply enter the directory and run a short script:

```
for i in *.aif; do sox "$i" "$i.wav"; done
```

Sox can also be tweaked with several options, but I'll leave you to the manpage for that stuff!  I want to thank [3rdalbum]("http://ubuntuforums.org/member.php?u=61044") for his/her help in the [original post]("http://ubuntuforums.org/showthread.php?t=58912").  The script is not from that post, but the idea to try sox is, so thanks, 3rdalbum!

I hope this helps somebody as much as it did me.

-Mark

---

### Post by treesurf on 2008-12-11
A friend just gave me a whole bunch of .aiff files and this little sox script saved me.  Thanks!

---

### Post by mc4man on 2008-12-12
Amarok will will playback .aiff no problem, no need to convert.

(As will mplayer, totem-xine, audacious, vlc, rhythmbox, ect.

---

### Post by mjpatey on 2008-12-12
@mc4man,

Hmm... if I set mplayer, vlc and rhythmbox to show "audio files" AIFs don't display... but if I set mplayer or vlc to recognize "all files," vlc will indeed play AIFs without a hitch!  Mplayer sort of plays them, but with a constant flashing error message.  With rhythmbox, I can't see a way to get it to recognize additional formats, so if it can play them, I can't tell.

I don't have Amarok, totem-xine or audacious installed, so I can't comment on those.

Thanks for making me check beyond the usual settings in VLC and Mplayer, though.  Quite helpful!

-Mark

---

### Post by mc4man on 2008-12-12
For rhythmbox install the 'gstreamer0.10-ffmpeg' plugin.

As far as mplayer I can't say, I  compile my own versions. If you use mplayer at all and don't want to build I'd suggest ck.ing here. (best way would be to add the rvm repo and get latest builds of mplayer/smplayer.

[http://ubuntuforums.org/showthread.php?t=917700&highlight=smplayer](http://ubuntuforums.org/showthread.php?t=917700&highlight=smplayer)

Note: if your using 8.10 then inconsistent behavior media wise would not be unexpected.

---

### Post by zaphodbblx on 2010-12-11
even easier use audacity and export as an .mp3

---

### Post by DanielWEWO on 2013-01-11
I Hate to rez this thread, but I'm an absolute beginner. I've learned how to navigate to that location, but it's telling me that it can't convert them because they are compression type 'ima4'

daniel@ubuntu:~/Music/J&M Ceremony$ for i in *.aif; do sox "$i" "$i.wav"; done
sox FAIL formats: can't open input file `Carmine's Entrance .aif': Unsupported AIFC compression type `ima4'


It says the same thing for every file in the folder. 

Sorry for being so new, I've been a windows user for years and years so Ubuntu is quite alien to me.

---

### Post by overdrank on 2013-01-11
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

