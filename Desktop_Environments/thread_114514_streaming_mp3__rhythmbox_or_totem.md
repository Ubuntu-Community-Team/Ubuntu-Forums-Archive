---
title: "streaming mp3:  rhythmbox or totem?"
date: 2006-01-08
forum: Desktop Environments
---

### Post by ChrisC on 2006-01-08
If I click on an mp3 streaming link (an m3u playlist) in Mozilla, it launches Rhythmbox, but then nothing happens within Rhythmbox -- no errors, nothing.  I do catch a quick "Loading" for a second in the status bar at the bottom but otherwise nothing.  It does this for multiple stations.

I tried loading an mp3 ***FILE*** into Rhythmbox, and Totem, and they both played fine, so it seems that I already have the necessary software (i.e. the RestrictedFormats stuff).  But *streaming* mp3 doesn't seem to work.

Should I expect it to work in Rhythmbox, and if so how can I troubleshoot further?  Or should I just tell Mozilla to launch Totem instead?

I definitely want to stick with "official" Ubuntu-supported programs, so if you have a suggestion for another player, limit it to those please :)

---

### Post by handy on 2006-01-08
Do you have the appropriate codecs installed for your browser?  That could possibly cause this problem I think...

If you install Automatix, you can select the option where that is done for you, & there sure are a lot of them!

[EDIT:]  [http://ubuntuforums.org/showthread.php?t=80295](http://ubuntuforums.org/showthread.php?t=80295)  It works fine on both 64 & 32bit.

Cheers,

handy

---

### Post by ChrisC on 2006-01-08
See 2nd paragraph.  The codecs are installed.  Thanks anyway.

---

### Post by handy on 2006-01-08
Ooops, I never was any good at speed reading!

Sorry.

handy

---

### Post by handy on 2006-01-08
I have the impression that there are browser specific codecs, meaning separate from the system ones.

Anyway, I'll be quite now...:rolleyes: 

handy

---

### Post by joeljkp on 2006-01-08
[QUOTE=ChrisC]Should I expect it to work in Rhythmbox, and if so how can I troubleshoot further?  Or should I just tell Mozilla to launch Totem instead?[/QUOTE]

I seem to remember Rhythmbox being no good at streaming mp3s. I usually use xmms, for what it's worth, but Totem sounds like the right tool for the job here.

---

### Post by doclivingston on 2006-01-08
[QUOTE=ChrisC]If I click on an mp3 streaming link (an m3u playlist) in Mozilla, it launches Rhythmbox, but then nothing happens within Rhythmbox -- no errors, nothing.  I do catch a quick "Loading" for a second in the status bar at the bottom but otherwise nothing.  It does this for multiple stations.[/QUOTE]

There is a bug filed about this in the Gnome bugzilla, but I can't find it at the moment. The problem is that when you do the above, the browsers downloads the playlist file (.m3u), and then hands the downloaded version to Rhythmbox. Rhythmbox needs the URL of the playlist, not the file, so it should work if you copy the link address and use that in RB's "add radio station" dialog.

---

### Post by crispy_420 on 2006-01-09
For streaming audio I usually use xmms as somebody mentioned before. I listen to shoutcast all the time this way. But that is not your only option. There are many apps that can do this(xinf, amarok, etc.).

You can also set your browser(firefox) to "auto-play" the link when clicked. xmms is very simple and takes up little desktop space but so is xinf. But if you like a little more flare, try amarok.

---

### Post by ChrisC on 2006-01-09
Thanks for the help.  I directed Mozilla to use Totem and it works fine.  So far I hate Totem, but that's another thread :)  I will get around to trying the others in due time, I'm sure.

---

### Post by altamaiz on 2006-01-30
I'm still struggling to get any app to play m3u streams.
I have a server that streams mp3s, I can play them on my <gasp> windows box using winamp (to establish that my site is working properly).
I can play mp3s that I've downloaded on my ubuntu box with rhythmbox and amarok.
I've also installed and reinstalled gstreamer0.8 plugins.
But still, I cannot play a stream.
Can anyone provide any more tips?
I read in another forum that some people were using xine instead of gstreamer?
Thanks

---

### Post by mtron on 2006-01-30
yea, the player engine for totem. install totem-gxine via synaptic and try then again with totem.

Did you install the win32 codecs?

---

