---
title: "&quot;Unified&quot; sound"
date: 2006-08-07
forum: Desktop Environments
---

### Post by El_Isma on 2006-08-07
Hello!

My problem is the following: I'm playing music with XMMS, when I try to open some flash-video in Opera. I can't hear any sound coming from the flash-video (youtube, google video, etc). If I stop XMMS and reload the video, it plays sound. Same thing happens with vmware, if it has sound enabled XMMS can't play anything... But I want to be able to play all the sounds together.

I use KDE and some Gnome apps. XMMS is now configured with arts output (I figured it would enable other apps to use arts at the same time, it was with Alsa by default)

It occurs to me that the problem is that I haven't correctly configured my soundcard. It's an Nforce 3 with Realtek AC850 Chip, which Ubuntu correctly identified (I get what this page says I should: [http://doc.gwos.org/index.php/AudioCard/Alsa-doc/Nforce_3_sound](http://doc.gwos.org/index.php/AudioCard/Alsa-doc/Nforce_3_sound) ). Is there anything I have to do to the card? I read somewhere about a "hardware mixer" and alsa's dmix. Is that what I want?

Maybe the problem is that some programs output to OSS (I think vmware does), others to Alsa, and others to arts. Alsa is supposedly emulating OSS devices. So, while one program outputs to Alsa, arts can't output anything to it. If this is the problem, how do I tell all of them to play nice and share the soundcard?

BTW: Is this the right forum to post? I wasn't really sure.

Thanks for any help!
Ismael

---

### Post by El_Isma on 2006-08-12
Nothing?

---

### Post by longinus on 2006-08-12
I have the same problem (and a completly different card). I think this happens to a lot of people, and I never got it working... :(
Some programs just don't share the same audio output, and you can't change it..

---

### Post by christhemonkey on 2006-08-12
From the linux-audio-user mailing list:
[QUOTE=LAU]It's because your card lacks hardware mixing support and Flash only
supports the OSS API (/dev/dsp) which bypasses ALSA's software mixing.
The only solution is to get Flash to support ALSA natively, or get a
hardware mixing soundcard.

You might be able to work around this limitation of Flash by setting
FIREFOX_DSP to "aoss" in /etc/firefox/firefoxrc[/QUOTE]

NOTE: You do need the alsa-oss package installed!
```
sudo apt-get install alsa-oss 
```

---

