---
title: "Problem with my sound card plug configuration on Dell Precision M4300"
date: 2007-08-07
forum: Dell  Ubuntu Support
---

### Post by moresun on 2007-08-07
Hi

I am running a Kubuntu 7.04 (2.6.20-16-generi) on my new Dell Precision M4300.
My sound card a Sigmatel 9205 is now driving me mad.
If I am using my headset under Windows XP the diver is asking me for the plug configuration like "Is there a microphone connected or is should the plug used as line out".
Under Linux there is (of course) no such pop up (and thats good) but the configuration is always wrong.
Sometimes (It depends which settings I used under windows) the speaker on my laptop are working and also the speaker of my headset. Or only the speaker on my headset even if I unplug the headset there is no sound on the laptop speakers.

I am searching now where or how can I setup the alsa driver used in such a way that my speakers are only working if my headset is not connected and the same also for the microphone.

I hope somebody knows a answer
Greetings
Max

PS.: There is my alsa configuration
[http://pastebin.ca/647810](http://pastebin.ca/647810)

---

### Post by JonathanWright on 2007-08-30
I have the same problem. It took a while to get started at all due to problems with the LiveCD (see another thread [1]), but those were fixed by going to gutsy. 
After some problem I finally got the nvidia driver from [www.nvidia.com](www.nvidia.com) and built it following their instructions, avoiding the ones from the repositories. Graphics are great - sound is not working. Will let you know if I make any progress.
Hoping an expert obtains on of these laptops before the gutsy final release is out.

-Jon

[1] [http://ubuntuforums.org/showthread.php?t=527105](http://ubuntuforums.org/showthread.php?t=527105)

---

### Post by zuffff on 2007-12-15
I have dell precision m4300 too.
I haved the same problem but I tryed 

sudo apt-get install linux-backports-modules-generic 

and it worked!!


[http://ubuntuforums.org/showthread.php?t=632748](http://ubuntuforums.org/showthread.php?t=632748)

thank you painejake!

---

