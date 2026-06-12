---
title: "Audacity audio init problems"
date: 2006-03-11
forum: Desktop Environments
---

### Post by bb002 on 2006-03-11
I'm having problems with audacity and I'm positive it has nothing to do with audacity itself.


If i try to start Audacity from the gnome menu it displays a "Unable to initalize audio i/o layer. you will not be able to play/record audio." error but if i start it from a terminal all goes well.

I've disabled Gnome's sound server since I have similar issues with totem with the sound server on.

I've checked the gnome shortcut for what it runs which is "audacity" i then did "which audacity" in a terminal and only got one item. Now I'm at a complete loss as for what could be up...any ideas?

---

### Post by bb002 on 2006-03-12
nvm. Got it working. Removed audacity with purge enable and reinstalled. That fixed it right up. Dunno what was wrong but it is fixed now.

---

### Post by shof2k on 2006-03-13
I had the same message and had to run it as root (yes i know v bad) to get it working.  Think this was related to permissions on /dev/dsp.  I will try reinstalling and see what happens.

---

### Post by OneSeventeen on 2006-03-13
I've noticed that I can only use sound in one place at a time.  Normally not an issue, but when using Audacity to record audio coming from another app, this can be very problematic.

If you disabled the gnome sound server, how do you still record with audacity?

---

### Post by bb002 on 2006-03-27
The gnome sound server is what makes all those nice sounds when you log in/out and click on menu items. It has nothing with your system's ability to produce or record sound.

By disabling the sound server your system will no longer produce the "thunk" when you select Audacity from the menu. Thus allowing Audacity to grap the sound card that would otherwise be in use by the Gnome sound server.

---

### Post by ts2000 on 2006-03-28
Why is audacity included in any linux distro when it doesn't work?  All 6 people I know who run and use linux can't get the damn thing going.  Really it's an interface without function.  What's the point?

---

### Post by Zimmer on 2006-03-28
Make that one more who DOES use Audacity with Ubuntu and find it works just fine..... you should meet more Linux users  ;)

---

### Post by arphe_el on 2006-03-29
is there any link which i can read on how to install the audacity?

also the procedures on how to record incoming audios like line in, stereo, mic etc. ?

any suggested link referrals I would appreciate it. thank you and GODspeed!

---

### Post by Zimmer on 2006-03-29
[QUOTE=arphe_el]is there any link which i can read on how to install the audacity?

also the procedures on how to record incoming audios like line in, stereo, mic etc. ?

any suggested link referrals I would appreciate it. thank you and GODspeed![/QUOTE]
Install through the Synaptic PAckage Manager.
Personally I have disabled Sounds for Events  through  System>Preferences>Sound
This allows Audacity to start without an error.
There is a thread on using multiple sounds at once, I may have tried that in the past and been unsuccessful, mainly because Audacity still uses OSS , I believe.
[http://www.ubuntuforums.org/showthread.php?t=101125](http://www.ubuntuforums.org/showthread.php?t=101125)
And...
[http://audacityteam.org/forum/](http://audacityteam.org/forum/)
[http://www.daniel.uklinux.net/tutorial/](http://www.daniel.uklinux.net/tutorial/)
are two links that may prove useful.

For recording ensure the Alsa mixer is set to allow capture from the device you are recording from (and mute the others,: )
Ensure you select the correct input device in Audacity...
I think that's enough for my letter to Phillipi  :)

---

### Post by Ramses de Norre on 2006-03-29
sudo apt-get install alsa-oss
aoss audacity & will then load audacity correctly (change the starter in the menu to this).

---

### Post by rykel on 2006-04-02
[QUOTE=Zimmer]... Personally I have disabled Sounds for Events  through  System>Preferences>Sound... [/QUOTE]

tat works for me!

i get exactly the same error right here in ubuntu dapper drake, and disabling the ESD seems like the fastest solution, altho' it always bewilder me why sounds in linux seem to conflict with each other frequently... alsa vs. oss vs. esd etc.

installing **alsa-oss** and running "**aoss audacity**" did the trick too, but with those cryptic messages in my terminal, i decided tat starting audacity without the ESD system sounds seems to be safest.   :rolleyes: 

hope this issue can be solved out, since audacity is a great piece of tool!

---

### Post by AdotB on 2006-04-09
[QUOTE=Ramses de Norre]sudo apt-get install alsa-oss
aoss audacity & will then load audacity correctly (change the starter in the menu to this).[/QUOTE]

Hey that solved my problem. I was having the same issue and was trying to compile audacity from source and see if that would fix it, but I failed.  Thanks !

---

### Post by ronmarley1 on 2006-04-10
[QUOTE=ts2000]Why is audacity included in any linux distro when it doesn't work?  All 6 people I know who run and use linux can't get the damn thing going.  Really it's an interface without function.  What's the point?[/QUOTE]

Runs just fine for me.  After adding the LAME codec, I can't imagine creating a podcast with out it.

---

### Post by Ramses de Norre on 2006-04-10
I thought I had it fixed but I get a new error now.. When I click on record I get > Error while opening sound device. Please check the input device settings and the project sample rate.
The only available input device in the drop down box is /dev/dsp and changing the sample rate doesn't change anything.
Anyone an idea?

---

### Post by AdotB on 2006-04-10
Oops, I spoke too soon. audacity starts but I can't record. 

[QUOTE=Ramses de Norre]I thought I had it fixed but I get a new error now.. When I click on record I get 
The only available input device in the drop down box is /dev/dsp and changing the sample rate doesn't change anything.[/QUOTE]

I have this same problem now.

---

### Post by Zimmer on 2006-04-11
The device selection box in Audacity should produce a list of Vol Line Mic CD Phonein etc.
Try launching the Volume control and going to the Capture tab and enabling capture (it is the furthest slider to the right..on this machine, anyway).

---

