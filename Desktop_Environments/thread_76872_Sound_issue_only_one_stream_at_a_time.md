---
title: "Sound issue: only one stream at a time"
date: 2005-10-15
forum: Desktop Environments
---

### Post by skyhorse on 2005-10-15
Hi,

I have a strange issue, I am only able to listen to one stream at a time.
If I am listening to an mp3 , no other sounds play.

I have checked the mixing panels, and it all looks ok, I don't know if there are any special options I should be tweaking.


I searched in several places but couldn't come up with a solution.

I have tried using ALSA, OSS and ESD (in the multimedia selector), all have the same results.

this is my esd.conf:

skyhorse@skybuntu:~$ cat /etc/esound/esd.conf
[esd]
auto_spawn=1
spawn_options=-terminate -nobeeps -as 2 -d default
spawn_wait_ms=100
# default options are used in spawned and non-spawned mode
default_options=


Any ideas?

---

### Post by skyhorse on 2005-10-17
Anyone?

---

### Post by tjabri on 2005-10-17
I'm no expert man, but from all I've read, you might want to try ALSA, as it seems to be better overall.

---

### Post by skyhorse on 2005-10-17
ok, I just found the problem, and the solution.

I am running some applications that use the SDL library (NeverWinter Nights being one of them) and I only had the SDL library with OSS support, so they were all trying to run with OSS while everything else, like my MP3's, were using ALSA.

I have now put everything running with ESD and it works fine.

I have also tried to put all running with ALSA but I find it is a *lot* slower to respond, especially inside NeverWinter Nights.

Thanks for the help though!

cheers,

sky

---

### Post by Stormy Eyes on 2005-10-17
Skyhorse, what sort of sound card do you have? Some don't implement mixing in hardware, but require special drivers.

---

### Post by BRODEL on 2005-10-18
I found this thread after doing a search. I have no where near the experience with linux that skyhorse obviously does, but my issues seems similar. I installed xmms and while playing my tunes I get no sounds when someone IMs me on GAIM or any other sounds from any other program. 

Since I have no idea what he did to fix his issue, I was wondering if someone could help me out a bit here. 

I am running breezy on a Toshiba Satellite laptop. Thanks.

---

### Post by anil_robo on 2005-10-19
Same problem here :( I missed so many conversations on GAIM while I was listening to music and reading newspaper :confused: . I also tried changing  the sound card : Double click the sound icon in system tray, click file, click change device, and choose a different device. The device got changed successfully, but even then I continue to have the same problem. I tried to find some information about this in this forum, but couldn't reach anywhere :(

---

### Post by anil_robo on 2005-12-04
How to enable playing more than one sound at a time:
[http://ubuntuforums.org/showthread.php?t=32063](http://ubuntuforums.org/showthread.php?t=32063)

ANd it worked for me! :)

---

