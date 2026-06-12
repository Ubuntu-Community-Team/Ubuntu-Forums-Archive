---
title: "~~~Has anyone ever got SOUND RECORDER work???"
date: 2005-10-17
forum: Desktop Environments
---

### Post by piggyaugu on 2005-10-17
I have to say that I have never made my sound input work properly under Linux. One time it worked under FC4, but under Ubuntu, never, neither Hoary nor Breezy.

My box is a IBM T41, the sound card is a integrated one(AC97). 

Anyone here has ever made his sound card record anything?

Can you tell me how you did the tricks?

Thx in advance.

:KS

---

### Post by shidai.liu on 2005-10-17
[QUOTE=piggyaugu]I have to say that I have never made my sound input work properly under Linux. One time it worked under FC4, but under Ubuntu, never, neither Hoary nor Breezy.

My box is a IBM T41, the sound card is a integrated one(AC97). 

Anyone here has ever made his sound card record anything?

Can you tell me how you did the tricks?

Thx in advance.

:KS[/QUOTE]

It worked under hoary not breezy. The recording program just freezes.

Open the volume control applet and click 'capture' and choose the right source of input. I successfully recorded bbc radio under hoary. I'm using AC97 integrated soundcard in Dell 700M.

---

### Post by piggyaugu on 2005-10-17
[QUOTE=shidai.liu]It worked under hoary not breezy. The recording program just freezes.

Open the volume control applet and click 'capture' and choose the right source of input. I successfully recorded bbc radio under hoary. I'm using AC97 integrated soundcard in Dell 700M.[/QUOTE]


I've tried that. 

I have even followed the "happy install" guide found in this forum. But it doesnt work for me. 

Actually, I can got some recording through mic. But it is rather pure noise than recording.

---

### Post by Antman on 2005-10-17
[QUOTE=piggyaugu]I have to say that I have never made my sound input work properly under Linux. One time it worked under FC4, but under Ubuntu, never, neither Hoary nor Breezy.

My box is a IBM T41, the sound card is a integrated one(AC97). 

Anyone here has ever made his sound card record anything?

Can you tell me how you did the tricks?

Thx in advance.

:KS[/QUOTE]

Works for me out of the box. Tried on a HP NC6220 laptop w/ AC'97 Audio (Intel ICH6)

---

### Post by Shabba on 2005-10-18
You need sox installed to record.

sudo apt-get install sox

Also, you might try to see if you if line in or mic is available by right clicking on the little speaker in the toolbar and select Open Volume Control. Make sure what you want to record is not crossed out.

I hope that helps you.

---

### Post by piggyaugu on 2005-10-18
[QUOTE=Shabba]You need sox installed to record.

sudo apt-get install sox

Also, you might try to see if you if line in or mic is available by right clicking on the little speaker in the toolbar and select Open Volume Control. Make sure what you want to record is not crossed out.

I hope that helps you.[/QUOTE]


I dont quite understand your method. Sox seems to be a format changing program.....:confused:

---

### Post by unexpected on 2005-10-18
Sound Recorder also doesn't work for me, it just freezes.

I also tried Audacity, and that doens't work as well. Ubuntu is receiving input, as I can hear my voice coming out of the speakers, but Audacity just doesn't want to record.

Anyone know what's going on?

---

### Post by Shabba on 2005-10-18
[QUOTE=piggyaugu]I dont quite understand your method. Sox seems to be a format changing program.....:confused:[/QUOTE]

Sox records the raw data into something you can later listen to (ogg, mp3 etc..)
as long as the codecs are available for it to do so. You can't record raw data as sound.

---

### Post by hajk on 2005-10-18
Well, I just recorded some old LPs to OGG with the Sound Recorder.

First, you should turn the system sounds in Preferences/Sound off, those beeps and groans are getting to be annoying after a while anyway; this frees up the /dev/dsp device.

Second, as somebody already said, run the mixer (either from the menu in Sound Recorder, or the Volume Control under Applications/Sound & Video), and turn 
Line-In or Capture (depending on where your source is -- it was Line-In for me) on and the level up. 

Then recording works. Right now, I haven't been able to play back the recording from within Sound Recorder (dunno why not), but saving the  recording to an .ogg file, then clicking on it starts Totem playing it (after first turning Line-In or Capture off).

---

### Post by anil_robo on 2005-12-17
Good news!
 I have successfully recorded sound in Ubuntu few times just half an hour back! Read my post [here]("http://www.ubuntuforums.org/showthread.php?t=102377#6")

---

### Post by jazzgossen on 2007-02-05
> **hajk said:**
> Well, I just recorded some old LPs to OGG with the Sound Recorder.

First, you should turn the system sounds in Preferences/Sound off, those beeps and groans are getting to be annoying after a while anyway; this frees up the /dev/dsp device.

Second, as somebody already said, run the mixer (either from the menu in Sound Recorder, or the Volume Control under Applications/Sound & Video), and turn 
Line-In or Capture (depending on where your source is -- it was Line-In for me) on and the level up. 

Then recording works. Right now, I haven't been able to play back the recording from within Sound Recorder (dunno why not), but saving the  recording to an .ogg file, then clicking on it starts Totem playing it (after first turning Line-In or Capture off).

Digging up a really old thread here, but I have similar problems with sound recording, running Dapper.

I've attached my mixer settings in the screenshot here (both alsamixer and gnome's volume control capture settings). Does anythig look wrong there? It looks a bit weird that there is no bar above the Mic settings in alsamixer, but no matter how much I press the up and down arrows there, nothing happens.

I can record using the same setup when I run Windows XP, and I can here my voice through the speakers also when I run Ubuntu, but no sound is recorded by Sound Recorder. I tried saving the recorded files and play them with XMMS, but everything that gets recorded is silence.
[IMG]http://eyra.se/temp/mixer.png[/IMG]

---

