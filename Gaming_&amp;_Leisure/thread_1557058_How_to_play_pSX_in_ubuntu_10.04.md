---
title: "How to play pSX in ubuntu 10.04?"
date: 2010-08-20
forum: Gaming &amp; Leisure
---

### Post by kirbyboy on 2010-08-20
Hi, im trying to play pSX in ubuntu 10.04, and actually i can play it, but the problem, as always, is pulseaudio.
To play, i created the file ~/.pulse/client.conf with the text "autospawn = no", and created a file to play pSX like this:

killall pulseaudio
./pSX #(or the aplication you want to run)
pulseaudio -D

and works perfectly.  The problem is that with autospawn = no, everytime i start ubuntu, pulseaudio is killed, and that's something i don't want, in ubuntu 9.10 did not happen.  How can i have the autospawn = no and pulseaudio starts always i start ubuntu?

---

### Post by disturbedite on 2010-08-20
make it a script for launching pSX and use that to start pSX.

---

### Post by kirbyboy on 2010-08-20
It's done as a script, the real problem is that with autospawn = no, everytime i start ubuntu, pulseaudio is killed.  Sorry if my english confused you.

---

### Post by disturbedite on 2010-08-21
> **kirbyboy said:**
> It's done as a script, the real problem is that with autospawn = no, everytime i start ubuntu, pulseaudio is killed.  Sorry if my english confused you.

you misunderstood me. what i meant was, instead of creating that .conf file perhaps see if there is a way to kill pulseaudio and then launch pSX afterwards with a script.

---

### Post by kirbyboy on 2010-08-23
autospawn = no must be in the .conf file, or else, pulseaudio can't be killed.  If you know a way to make that part inside the script, please, tell me.
Something like this?:
echo "autospawn = no">> ~/pulse/client.conf
#the rest of the code goes here
rm ~/pulse/client.conf

---

### Post by dfreer on 2010-08-24
> **kirbyboy said:**
> and works perfectly.  The problem is that with autospawn = no, everytime i start ubuntu, pulseaudio is killed, and that's something i don't want, in ubuntu 9.10 did not happen.  How can i have the autospawn = no and pulseaudio starts always i start ubuntu?

Could you add the command to start pulseaudio in your startup?

---

### Post by beloved88 on 2010-09-28
I got around the same problem in a sorta drastic method i found on another thread.  Problem is, with pSX's default configuration to use the option "Default" under the Device option in the sound tab, it won't run while pulseaudio is also running.  killall didn't work for me, it just kept coming back.  also, scripts meant to shut if off on pSX startup then start it up on pSX shutoff weren't working either.  I just ran ```
 sudo apt-get remove pulseaudio 
```, started pSX, changed the Device option to my actual device, then reinstalled pulseaudio.  it doesn't give me any problems now, accept for the case when i have something already running, ie Slacker radio.  I have to stop it before i start pSX or it gives me this error: ```
[src/linux/sound.cpp, line 582]: 'snd_pcm_open(&pcm_handle,dev->info->device_fname,SND_PCM_STREAM_PLAYBACK,0)' returned 'Device or resource busy'
pSX: pcm_params.c:2274: snd_pcm_hw_refine: Assertion `pcm && params' failed.
Aborted

```

---

### Post by whochismo on 2011-01-02
I think it's much easier than this. We need to kill pulseaudio, create the file client.conf with the "autospawn = no" option, and then run the game. And when the emulator stops, just the opposite.

First we create a client.conf file. We need to do this JUST ONCE! Copypaste and run the following in a console. 

> touch ~/.pulse/client.confDisabled
echo "autospawn = no">> ~/.pulse/client.confDisabled

And then create this script: 

> #!/bin/bash
mv ~/.pulse/client.confDisabled ~/.pulse/client.conf
gksudo killall pulseaudio
sleep 1
/home/user/pSX/pSX ## CHANGE THIS PATH TO THE CORRECT pSX PATH!!
sleep 1
pulseaudio &
mv ~/.pulse/client.conf ~/.pulse/client.confDisabled

(Don't forget to give execution permissions to this file)

Basically, it stops pulseaudio only during the execution of pSX, and when it's closed, it starts again. It works perfectly for me in Ubuntu 10.04 (and should run as well in 10.10)

---

