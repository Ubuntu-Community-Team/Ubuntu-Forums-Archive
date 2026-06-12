---
title: "Enemy territory wont start!"
date: 2005-03-25
forum: Gaming &amp; Leisure
---

### Post by psyko-lefse on 2005-03-25
When I try running ET the screen goes black, and nothing more happens. The fglrx-drivers are installed and working, and ET ran great when I was using warthy. I've had read other topics regarding this, but I havent found a solution to the problem. Also, when playing video with VLC, there's not sound, can these problems be related?

On the bright side, Hoary solved many of the problems I had when using warthy, like speedstep and WLAN =D>

---

### Post by Corey on 2005-03-25
I haven't tried VLC, but I have the same problem with enemy territory. Even in the new 2.60 version. :( Bummer, I really really really wanna play the new True Combat: ELITE!

---

### Post by psyko-lefse on 2005-03-26
I'm also using the latest versjon, 2.60. Maybe this is the problem, since it worked fine when using 2.56(?)....

---

### Post by macmasterxiv on 2005-03-26
[QUOTE=psyko-lefse]I'm also using the latest versjon, 2.60. Maybe this is the problem, since it worked fine when using 2.56(?)....[/QUOTE]
 I think the version may be the culprit, since I also have the problem. (using mesa rendering; fglrx=broke)

---

### Post by jensyt on 2005-03-26
[QUOTE=psyko-lefse]I'm also using the latest versjon, 2.60. Maybe this is the problem, since it worked fine when using 2.56(?)....[/QUOTE]
Your initial ambitions were correct: it is a sound problem. I've used this patch without any problems (had to downgrade again because most servers don't yet have it, though). Sadly, I can't remember the solution exactly, but it is definitely a sound issue. Enemy Territory cannot get control of the sound device, and therefor can't initialize sound. And since that doesn't work, it waits until it **can**, which I'm assuming would be never. I think restarting esd has something to do with it, but the details have left me, sorry.

---

### Post by psyko-lefse on 2005-03-26
Do you have any links  to the 2.56 version? I'll try with that one first....

---

### Post by Lindo on 2005-03-26
try this command, it has worked for me "killall -9 esd"  :mrgreen:

---

### Post by dcraven on 2005-03-26
Yes. Kill esd and you're golden.

Cheers,
~djc

---

### Post by psyko-lefse on 2005-03-26
[QUOTE=Lindo]try this command, it has worked for me "killall -9 esd"  :mrgreen:[/QUOTE]
 Jepp, it worked, VLC also! But there's got to be a more sutible solution, since programs depending on esd dont work anymore, like Music player. This wasn't a problem in Warthy, why is it one in Hoary? argh....

---

### Post by atf487 on 2005-03-26
I don't know about you guys, but esd never works well for me. I always use oss/alsa and I'm fine. 

and i didnt know the game was updated!

---

### Post by psyko-lefse on 2005-03-26
[QUOTE=atf487]I don't know about you guys, but esd never works well for me. I always use oss/alsa and I'm fine. 

and i didnt know the game was updated![/QUOTE]
 Esd seemes to be the standard in ubuntu 5.04. How do I get oss/alsa?

---

### Post by maqi on 2005-04-12
I found a script for audacity - which has the same problem wit esd. I have altered it for et & I simply have a launcher on the panel which points to this script. I have saved it as ~/bin/et. It's a bit of a rough and ready workaround but ... it works :) If anyone can see how this could be improved please do so.

```
#!/bin/bash

killall esd
sleep 2 # To give the previous command time to fully complete
/usr/local/games/enemy-territory/et
esd

#
# This script is based on a script by a guy named Wulf. Found here: http://www.ubuntuforums.org/printthread.php?t=6551
#

```

You will hear a weird noise when you quit et and esd restarts. You could do the same thing for vlc ;)

One problem - et starts in fullscreen mode. When I quit my desktop is oversized - resolution is the same but it's magnified and sticks out past the edges of my screen. I end up having to change resolution and then revert to my original. Does anyone know how to fix this? EDIT : don't worry saw in onother post - made game resolution and desktop resolution the same - problem gone :)

cheers,
maqi

---

### Post by tont on 2005-04-13
but when i kill esd, i dont hear teamspeak/music..

---

### Post by maqi on 2005-04-13
[QUOTE=tont]but when i kill esd, i dont hear teamspeak/music..[/QUOTE]

I found a better solution [here](http://www.ubuntuforums.org/showthread.php?t=26567) - means you don't need to kill esd. I'm no longer using the script and et launches perfectly. I don't know if it works for all sound cards but it worked for me with my onboard sound.

---

### Post by Skid on 2005-04-13
[QUOTE=maqi]I found a better solution [here](http://www.ubuntuforums.org/showthread.php?t=26567) - means you don't need to kill esd. I'm no longer using the script and et launches perfectly. I don't know if it works for all sound cards but it worked for me with my onboard sound.[/QUOTE]

Which solution did you use?

I just posted and found out that this is the problem (the killing of esd solves it).  However, XMMS will play with the ASLA plugin selecting, and the OSS, etc.. BMP plays with ESD, but not ALSA - *shrug*.

I've changed the esd.conf file to match what that post says, but still... odd?

---

### Post by tont on 2005-04-13
[QUOTE=maqi]I found a better solution [here](http://www.ubuntuforums.org/showthread.php?t=26567) - means you don't need to kill esd. I'm no longer using the script and et launches perfectly. I don't know if it works for all sound cards but it worked for me with my onboard sound.[/QUOTE]actually i didn't understand a shit of this.. bad english or something :-|

---

### Post by Skid on 2005-04-13
[QUOTE=tont]actually i didn't understand a shit of this.. bad english or something :-|[/QUOTE]
 The english is perfectly understandable...

Maqi - what onboard soundcard is it AC'97?

---

### Post by maqi on 2005-04-14
[QUOTE=Skid]The english is perfectly understandable...

Maqi - what onboard soundcard is it AC'97?[/QUOTE]

Not sure if I understand  :-P  :-P 

Yes. There's another post somewhere in the forums which mentions the same fix (search "esd" + "alsa") and the guy uses the i8x0 driver. I'm not sure if this fix only works on AC97 or not.

Must admit that I haven't tried listening to music while I play (I never do this - I generally want to hear what's going on) and I haven't tried teamspeak on ubuntu. I couldn't get it to work on debian so I didn't bother. Besides the only game I use TS for I play on what I call my Micro$hit X(P) Box. So I'm not sure exactly how well this works. All I know is that I no longer have apps refuse to open because the sound device is busy.

maqi

---

