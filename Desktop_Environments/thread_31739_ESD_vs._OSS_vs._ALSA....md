---
title: "ESD vs. OSS vs. ALSA..."
date: 2005-05-04
forum: Desktop Environments
---

### Post by sonshyneteen on 2005-05-04
<I'm a newbie to Linux, but I'm trying to figure these things out as I go...>

I currently have Ubuntu "Hoary" installed on my i386 PC, and most everything works perfectly.  However, while I **can** get sound through TotemPlayer and XMMS, I **cannot** get any sound from Rhythmbox Music Player, or even VLC.  This is a pain because, while I like XMMS, Rhythmbox has a more organized interface, which is nice!  And although TotemPlayer plays DVD's ok, it's a lot slower than VLC (for me, at least).

I have set "Multimedia Systems Selector" to the default "ESD" sink and "OSS" source.  I have no clue what the difference b/twn sink and source is...

Audio ONLY works in XMMS when the output is set to ALSA plug-in under XMMS preferences.  Maybe this is a clue???

I have read some about editing the esdconfig file, which I did try, but nothing changed, so I went back to the default settings.  Has anyone had success doing this, esp. if only ALSA seems to be working?  (I haven't a clue what TotemPlayer uses for it's output, or how to adjust that, but it's working anyhow... albeit slowly).

Thanks in advance for all of your tips,
~ Sonshyne

---

### Post by sonshyneteen on 2005-05-04
::bump::

---

### Post by wolovids on 2005-05-04
Do you have esd running?

---

### Post by MaX on 2005-05-04
[QUOTE=sonshyneteen]<I'm a newbie to Linux, but I'm trying to figure these things out as I go...>

I currently have Ubuntu "Hoary" installed on my i386 PC, and most everything works perfectly.  However, while I **can** get sound through TotemPlayer and XMMS, I **cannot** get any sound from Rhythmbox Music Player, or even VLC.  This is a pain because, while I like XMMS, Rhythmbox has a more organized interface, which is nice!  And although TotemPlayer plays DVD's ok, it's a lot slower than VLC (for me, at least).

I have set "Multimedia Systems Selector" to the default "ESD" sink and "OSS" source.  I have no clue what the difference b/twn sink and source is...

Audio ONLY works in XMMS when the output is set to ALSA plug-in under XMMS preferences.  Maybe this is a clue???

I have read some about editing the esdconfig file, which I did try, but nothing changed, so I went back to the default settings.  Has anyone had success doing this, esp. if only ALSA seems to be working?  (I haven't a clue what TotemPlayer uses for it's output, or how to adjust that, but it's working anyhow... albeit slowly).

Thanks in advance for all of your tips,
~ Sonshyne[/QUOTE]
 Read the Unofficial FAQ

---

### Post by sonshyneteen on 2005-05-04
[QUOTE=wolovids]Do you have esd running?[/QUOTE]

Hmm... I would say "yes," but I'm not sure.  How do I find out?

---

### Post by kvidell on 2005-05-04
[QUOTE=sonshyneteen]Hmm... I would say "yes," but I'm not sure.  How do I find out?[/QUOTE]
lsof | grep dsp
or
ps aux | grep esd


I suppose the first one is just for figuring out if something is harassing your soundcard and keeping something you actually WANT emitting sound from running. (which for me, 99% of the time, is ESD (being stupid))
I always have to kill -9 ESD so I can do other things (like look at flash animations or run bmp, kphone, etc..)

---

### Post by Arthemys on 2005-05-08
[QUOTE=kvidell]lsof | grep dsp
or
ps aux | grep esd


I suppose the first one is just for figuring out if something is harassing your soundcard and keeping something you actually WANT emitting sound from running. (which for me, 99% of the time, is ESD (being stupid))
I always have to kill -9 ESD so I can do other things (like look at flash animations or run bmp, kphone, etc..)[/QUOTE]

As you've told me it stops all system bells from working which for you and myself doesn't really matter cause sounds suck. :P

Quick fix right now as I can find it is to go up to your "System" menu then "Preferences" then "Sound" and turn off the starting of the sound server.

From what I can tell so far, this is an issue with GNOME itself, since that's where it gets started from... I could be wrong.

---

### Post by nix4me on 2005-05-08
Read the howto section.  There is a post in there on how to get esd and alsa running at the same time.  I did it and it all sound works fine.

Here is the link:
[http://www.ubuntuforums.org/showthread.php?t=32063](http://www.ubuntuforums.org/showthread.php?t=32063)

Worked great for me.

nix

---

### Post by Arthemys on 2005-05-08
[QUOTE=nix4me]Read the howto section.  There is a post in there on how to get esd and alsa running at the same time.  I did it and it all sound works fine.

Here is the link:
[http://www.ubuntuforums.org/showthread.php?t=32063](http://www.ubuntuforums.org/showthread.php?t=32063)

Worked great for me.

nix[/QUOTE]

I second this motion, worked beautifully.  :smile:

---

### Post by psoleko on 2005-05-08
Some programs like VLC need the ESD output plugin to work. If you search synaptic for VLC and ESD you'll see it in there. You will have to enable it as your sound output for VLC.

---

