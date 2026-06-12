---
title: "Microphone with very low volume"
date: 2005-12-24
forum: General Help
---

### Post by Nekrataal on 2005-12-24
Anyone knows how to fix this?, i really would like to use voip programs but this bug is not leting me, please help!

---

### Post by Nekos on 2005-12-31
i have the same problem, any solution ? :(

---

### Post by martibs on 2006-01-05
In gmix there is an option named "Mic Boost", which will make it a bit louder. I have the same problem, and although the mic boost made it louder, it's still quite low.

---

### Post by anil_robo on 2006-01-05
1. Test your mike with another PC and another OS. The fault may be in the mike itself.
2. Double click the volume icon in the system tray. Open up Edit-->Preferences. Tick "capture" and you would then see the capture sliders. Make sure you set the "microphone" and "capture" sliders to maximum.
 
Let me know.

---

### Post by RagingOcelot on 2006-01-09
I have the same problem.  I followed the advice and it's still a no-go with the mic.  I have sound output just fine but very low mic input.  I have a C-Media CMI8738-MC6.  I'd like to be able to use skype and gizmo eventually.

---

### Post by The Mekon on 2006-01-09
[QUOTE=anil_robo]1. Test your mike with another PC and another OS. The fault may be in the mike itself.
2. Double click the volume icon in the system tray. Open up Edit-->Preferences. Tick "capture" and you would then see the capture sliders. Make sure you set the "microphone" and "capture" sliders to maximum.
 
Let me know.[/QUOTE]

also after double clicking on the Volume Icon click on Switches and then Mic Boost (+20db) which boosts the mic's level 10 times.

---

### Post by RagingOcelot on 2006-01-09
I can record my voice in Audacity with mic-boost on and then play my recording back with the gain bar in Audacity at full boost and it plays to almost where it should be (just as a reference).

---

### Post by saads on 2006-02-23
Has anyone figured this one out?  I have the same problem

---

### Post by The Mekon on 2006-02-24
[QUOTE=anil_robo]1. Test your mike with another PC and another OS. The fault may be in the mike itself.
2. Double click the volume icon in the system tray. Open up Edit-->Preferences. Tick "capture" and you would then see the capture sliders. Make sure you set the "microphone" and "capture" sliders to maximum.
 
Let me know.[/QUOTE]

In addition to the above  in Preferences check if you can find Mic Boost (+20db).  If so tick its box.

You should now have an extra tab next the Capture tab called switches.  This will allow you to boost the mic volume by 20 db which is quite noticlble.

---

### Post by Deaf_Head on 2006-02-24
zi have this same problem and can't find a mic boost button either. I KNOW my microphone works because it works fine perfect in windows.

---

### Post by Deaf_Head on 2006-02-24
[QUOTE=Deaf_Head]zi have this same problem and can't find a mic boost button either. I KNOW my microphone works because it works fine perfect in windows.[/QUOTE]
 nvm i got mic boost working, quality is nowhere near as good as it is in windows though

---

### Post by cotcot on 2006-02-25
I recognise the problem by me too. A way to work around it :

>system>preference>sound  Disable starting the sound server at startup.

It is only a work around. The sound server is to be enabled afterwards.

I am not sure about the syntax of "system" because i am using the desktop in Dutch. Could be "administration". (Maybe i should change the language)

---

### Post by saads on 2006-02-25
so you're saying enabling it after startup will fix the problem?  What command do u use to enable the sound?

---

### Post by beauty on 2006-04-01
[QUOTE=The Mekon]In addition to the above  in Preferences check if you can find Mic Boost (+20db).  If so tick its box.

You should now have an extra tab next the Capture tab called switches.  This will allow you to boost the mic volume by 20 db which is quite noticlble.[/QUOTE]
I have "Volume Control 2.12.0 / A GNOME/GStreamer-based volume control application"
It gives me a 'Playback' tab and a 'Capture' tab.  I have no 'Switches' tab and nothing about 'Mic Boost'.  
Any Ideas?

---

### Post by rvergara on 2006-04-04
I had the same problem with 5.10. My sound card is 7.1 and supports ALSA. I went to the mixer and in the preferences I noticed that instead of just one capture I have 3 capture boxes. I ticked all of them and then slide their controls to maximum. Capture 3 did boost the mic volume. It is not as I would like but it is usable.
Hope this helps to anybody having similar problems with Audio Cards 5.1 and 7.1

Regards

Ramiro

---

### Post by jinxed on 2006-04-16
[QUOTE=RagingOcelot]I have the same problem.  I followed the advice and it's still a no-go with the mic.  I have sound output just fine but very low mic input.  I have a C-Media CMI8738-MC6.  I'd like to be able to use skype and gizmo eventually.[/QUOTE]

I've got the same card, and the same problem... any solution yet? I have no option for the +20db boost...

---

### Post by xyz on 2006-04-16
In Volume Control, go Edit>Preferences and see what you guys have 'checked' or 'unchecked' in there! Hopefully, it'll do it.

---

### Post by jinxed on 2006-04-16
To those of you who don't see the option for enabling Mic Boost in GMix (or other apps), try using alsamixergui. I found that in GMix, there was no option for enabling the Mic Boost, but in alsamixergui, the option does exist. The volume still seems a little low, but is 10x better now.:-|

---

### Post by PosTi85 on 2006-11-20
I still have the same problem XD, yes, in edgy... Any solution?

---

### Post by strabes on 2006-11-20
```
sudo apt-get install gnome-alsamixer
gnome-alsamixer
```

you should be able to adjust the input volumes of your input sources. hope this helps.

---

### Post by ArtInvent on 2007-04-02
First, why on earth is gnome-alsamixer not a standard default Ubuntu package? I mean, pretty much everyone needs to be able to adjust their mic and other input levels. All we get by default is the output levels, no inputs. Okay.

Now to the problem at hand, my mic works but the level is low. This is a typical problem for some reason on many many audio systems and sound cards, the mic preamps are completely wimpy and the level of any standard mic will be too low. Now, whether there is a way to boost the mic level, which is to say, adjust the gain, seems to be a function of the particular sound card. In alsamixer, the mic boost switch is there for some users, and for others it's just not. I have used both the command line alsamixer as well as the gnome-alsamixer and the switch or slider is simply not there for me. I have onboard 7.1 sound with an Asus motherboard, "Analog Devices AD1986A." 

In short, simply telling people to install alsamixer or open it, is not going to solve this problem in these cases.

If there is any way to get the mic boost switch to magically appear, then I would like to know.

---

### Post by ArtInvent on 2007-04-02
I will say that another work-around is to buy a cheap mic preamp. You plug the mic into this box, and then plug this into a LINE IN jack rather than the MIC jack. The preamp will turn the tiny mic signal into a stand line level signal, and it will sound very good. You will get plenty of volume this way. You might also try plugging this into the MIC in if your line in is occupied, but be careful, the level will be very hot and distorted, you will have to turn it way down in the software mixer. A lot of sound cards also are able to switch a jack from LINE IN to MIC functionality.

I got a cheap mic preamp/mixer box at Radio Shack years ago. Now I'm pretty much soundcard-idiocy proof.

---

### Post by spegru on 2007-06-13
My 20dB Mic Boost button is also missing.  I am using nVidia HDA
This seesm to ba a common problem for a long time with HDA



I think am using the latest Alsa drivers (1.0.14) and Kubuntu 7.04

I tried alsamixer and it does not help - there is still no Mic Boost button

By the way how can I check thatt the correct drivers are being used?

Is there a way to config the boost on in one of the setup files?

rgds
spegru

---

### Post by spegru on 2007-06-17
Still making no useful progress on this.
I read many threads on the issue,  reverted to the older alsa 1.0.13 drivers and gone back to 1.0.14 again.

One iinteresting thing though is that out of desperation I installed another sound card (SB Audigy LS).
KMix now gives me the option of controls for each of the two cards.

But guess what, Mic Boost is missing for both sound cards!!

Is this a bug in the newer Alsa drivers???

Any opinions?

rgds

spegru

---

### Post by jrz on 2007-10-27
Same problem here, installed the latest ALSA 1.0.15, and still no mike boost, and very low record level. If anyone has found a solution or fix for this please post it here.
Thanks

---

### Post by Chymera on 2007-10-27
Yep, same here, ALSA seems to have topped everything else in the fine art of blowing....
I have to hold the mic 2mm from my teeth in so that ppl on the other end may hear something (and yes, i have boost torned on, all sliders to the max)... oh, and yes, this only works if the person i'm talking to has his speakers turned at max...

---

### Post by jrz on 2007-10-28
Yesterday we noticed that the mixer controls related to both the internal and the external microphones has no effect at all. Even with the sliders at minimum we get the same record level from the microphones. The Master volume control does work however, and we are now curious if the solution to the problem may reside in a configuration file somewhere? Another possibility is that we need to make use of some unknown option when installing ALSA, but not being Linux aware, I'm uncertain of where to look and what to look for. We've also tried asking for help on the #ALSA irc site, but have not received any response to date. If anyone finds a solution, please post it here, and we will do the same should we achieve success.

---

### Post by galleonway on 2007-10-28
> **anil_robo said:**
> 1. Test your mike with another PC and another OS. The fault may be in the mike itself.
2. Double click the volume icon in the system tray. Open up Edit-->Preferences. Tick "capture" and you would then see the capture sliders. Make sure you set the "microphone" and "capture" sliders to maximum.
 
Let me know.

Worked for me. Using Realtek ALC560E on board audio. First time my mike has worked in linux!

---

### Post by jrz on 2007-10-29
Thanks, but those suggestions have been given and eliminated many months ago. Our problem is being narrowed but still awaiting a solution. The hardware, in our opinion has been eliminated through extensive testing and it appears the answer is to be found only in software, ALSA in particular. We have tried 4 versions of ALSA to date and the last 3 have enabled the microphone to record, but the volume is insufficient. The mixer controls for the microphone have no effect at all. The sliders can be set to any position and the record level remains the same, although the Master volume control does work. We have a fairly new computer and it may be our hardware has not been made fully compatible with ALSA, using a Compaq Presario V3042AU notebook, which has Nvidia shown for the Audio, using a Connexant CX20549 codec which we find mentioned in many problem posts when googling, although no solutions included.
We've also tried the ALSA irc #alsa, and received help, but no solutions there either. The vumeter barely moves when recording, and under WindowsXP we have to reduce the microphone level to eliminate feedback. 
I'm also uncertain if there might be some options necessary that we are unaware of when installing the alsa-drivers and entering the ./.configure command? 
Others have suggested we check the 20 DB mike boost box in the alsa mixer, but we have no such box and have been unable to find a way to get it to display.

---

### Post by pjalegria on 2007-12-02
I have the same problem, why they dont fix that???

---

