---
title: "sound not working"
date: 2014-12-29
forum: Debian
---

### Post by Hasan55 on 2014-12-29
hey guys plz help me .....

today i have install MX-14.3-pae.iso (anti x linux) but sound is not working...
my laptop sound card is damage so i use (GENRIC USB AUDIO MIXER )  USB SOUND CARD .it working i can here
my microphone sound but when i use it as headphone then i can not here media
play back sound such as mp3,mp4 etc. nothing sound happening....
HOW TO SET AUDIO OUT PUT ........

HOW TO FIX THIS SOUND PROBLEM .....THANKS

---

### Post by Holger_Gehrke on 2014-12-29
Have you checked the volume ? For all sound cards I've seen the mixer offers separate controls for the volume of the speakers and the headphones. So it might just be that the volume for the headphones is muted or set very low.

---

### Post by ajgreeny on 2014-12-29
^^ AS ABOVE ^^
Install pavucontrol if it is not already installed on your system and open it from the **Volume icon ->Sound Settings** in the panel to check that, and/or use alsamixer in terminal and check that the levels of outputs are not set too low.

Move from slider to slider, and raise and lower levels with the cursor keys;
Mute and unmute with the "M" key.
Tab will move you from "playback" to "capture".
Esc will save and exit.

---

### Post by Bucky Ball on 2014-12-29
*Thread moved to **Debian**.*

Please be aware that the main forum areas here are for support with Ubuntu and its flavours, Kubuntu, Xubuntu, Edubuntu, Lubuntu, UbuntuGnome, Ubuntu Studio, and Mythbuntu.

From its description [here]("http://sourceforge.net/projects/antix-linux/"), '_antiX is_ a fast, lightweight and easy to install linux live CD distribution_ based on Debian Testing _for Intel-AMD x86 compatible systems.'

While you are welcome to post in this sub-forum here, antix has its own forum [HERE]("http://antix.freeforums.org/"). 

Good luck. ;)

---

### Post by Hasan55 on 2014-12-29
hey ajgreeny thanks man after whole day useless effort finally your trick works .. ALLAH (GOD) bless you man. love your helpful work....
Keep doing help who are needy bye man god job.

---

### Post by ajgreeny on 2014-12-29
Great!
I didn't even notice it was Antix that you were using, not one of the *ubuntu family.

Was it the pavucontrol or alsamixer that did the trick; I suspect alsamixer was the solution, as I am not sure that pulseaudio is in Antix, but it would be good to know which did the trick.

---

### Post by Bucky Ball on 2014-12-29
> **ajgreeny said:**
> 
Was it the pavucontrol or alsamixer that did the trick; I suspect alsamixer was the solution, as I am not sure that pulseaudio is in Antix, but it would be good to know which did the trick.

Yes, please share the fix. ;)

---

