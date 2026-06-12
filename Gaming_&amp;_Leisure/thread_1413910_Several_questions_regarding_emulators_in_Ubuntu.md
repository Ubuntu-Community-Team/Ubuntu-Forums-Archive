---
title: "Several questions regarding emulators in Ubuntu"
date: 2010-02-23
forum: Gaming &amp; Leisure
---

### Post by ThanosIsKing on 2010-02-23
I have Ubuntu 9.10. I've been trying to create my own Let's Play-s using DOSBox and other emulators. I have several questions regarding this however.

Regarding DOSBox (I have 0.73):
QUESTION 1)
I know that the CTRL+ALT+F5 that normally starts/stops video recording is already used by Ubuntu for something else, so I've remapped the video capture to CTRL+ALT+R. However, pressing this never does anything. I never see anything that lets me know that video recording is commencing (though I don't know if anything is supposed to happen to let you know about this), and when I exit DOSBox and go hunting for my video, it's nowhere to be found. Is there a fix for this?

QUESTION 2)
I want to be able to include my own audio commentary on the games. Is there a way to set up DOSBox in Ubuntu to be able to record a second audio (like from a microphone) on top of the audio/video of the game?

CONSOLE EMULATORS:
QUESTION 1)
I've heard that there is a way to set up emulators like ZSNES and VBA to be able to capture video of your gameplay, much like what I'm attempting to do with DOSBox. How would I set up those two emulators in order to accomplish this? I'm assuming that, unlike with DOSBox, I would have to record my audio commentary separately when using ZSNES and VBA.

---

### Post by Nevon on 2010-02-23
Your best bet would probably be to use something like recordmydesktop (it's in the repos) to handle video and audio recording of the game, and simultaneously recording the microphone sound with some other sound recorder (audacity or the recording software that comes with Ubuntu).

---

### Post by ThanosIsKing on 2010-02-24
Thanks for letting me know about recordMyDesktop. It's been working wonders for me. HOWEVER, I haven't been able to get the audio of the game to be recorded along with the video. Video is great, but could you help me get recordMyDesktop to pick up the game's audio as well?

---

### Post by punkrockguy318 on 2010-02-25
fceuX supports audio and video recording out of the box

---

### Post by Nevon on 2010-02-25
> **ThanosIsKing said:**
> Thanks for letting me know about recordMyDesktop. It's been working wonders for me. HOWEVER, I haven't been able to get the audio of the game to be recorded along with the video. Video is great, but could you help me get recordMyDesktop to pick up the game's audio as well?

It might be that your sound card just isn't equipped to handle stereo mix. Mine isn't. What you could do is right click on the volume indicator, choose "sound preferences", go to the hardware tab and muck around with the settings there. You might also have to go into the "input" tab and fiddle around some.

---

### Post by d3v1150m471c on 2010-02-25
You can combine jackd with recordmydesktop to pull sound from input and/or output. I've seen this done successfully but was never able to do it myself

---

### Post by ThanosIsKing on 2010-02-25
> **d3v1150m471c said:**
> You can combine jackd with recordmydesktop to pull sound from input and/or output. I've seen this done successfully but was never able to do it myself

I'm assuming you do it [with this method](http://ubuntuforums.org/showthread.php?t=986966), however when I start up JACK and try to start the audio recording (as per instructions in the link), I get an error message saying "Could not connect to JACK server as a client. Overall operation failed, Unable to connect to server." The message window says "cannot use real-time scheduling (FIFO at priority 10). Cannot create engine".

This is really starting to cheese me off. It's funny, in a sad way, to watch my computer thwart all my attempts to create a good-looking Let's Play video.

I'm at my wits end. I'm not one to give up easily, but if anyone's solution to this latest problem doesn't work, I'm gonna have to forget about it and just go make the video without the game's sounds.:-x

---

### Post by Nevon on 2010-02-26
> **ThanosIsKing said:**
> I'm at my wits end. I'm not one to give up easily, but if anyone's solution to this latest problem doesn't work, I'm gonna have to forget about it and just go make the video without the game's sounds.:-x

While it is a horrible, horrible hack, what you could do is place a microphone by the speakers and record the sounds this way.

---

### Post by mastablasta on 2010-02-26
I will take a guess but doesn't DosBox have a command to record also in Linux? i would ask about it on their forums.
 
And i would record the whole thing first and then record my comment and then put it all together. game sounds in background and my comment in front.

---

### Post by ThanosIsKing on 2010-03-01
> **Nevon said:**
> While it is a horrible, horrible hack, what you could do is place a microphone by the speakers and record the sounds this way.

Tried this method. recordMyDesktop STILL refuses to record audio on top of video. I noticed that recordMyDesktop has an option to use JACK to capture audio, but that would require JACK to start working for me. Here's what JACK says when I try to initialize it:

> **JACK]
 p, li { white-space: pre-wrap said:**
> 16:47:05.918 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]16:47:05.971 Statistics reset.[/COLOR]
 [COLOR=#66CC99]16:47:06.035 ALSA connection graph change.[/COLOR]
 [COLOR=#CCCC99]16:47:06.229 ALSA connection change.[/COLOR]
 [COLOR=#999999]16:47:16.390 Statistics reset.[/COLOR]
 [COLOR=#CCCC99]16:47:36.414 ALSA connection change.[/COLOR]
 [COLOR=#999999]16:47:46.496 JACK is starting...[/COLOR]
 [COLOR=#990099]16:47:46.497 /usr/bin/jackd -R -dalsa -dhw:0 -r44100 -p1024 -n2 -C -i1[/COLOR]
 [COLOR=#999999]16:47:46.676 JACK was started with PID=15802.[/COLOR]
 no message buffer overruns
 jackd 0.116.1
 Copyright 2001-2005 Paul Davis and others.
 jackd comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 JACK compiled with System V SHM support.
 cannot use real-time scheduling (FIFO at priority 10) [for thread -1216039232, from thread -1216039232] (1: Operation not permitted)
 cannot create engine
 [COLOR=#999999]16:47:47.120 JACK was stopped successfully.[/COLOR]
 [COLOR=#999999]16:47:47.121 Post-shutdown script...[/COLOR]
 [COLOR=#990099]16:47:47.121 killall jackd[/COLOR]
 jackd: no process found
 [COLOR=#999999]16:47:47.606 Post-shutdown script terminated with exit status=256.[/COLOR]
 [COLOR=#FF0000]16:47:48.709 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[COLOR=Black][/COLOR][/COLOR]

[COLOR=#FF0000][/COLOR]
[COLOR=#FF0000][COLOR=Black]I *REALLY, REALLY* don't want to have to make my videos without the game's audio. Any clue as to what might be making JACK not want to work? Or am I going on a wild goose chase with JACK? Is it looking to be impossible to capture audio?
[/COLOR][/COLOR]

---

### Post by Nevon on 2010-03-02
> **ThanosIsKing said:**
> Tried this method. recordMyDesktop STILL refuses to record audio on top of video. I noticed that recordMyDesktop has an option to use JACK to capture audio, but that would require JACK to start working for me.

If you were trying to record audio via a mic through the speakers, you woulnd't use recordmydesktop for that. You could use the standard sound recorder or something for that. 

I did try to see if I could get JACKd working for me, but I get the same problem as you. Either something has changed in the later versions of Ubuntu, or neither of us has a sound card with the proper capabilities.

---

