---
title: "Several problems with music/media in Hoary"
date: 2005-03-22
forum: Desktop Environments
---

### Post by mostwanted on 2005-03-22
I've managed to install RealPlayer and XMMS, but neither work without the sound server switched off, which means I can't hear when people write me in Gaim for example and that's quite annoying =/

Also, Rhythmbox looks like a great uukebox application (albeit very simple) but whenever I try to load an AAC (.m4a, .mp4) it dissappears. I've installed libraries so that it should be able to play AAC, but doesn't help when this happens...

Also, does anyone have any experience getting iPod support to work in it?

Thanks! There, that was 3 questions :)

---

### Post by wmcbrine on 2005-03-22
Yes, esd is hateful. Some have recommended switching to polyp, which used to be used in Warty. I'm just doing without system sounds for now (I mean the beeps, etc,; my media players are all switched to alsa and work fine now), so I can't say how well that works.

---

### Post by CyrilleMortreux on 2005-03-23
[QUOTE=mostwanted]I've installed libraries so that it should be able to play AAC, but doesn't help when this happens...
[/QUOTE]

May I ask you witch one ?
I spend my time converting mp4 and others to mp3 :(

Anyway, I have no troubles with gaim with my hoary. But when my son wants to play to Wesnoth, or Frozen Bubbles, I have first to kill esd to have sound working. And after, I have to launch it again to listen to music.

---

### Post by bored2k on 2005-03-23
[QUOTE=CyrilleMortreux]May I ask you witch one ?
I spend my time converting mp4 and others to mp3 :(

Anyway, I have no troubles with gaim with my hoary. But when my son wants to play to Wesnoth, or Frozen Bubbles, I have first to kill esd to have sound working. And after, I have to launch it again to listen to music.[/QUOTE]
 deb [http://luca.pca.it/debian/](http://luca.pca.it/debian/) ./
--> gstreamer-faad

I love esd . The problem is usually you all not configuring beep media player or xmms or totem or vlc or xine to use esd.

Go to its configure and enable esd .

---

### Post by CyrilleMortreux on 2005-03-23
[QUOTE=bored2k]deb [http://luca.pca.it/debian/](http://luca.pca.it/debian/) ./
--> gstreamer-faad

I love esd . The problem is usually you all not configuring beep media player or xmms or totem or vlc or xine to use esd.

Go to its configure and enable esd .[/QUOTE]


Totem, Rhythmbox, xmms works fine with me. Wesnoth; frozen bubbles and other games not. 

Thanks fot the link but is there an Ubuntu backport ? I experienced strange things once before with Debian unofficial packages on Ubuntu (Perl bas broken and I was forced to use a dpkg --force-drowngrade)

---

### Post by mostwanted on 2005-03-23
Ok, so I did a complete reinstall of Ubuntu Warty and reupgraded to Hoary with the sole goal of playing my AAC files in Rhythmbox, and it works now!

I won't bother with XMMS or RealPlayer anymore now. Totem and Rhythmbox seem the most integrated players, so I'll just use them.

---

### Post by Steel3 on 2005-03-23
[QUOTE=bored2k]deb [http://luca.pca.it/debian/](http://luca.pca.it/debian/) ./
--> gstreamer-faad

I love esd . The problem is usually you all not configuring beep media player or xmms or totem or vlc or xine to use esd.

Go to its configure and enable esd .[/QUOTE]

How do you configure vlc/xine to use esd?

---

### Post by Buffalo Soldier on 2005-03-23
[QUOTE=mostwanted]Ok, so I did a complete reinstall of Ubuntu Warty and reupgraded to Hoary with the sole goal of playing my AAC files in Rhythmbox, and it works now!

I won't bother with XMMS or RealPlayer anymore now. Totem and Rhythmbox seem the most integrated players, so I'll just use them.[/QUOTE]It's good to know another Rhythmbox & Totem lover :)

---

### Post by Steel3 on 2005-03-23
[QUOTE=Buffalo Soldier]It's good to know another Rhythmbox & Totem lover :)[/QUOTE]

Rythmbox seems good, but my main beef with it is that I can't import my entire library into it at once, but in small pieces or it'll crash.  I've tried creating playlists in other programs and importing them into rythmbox to no avail.  Otherwise, its a pretty good little program.

---

### Post by jMack on 2005-03-23
I'm curious as well:  can you configure vlc / mplayer to use esd?

I've got no sounds from DVD/avi playback since running symantec update w/ Warty.
Not sure how to properly configure it to work, but maybe configuring it to play through esd will do the trick....?

---

### Post by mostwanted on 2005-03-23
[QUOTE=Nirmal Mankani]Rythmbox seems good, but my main beef with it is that I can't import my entire library into it at once, but in small pieces or it'll crash.  I've tried creating playlists in other programs and importing them into rythmbox to no avail.  Otherwise, its a pretty good little program.[/QUOTE]

I was able to do that. iTunes on Windows kept all of my music in lots of folders, but all inside a single container folder, so I just imported that into Rhythmbox.

---

### Post by mostwanted on 2005-03-23
Anyway, I found out why Rhythmbox went bad before.

In the marillat depository is a bad package with some sort of dependency problem (the package is needed for AAC playback). This package can also be found in multiverse and this version works! But with the marillat depository enabled, it'll try downloading the bad package instead of the one in multiverse.

So I downloaded the most important stuff from marillat (w32codecs and stuff) and disabled it again, so I won't get surprised when running Ubuntu update and ruin everything again - it even tried updating for me before I could do that, but I canceled it.

---

### Post by Buffalo Soldier on 2005-03-23
[QUOTE=Nirmal Mankani]Rythmbox seems good, but my main beef with it is that I can't import my entire library into it at once, but in small pieces or it'll crash.  I've tried creating playlists in other programs and importing them into rythmbox to no avail.  Otherwise, its a pretty good little program.[/QUOTE]
 I hate to admit it but it's my main beef with Rhythmbox too. I guess I just have to live with it until it get fixed.

But I notice 1 think. After I clean the tags for my mp3 files... my rhythmbox havent had a crash... YET :P

---

### Post by Steel3 on 2005-03-23
[QUOTE=bored2k]deb [http://luca.pca.it/debian/](http://luca.pca.it/debian/) ./
--> gstreamer-faad

I love esd . The problem is usually you all not configuring beep media player or xmms or totem or vlc or xine to use esd.

Go to its configure and enable esd .[/QUOTE]

Since its not always intuitive as to how to configure each application to use esd (if it can), there's a useful guide on the [Ubuntu Wiki](https://www.ubuntulinux.org/wiki/RestrictedFormats) that details how to get esd to release the sound card when its not using it so other applications that aren't configured for esd can play sound normally.  I wish this would be set by default, but according to the wikipage everything in ubuntu main uses esd.

---

### Post by MaX on 2005-03-24
[QUOTE=Nirmal Mankani]Rythmbox seems good, but my main beef with it is that I can't import my entire library into it at once, but in small pieces or it'll crash.  I've tried creating playlists in other programs and importing them into rythmbox to no avail.  Otherwise, its a pretty good little program.[/QUOTE]

Your problem probably is that Rythmbox (at least older versions) crashes when it finds NON-mp3/audio objects in the folder, say Cover.jpg or desktop.ini (from windows) these sort of things made rythmbox just hang and didn't import anymore.

---

### Post by Steel3 on 2005-03-24
[QUOTE=MaX]Your problem probably is that Rythmbox (at least older versions) crashes when it finds NON-mp3/audio objects in the folder, say Cover.jpg or desktop.ini (from windows) these sort of things made rythmbox just hang and didn't import anymore.[/QUOTE]

Yeah, I've got a fair amount of those in my music folders -- seems like sometimes Rythmbox can get past them but not in large volumes.  Luckily, after switching to esd and telling esd to let go of the soundcard its all good.

---

