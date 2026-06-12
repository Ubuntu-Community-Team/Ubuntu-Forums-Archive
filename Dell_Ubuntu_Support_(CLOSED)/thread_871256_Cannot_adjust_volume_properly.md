---
title: "Cannot adjust volume properly"
date: 2008-07-26
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Tsarj on 2008-07-26
When I try to drop the volume a little bit, it will not. I put in the Live CD and volume adjustment worked fine. The Device under Default Mixer Tracks was ALSA. Now it is Conexant HSF... Anyone know how I can switch that to see if that resolves my problem??

---

### Post by stepdown on 2008-07-27
If you double click the volume icon in the taskbar then you should be able to change back to ALSA mixer by looking under File > Change Device :)

---

### Post by Tsarj on 2008-07-27
I wish... But like I said, Conexant is the only one available... I cannot select ALSA or any other one for that matter. Video to come...

---

### Post by Tsarj on 2008-07-28
No video... But I did take a screenshot. Below.

[http://img507.imageshack.us/my.php?image=soundissueimagerz5.png]("http://img507.imageshack.us/my.php?image=soundissueimagerz5.png")

---

### Post by ms_whosit on 2008-07-30
I have a similar problem. (Gutsy, on an Inspiron 1525). I first noticed that I wasn't able to adjust the volume properly, as you said, and then noticed that the gnome-volume-control was Conexant HSF (OSS) instead of Alsa as it used to be. 

I tried to launch Alsamixer from the command line and got:
$ alsamixer
ALSA lib simple_none.c:1710: (simple_add1) helem (MIXER,'Master Playback Volume',0,2,0) appears twice or more

alsamixer: function snd_mixer_load failed: Invalid argument

I assume that the sound now goes through HSF because Alsa is broken. I also discovered that I cannot use the mic. 

I tracked the problem back to a kernel update a few weeks ago (from 2.6.22.14 to 2.6.22.15)---when I boot in the old kernel, everything works as before (alsa and microphone).

I am a newbie so I'm not sure how to fix it. I am afraid of trying anything lest I break it under the old kernel also.

---

### Post by Tsarj on 2008-07-30
Well now, I never noticed that. I think how we can fix it is by logging in to Ubuntu on the 14 generic kernel and saving the asound.state file in /tmp folder. And then restoring the alsa asound.state file. I'll try it after my lunch is over and get back to you.

---

### Post by secristrc on 2008-08-18
Did you ever resolve your volume issue?  I think I have the same problem on my 1525.

Thanks,
rcs

---

### Post by Tsarj on 2008-08-19
I simply stopped using the kernel with the 15 in it and used the one with 14. No problems whatsoever... haha.

---

### Post by secristrc on 2008-08-21
This worked for me too -- thanks!  

A couple of caveats for others.  For whatever reason on my 1525n, it also quit letting me login to X-Windows.  I did the reinstall, told Ubuntu Updates to update everything (not just important security fixes), and told it to update with all known patches as of 8/20/2008, and neither the -14 or -15 kernel boots had a working volume control (but now I COULD login).  I reinstalled again, and left Ubuntu Updates at just "important security fixes," at -15 still broke the volume control, but as Tsarj said, the -14 kernel still works (yay!).  Now I need to set -14 to default.

Thanks again, Tsarj!

rcs

---

### Post by fsmithred on 2008-08-22
I can confirm this on a friend's Dell laptop (1525n) with Gutsy. She did an update a couple weeks ago but didn't reboot until yesterday, resulting in several errors (including no sound).

Intel HDA got changed to Conexant in the sound controls, but lsmod showed that snd_intel_hda was loaded.
Gnome mixer and kmix lost a bunch of channels that they had before.
Alsamixer wouldn't start, and spit out this error message:
```
 :~$ ALSA lib simple_none.c:1710:(simple_add1) helem
(MIXER,'Master Playback Volume',0,2,0) appears twice or more

alsamixer: function snd_mixer_load failed: Invalid argument
```


Changing back to the -14 kernel (2.6.22-14-generic) corrected the problems.

---

### Post by reddcroww on 2008-08-22
I'm the friend with the inspiron 1525n. 

More about what was not working after the update to -15 kernel:

Sound could be turned on by using gnome-volume-control, but that didn't show all the channels that used to be there.

Kmix had no tab for input and no tab for switches, it had only the output tab, and in that were only:
Volume
lGain
Digital1

After the sound was turned on, then using the kmix volume control resulted in the volume control first sticking, then going to zero and staying there (slider quit working), requiring the volume to be turned back on again, using gnome-volume-control.

Also, mic jack didn't work any more after the update. Audio was present in headset, but no mic.

---

### Post by Andy D on 2008-10-03
> **ms_whosit said:**
> I have a similar problem. (Gutsy, on an Inspiron 1525). I first noticed that I wasn't able to adjust the volume properly, as you said, and then noticed that the gnome-volume-control was Conexant HSF (OSS) instead of Alsa as it used to be. 

I tried to launch Alsamixer from the command line and got:
$ alsamixer
ALSA lib simple_none.c:1710: (simple_add1) helem (MIXER,'Master Playback Volume',0,2,0) appears twice or more

alsamixer: function snd_mixer_load failed: Invalid argument

I assume that the sound now goes through HSF because Alsa is broken. I also discovered that I cannot use the mic. 

I tracked the problem back to a kernel update a few weeks ago (from 2.6.22.14 to 2.6.22.15)---when I boot in the old kernel, everything works as before (alsa and microphone).

I am a newbie so I'm not sure how to fix it. I am afraid of trying anything lest I break it under the old kernel also.

I have exactly the same problem as this on my Gutsy 1525 - the volume adjusters on the keyboard stopped working which was how I first noticed it. I've just tried booting up with the -14 kernel and the sound seems to be OK now. Thanks for your post ms_whosit, I've been looking for the cause of the problem for some time.

> **secristrc said:**
> 
Now I need to set -14 to default.


How do I do that? Or is there another solution?

---

### Post by Andy D on 2008-10-03
> 
How do I do that? Or is there another solution? 


Don't worry about the first question, I've found out that I need to edit the "default" value in /boot/grub/menu.lst 

I've done so and my 1525 now boots into 2.6.22-14 by default.

I'd still like to know if there's another solution though.

---

