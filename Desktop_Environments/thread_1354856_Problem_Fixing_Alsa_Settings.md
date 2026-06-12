---
title: "Problem Fixing Alsa Settings"
date: 2009-12-14
forum: Desktop Environments
---

### Post by lukereimer on 2009-12-14
Hi there, 

After a kernel upgrade my sound was super-low volume, so I used some threads in the forum to play with my alsa settings to try and get it right. 

Now I have no sound, and my Ubuntu does not recognize any sound card hardware or drivers. 

I've tried to use: [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting) to get it back to normal, but my files do not contain the same information listed in that document. 

When trying to reset Alsa settings in the terminal, I get errors like "none loaded, none to reload". I just want sound! 

Is there any way to totally reset the sound card recognition and drivers as if it were a fresh install? 

Thanks
Luke
Ubuntu 9.10, Desktop

---

### Post by alexfish on 2009-12-14
Hi

Are you using 1: Pulse Audio

---

### Post by lukereimer on 2009-12-14
I'm not exactly sure what you mean (sorry, I'm a medium-level ubuntu user). 

In sound preferences, it shows no hardware for me to use (whereas before there was a piece of hardware listed that I could set up settings for).

---

### Post by alexfish on 2009-12-14
> **lukereimer said:**
> I'm not exactly sure what you mean (sorry, I'm a medium-level ubuntu user). 

In sound preferences, it shows no hardware for me to use (whereas before there was a piece of hardware listed that I could set up settings for).

Hi
 have a look here it will show you how to set up Pulse Audio The easy way  //But don't install any Video software yet

                         [5.1  Sound (Pulse Audio  Sound Server)  Ubuntu 9.10]("http://ubuntuforums.org/showthread.php?t=1353851")


  Then post me a private message  if you need help on that site //or help here if your sorted

alexfish

To send a private message click on my name to the left

---

### Post by lukereimer on 2009-12-14
Thanks Alexfish, but I already had the vlc-pulse plugin installed. I marked it for reinstallation, still nothing. 

Under my audio preferences, it shows nothing for hardware, and under output it says "Dummy Output (stereo)". 

Wouldn't any third-party (such as the pulse plugin) audio control programs still need recognition of the sound card hardware and its basic use? I believe that's what I'm still missing. 

Thanks so much, 
Luke

---

