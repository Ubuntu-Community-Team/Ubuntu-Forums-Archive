---
title: "Wanted: working media player"
date: 2005-03-17
forum: Desktop Environments
---

### Post by josh2112 on 2005-03-17
Hello Ubuntu Gurus...

I am trying my hardest to make the total switch from Windows to Linux... Ubuntu has given me the best chance of that yet, but there are still these annoying and frustrating little issues popping up all over the place  ](*,).  Currently I'm trying to get a working audio solution.

Rhythmbox is nice, but refuses to play m4a's, in fact it crashes when I accidentally import a folder that contains them.  It gives the following error:

```

rhythmbox: relocation error: /usr/lib/gstreamer-0.8/libgstfaad.so: undefined symbol: NeAACDecOpen

```

So I tried mplayer -- it crashes with the same "relocation error", same symbol, but a different library  -- libavcodec.so.0.4.9-pre1.

Finally, I went to XMMS, which always did the job for me on Red Hat.  At least it runs.. that is until you try to play something.  It freezes up for a minute or two, the prints to the console "Message: alsa mixer timed out".  I went to Preferences and tried switching the output between esound, oss, alsa, etc. and got the same results with all of them.

This is a fresh install (just installed it 2 days ago).  Everything was fully updated thru Synaptic as of this afternoon using the Smart Upgrade thing.  I'm using the k7 kernel, and my system is an Athlon XP 3200+ with a gig of ram, nForce2 motherboard and a Sound Blaster Live 5.1 soundcard.

It's a little frustrating for someone who is used to Windows Media Player, just working, right out of the box.  And now I come to Linux and have 10 different media players and 10 different sound output systems, and each of them does a little piece of what I want, none of them does it all.

Also I understand that Hoary is a preview release, therefore I feel a little bad complaining about stuff... Warty users, do these problems exist on that release too?  Maybe I should downgrade and wait for Hoary to go stable?

Any ideas?

---

### Post by HungSquirrel on 2005-03-18
I don't have any m4a files to test this on, so I don't know if it works.  By going to the [XMMS input plugin page](http://www.xmms.org/plugins.php?category=input), I found an MP4 for XMMS plugin (m4a files are MP4).  There are two plugins that may help you.

[http://fondriest.frederic.free.fr/fichiers/libmp4.so](http://fondriest.frederic.free.fr/fichiers/libmp4.so)
[http://fondriest.frederic.free.fr/fichiers/libfaad.so](http://fondriest.frederic.free.fr/fichiers/libfaad.so)

Put them in /usr/lib/xmms/Input .  Let me know if this helps.

---

### Post by josh2112 on 2005-03-18
Thanks for the reply HungSquirrel.  I did as you suggested, and now when I start xmms I get the following error at the console:

/usr/lib/xmms/Input/libmp4.so: undefined symbol: NeAACDecDecode

then the same behavior as before -- I double-click on a playlist item, them xmms freezes.

I did a Google search, and from what I can tell somebody renamed all the faad* symbols to NeAAC*, and apparently all my media players know this and are looking for the new names, but some of my libraries still have the faad* prefixes.

The libfaad.so you linked to contains the NeAAC* symbols, but I did an ldd on libmp4.so and it was pointing at libfaad.so in /usr/lib, not /usr/lib/xmms/Input.  So I backed up the one in /usr/lib, made a symbolic link to the new one, and still didn't have any luck.

And I'm not sure if the "alsa mixer timed out" error is related to all this.

---

### Post by josh2112 on 2005-03-19
Problem solved.

I finally gave up, uninstalled Ubuntu, and spent all day today trying different distributions.

Fedora Core 3 wouldn't even boot up - udev doesn't like my motherboard.

SimplyMEPIS 3.3 was functionally perfect, although the display was halfway off the left side of my screen.  I spent 20 minutes in xvidtune trying to fix it, got something reasonably centered, then went into vi and discovered it was pretty much unusable because of Mepis's bizarre keyboard mappings.

So I said screw it, I'll just reinstall Ubuntu and deal with no m4a support.  That's what Windows is for, right?  Keep it as a dual-boot option until that day in the not-so-distant future when Linux is truly ready for the desktop.  But on a whim, I reinstalled xmms and the mp4 libraries, and lo and behold, IT WORKED!  I don't know how or why... but I'm happy for now.

---

### Post by lorap on 2005-03-19
hi friend!
i propose you use VLC player for everything.
XMMS player plays mp3 files,but avi it doesn't,so you'll need to add the codecs by yourself on you own (but it looks nice have to say,i use for mp3 files also).
VLC's its own codecs built in in the simple executable.
to install in do this Computer-->System Configuration-->Synaptic Package Manager.
after you get inside it go to the Settings-->Repositories.after the repositories window shows up,mark there all options ignoring warning messages then press Ok button.
after the repositories window closes up press the Reload button at the left up corner and wait.once the process's complete press the Search button and write in VLC then press Ok button.
once the synaptic's found it out for you mark it for install and press Apply button.
now you're done.
have a nice day.
pavel

---

### Post by bored2k on 2005-03-19
[QUOTE=lorap]hi friend!
i propose you use VLC player for everything.
XMMS player plays mp3 files,but avi it doesn't,so you'll need to add the codecs by yourself on you own (but it looks nice have to say,i use for mp3 files also).
VLC's its own codecs built in in the simple executable.
to install in do this Computer-->System Configuration-->Synaptic Package Manager.
after you get inside it go to the Settings-->Repositories.after the repositories window shows up,mark there all options ignoring warning messages then press Ok button.
after the repositories window closes up press the Reload button at the left up corner and wait.once the process's complete press the Search button and write in VLC then press Ok button.
once the synaptic's found it out for you mark it for install and press Apply button.
now you're done.
have a nice day.
pavel[/QUOTE]
 Yes but he will still need w32codecs working with totem because vlc though its my favorite and the one I use, certain file formats will run badly or just not show video on it .

---

### Post by lorap on 2005-03-19
that was probably the case why i couldn't watch one movie.
now i understand what was the reason.i felt the movie was ok but couldn't imagine vlc couldn't run in.
thanks.
pavel

---

### Post by bored2k on 2005-03-19
[QUOTE=lorap]that was probably the case why i couldn't watch one movie.
now i understand what was the reason.i felt the movie was ok but couldn't imagine vlc couldn't run in.
thanks.
pavel[/QUOTE]
 I always open my movies on VLC, but the moment I smell something fishy I retry on totem with w32codecs . [I wish we could add some of those codecs to vlc ;) ]

---

### Post by bored2k on 2005-03-19
> **bored2k]I always open my movies on VLC, but the moment I smell something fishy I retry on totem with w32codecs . [I wish we could add some of those codecs to vlc  said:**
> 
 [http://ubuntuforums.org/showthread.php?t=20678](http://ubuntuforums.org/showthread.php?t=20678)
VLC Feature list

You can see there some .wmv files won't show. Some normal files either but they wont recognize this .

By the way here are much better vlc sources :
[http://www.videolan.org/vlc/download-debian.html](http://www.videolan.org/vlc/download-debian.html)

---

### Post by lorap on 2005-03-19
thanks friend,i'll check it just right now :-)

---

### Post by Adrenal on 2005-03-19
Yeh, try
sudo apt-get install vlc
Think of it as itunes on crack

---

### Post by josh2112 on 2005-03-19
How about xine vs VLC?  (As I am too lazy to try them both on this machine :-)

I messed around with xine on MEPIS, seemed to play pretty much everything, plus when you played videos fullscreen, they were resampled -- VLC doesn't do any sort of smoothing and fullscreen videos look blocky.

---

### Post by bored2k on 2005-03-19
[QUOTE=josh2112]How about xine vs VLC?  (As I am too lazy to try them both on this machine :-)

I messed around with xine on MEPIS, seemed to play pretty much everything, plus when you played videos fullscreen, they were resampled -- VLC doesn't do any sort of smoothing and fullscreen videos look blocky.[/QUOTE]
  VLC is far more advanced that xine . They have a miriad of options to juggle with like Subtitling speed, live streaming etc.

Xine and Totem are great for "just push play" media, but if you mess with subs a lot and some of the subs arent in the correct speed, vlc has very good tools to resample [an example].

---

