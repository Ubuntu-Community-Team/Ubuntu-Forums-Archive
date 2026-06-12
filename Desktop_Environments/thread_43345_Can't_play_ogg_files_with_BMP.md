---
title: "Can't play ogg files with BMP"
date: 2005-06-21
forum: Desktop Environments
---

### Post by timelord726 on 2005-06-21
Hi all,

I find myself unable to play ogg files with Beep Media Player or XMMS and instead have to use Totem (which is what it opens them with by default).  I assume this is not as it should be.  Can I fix this?

Thanks!

---

### Post by Dave_is_sexy on 2005-06-21
Yeah i noticed stuff like that was happening too. That's why I started my thread about "low-down on video", hoping to learn that some players have internal codecs. 

I don't know for sure, but i reckon that's the reason. On my install hardly anythng works anywhere except in mplayer. Interestingly I installed every codec under the sun (not happy about that) and still nothing from totem. Mplayer first time, which suggests to me that totem uses internal codecs, as my codecs went on before Mplayer. Either that, or all the codecs failed and mplayer has al internal codecs as default?

---

### Post by timelord726 on 2005-06-21
That's odd.  So is there some kind of internal codec I need to install in order to get Beep Media Player to recognize and play ogg files?  If so, how would I do that?

---

### Post by Dave_is_sexy on 2005-06-21
Well i dunno if there is or not for sure. It could just be that there are paths or something which are pointing to the wrong place.

---

### Post by cwaldbieser on 2005-06-21
If you open up XMMS and go to Options -> Preferences (or just hit CTRL+P), you should see a dialog with a bunch of tabs.  On the AUDIO I/O tab, there is a section called "Input Pluggins".  One of my pluggins is called "Ogg Vorbis Player 1.2.10 [libvorbis.so]".  If I choose the "About" button for that pluggin, it gives me an about box with some info and the following URL: [http://www.xiph.org/](http://www.xiph.org/).

It looks like libvorbis.so comes from installing the "libvorbis0a" package with Synaptic on my system.  Hope that helps.

---

### Post by timelord726 on 2005-06-22
Strangely, I appear to be able to play ogg files through Beep Media Player if I tell the ogg files to open through XMMS.  Now, I've set ogg files to open with XMMS, and they'll open with Beep Media Player.  I also set it to open through BMP and that works too.  It must come from toggling the status of my Ogg Vorbis plugin on and off a few times.  Thanks for the assistance!

---

