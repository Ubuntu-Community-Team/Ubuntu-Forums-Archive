---
title: "Ddell Inspiron 1720, Ubuntu with Skype &amp; Mic problem please......"
date: 2008-10-20
forum: Dell Ubuntu Support (CLOSED)
---

### Post by liviococcia on 2008-10-20
Hello Members, as you can see from the threads title, i've set up my Dell laptop to duel boot OS, so i've got Viista/Ubuntu running, the Ubuntu version i'm using is 8.10 (i realise this is still in beta, but i gather it will be ratified soon).

Eveything seems to be running so far well, other than Skype from what i can tell, i seem to be able to hear the caller only through the left headphone but i do hear them clearly,  a larger problem, is  my internal Microphone (above the screen) is picking up sound at a very low level, and the funny thing is, when i do the Skype echo test and actually scratch over the top of the Mic's little holes, the one on the left side of the webcam picks up louder than the right side.

I have checked the settings in Alsamixer, and the device i'm using is 'HDA Alsa mixer device', i've given ths Sigmatel device a go, with the same result.

The 'device input' is set to 'Digital mic 1 in the 'options' tab , and on the 'Recording' tab the 'Capture' sliders are set to full, the speaker icon's under them is clear, but the microphone icon has a red cross over it, which won't come off.

Mux & Mx1, there sliders are completely flat, again the speaker icon is clear, but the mic icon again has a red cross over them, which again will not come off.

On the 'switches' tab 'IEC958' is ticked, 'IEC958 default PCM' is unticked, 'analog loopback' is unticked.

On the 'playback' tab 'Master' 'PCM' and 'Front' sliders are at full, nothing is muted (no red crosses.

I am not experiencing any issues with the sound or the microphone in Skype when in Vista, am i possibly missing specific special drivers (packages) for this particular Dell model of laptop?, or are my setting incorrect in some way?

Also, normal sound playback through a website, or by other means when in Ubuntu has no problems, i get sound through both headphone ear buds, at equal volumes.

 
Any help would be very grateful.

regards

Livio

---

### Post by liviococcia on 2008-10-20
Just to let members no, i've just had some updates downloaded by the updater service, and notice there were alot of Pulseaudio updates, i then changes my sound out setting in Skype to Pulse, and now i seem to have sound out of both headphone ear buds.

Now, i still have the problem of very little recording level, i have to go right up to the inbuilt mic on the laptop for the person i'm calling to hear.

I've also noticed, if i go to the terminal and type 'sudo alsamixer', the mixer states Pulseaudio for 'Playback' and 'Capture', i did try every kind of change under my volume control setting, picking different playback, capture devices, none of the changes made any difference to the mic level.

Does anyone have the solution to this problem, if they do, i'd really be grateful for there help.

regards

---

### Post by liviococcia on 2008-10-21
> **liviococcia said:**
> Just to let members no, i've just had some updates downloaded by the updater service, and notice there were alot of Pulseaudio updates, i then changes my sound out setting in Skype to Pulse, and now i seem to have sound out of both headphone ear buds.

Now, i still have the problem of very little recording level, i have to go right up to the inbuilt mic on the laptop for the person i'm calling to hear.

I've also noticed, if i go to the terminal and type 'sudo alsamixer', the mixer states Pulseaudio for 'Playback' and 'Capture', i did try every kind of change under my volume control setting, picking different playback, capture devices, none of the changes made any difference to the mic level.

Does anyone have the solution to this problem, if they do, i'd really be grateful for there help.

regards

Just trying to keep this thread alive, and hoping someone will have a solution to my Mic problem???

thanks

---

### Post by bramvanvliet on 2009-03-25
I have the same laptop with the same problem with skype!
Did anyone find a solution already?

---

### Post by Mcavity on 2009-03-25
Ok well I also have a 1720 and thanks to this post I was able to get the mic turned on. thanks! [I didnt know about digital input source] the volume level is still low. I'm thinking the gain is not enabled. but I want to try booting into windows and seeing what happens if i set it there. [maybe the default will carry over?]

---

### Post by tbastian on 2009-03-27
Try opening your volume control and turning up the mic boost or even mic volume if you haven't already. You can open the control by right clicking on the volume icon on the menubar. If mic boost isn't on the list, select preferences, and there should be a list of visible channels and you can select mic boost then go back to the controller and adjust the level.

I hope it works, 'cause thats about all I've got...

---

### Post by Mcavity on 2009-04-26
nope mic boost is not on the list. 
Its a bit annoying that I havent been able to figure this one out.

---

### Post by PhrygianCat on 2009-04-26
I fixed mine by installing pulseaudio gnome 2.26 volume controller. You can do that by running this command: sudo apt-get install gnome-volume-control-pulse. You'll see 2 applets running after the installation. Use the new one to adjust the mic volume.

---

### Post by ramzz on 2009-05-09
simple and efficient solution
thanks a lot
 
you're the boss :)

---

### Post by KrisBerg on 2009-05-10
Thanks alot, PhrygianCat ! Worked on my Dell Inspiron 1720 with Ubuntu Jaunty Jackalope.

---

### Post by riberet on 2009-05-11
I've just installed the same but cannot see 2 volume applets running. Any reason? I have ubuntu 9.04. Have I forgotten something ?

---

### Post by wil08son on 2009-05-11
^ Unfortunately I'm having the same problem.

---

### Post by riberet on 2009-05-11
Ok after logging off and back I can see the two appelets. I adjusted the i/p volume on the new applet but the same problem in skype. The gain is very weak. Could somebody give me their volume applet settings. I've done almost everything but cannot increase the gain.

---

