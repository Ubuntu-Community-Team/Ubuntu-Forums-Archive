---
title: "MPlayer plugin for firefox sounds choppy"
date: 2006-01-11
forum: General Help
---

### Post by bennettg on 2006-01-11
Hi.  nOOb here.

Fresh install.  Back to ubuntu/kubuntu after flirting with suse.

i used arnieboy's amazing automatix to install firefox and mplayer plugin.  when i stream audio (ie national public radio, cbc.ca, etc) it works but sounds real choppy...pops at times.  not smooth.

i tried playing with the preferences in mplayer without success.  tried to search the forums here too.

i am such a noob that i dont know where to start.  please help

---

### Post by Masteroc on 2006-01-11
maybe it is your internet connection or even your sound card.

---

### Post by TransitMan on 2006-01-11
[QUOTE=Masteroc]maybe it is your internet connection or even your sound card.[/QUOTE]

Well, I doubt it is the internet connection or sound card.
I am also experiencing the same issues, with sound and/or video in Firefox with the mplayer plugin.



A lot of us switching to Ubuntu Linux are always looking for answer to questions raised, not something as stupid as your response.

So how about a solution instead of a half-assed answer, please.

---

### Post by akudewan on 2006-01-12
[QUOTE=TransitMan]Well, I doubt it is the internet connection or sound card.
I am also experiencing the same issues, with sound and/or video in Firefox with the mplayer plugin.



A lot of us switching to Ubuntu Linux are always looking for answer to questions raised, not something as stupid as your response.

So how about a solution instead of a half-assed answer, please.[/QUOTE]

Actually Transitman does have a point, only that he hasn't put it well. If your internet connection is too slow, then internet radio sometimes becomes choppy. I have a 128kbps connection, for instance, and some stations just don't work right.

Assuming that you have a good internet connection, another thing that you can try is playing a audio/video file from disk. If the quality is still bad, then it must be a problem with mplayer, and you can try tweaking your preferences.

You could also try some other app. like gxine if mplayer isn't working right.

Hope this helps a little.

---

### Post by rubengs on 2006-01-12
I have the same problem with audio and video in mplayer-plugin, the video and audio files played through mplayer sounds and looks good, the problem is in the mplayer firefox plugin only, I have an ATI card and a Intel motherboard with integrated soundcard based in the REALTEK audio codec. The problem is not the connexion, I have a fast internet line. 

Anybody have some ideas? I tried to change the buffer, and the audio driver (ALSA, OSS) in mplayer with no exit.

---

### Post by bennettg on 2006-01-12
it is definately not theinternet connection or the sound card.  I have fiber optic to the home from verizon and the sound card works fine with streaming real player radio.   i even upgraded to the i686mplyer package without any success.

can anyone help us>?

---

### Post by Horndog on 2006-01-12
The Mplayer plugin is a POS. I have the same problem with it. I paste the url to my RealPlayer 10 and it it is a world of difference. If it wasn't so easy to use RealPlayer as is I would get rid if Mplayer as a plugin.

---

### Post by bennettg on 2006-01-12
someone please help us.

i dont think it is mplayer plugin since i had recently flirted with opensuse and there wasnt any problem

---

### Post by bennettg on 2006-01-12
SOLVED.

edit /etc/mplayer/mplayer.conf   add the following to the bottom of the file:

srate=48000


THEN EVERYTHING IS BLISS!!!!!!!!!!!!!!!!!!

---

### Post by Greg T. on 2006-01-29
bennettg's solution worked for me as well. 

As background, I was having choppy playback, only in mplayer plugin. This was the case even when I created a web page that linked to a video on my hard drive, so I knew it wasn't an internet connection issue. (The videos played fine when loaded directly by mplayer, but not when shown as embedded videos using the plugin.)

---

### Post by Greg T. on 2006-01-29
Spoke too soon. Changing to ESD helps, but the sound and video go out of sync. Changing to 48000 does nothing for me.

---

### Post by Horndog on 2006-01-29
Here is something to try If you must use that player. Change the output audio to oss.

---

### Post by Greg T. on 2006-01-29
Tried OSS. Video plays without prob, but in complete silence.

---

### Post by Greg T. on 2006-01-29
At last, success. I replaced my /etc/asound.conf file with the one in this thread: [http://www.ubuntuforums.org/showthread.php?t=44753](http://www.ubuntuforums.org/showthread.php?t=44753)

This is an OSS-friendly configuration. It allowed me to use OSS in the mplayer plugin. No stuttering and everything's in sync.

Oddly, under this new configuration using ALSA in the plugin no longer results in stuttering, but instead produces Alvin-&-the-Chipmunks high-pitched sound. ALSA seems fine in other programs, though. Damn strange, but it works.

---

### Post by TechSonic on 2006-01-30
[QUOTE=TransitMan]Well, I doubt it is the internet connection or sound card.
I am also experiencing the same issues, with sound and/or video in Firefox with the mplayer plugin.



A lot of us switching to Ubuntu Linux are always looking for answer to questions raised, not something as stupid as your response.

So how about a solution instead of a half-assed answer, please.[/QUOTE]


Hey man, the guy is only suggesting.  He is only trying to help you.  Don't get all ticked off for people helping you out for no benifit to them selfs.  If you paid for this help, then you have a right to piss and moan.

---

### Post by catric69 on 2006-04-17
[QUOTE=bennettg]SOLVED.

edit /etc/mplayer/mplayer.conf   add the following to the bottom of the file:

srate=48000


THEN EVERYTHING IS BLISS!!!!!!!!!!!!!!!!!![/QUOTE]

This edit worked great!  I am now able to listen to my flac files on my hdd without the choppy sound.  I have not tried any videos yet, but I cross that bridge when I get to it.

Thanks,

Eric.

---

### Post by _linux_ on 2006-04-17
[QUOTE=bennettg]Hi.  nOOb here.

Fresh install.  Back to ubuntu/kubuntu after flirting with suse.

i used arnieboy's amazing automatix to install firefox and mplayer plugin.  when i stream audio (ie national public radio, cbc.ca, etc) it works but sounds real choppy...pops at times.  not smooth.

i tried playing with the preferences in mplayer without success.  tried to search the forums here too.

i am such a noob that i dont know where to start.  please help[/QUOTE]
Well, if you're only having these problems with MPlayer, try using VLC. It also has a plugin for Firefox and supports many formats. I use VLC and it's very good! :KS

---

### Post by rynop on 2006-05-04
"srate=48000"

the above worked like a charm for me.  This problem has been pissing me off to no end - thanks!

---

### Post by zugvogel on 2006-05-06
This srate command worked fine. This problem has been causing me a lot of difficulties. Thank you very much for this!

---

### Post by gommle on 2006-05-08
Thanks! Worked for me too.
Im using ALSA.

Is there any way the mplayer plugin can begin playing without caching it 100%?
So i dont have to wait, like quicktime or windows media player.

---

