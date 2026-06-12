---
title: "How to resume after suspend?"
date: 2005-11-30
forum: Desktop Environments
---

### Post by andy80 on 2005-11-30
Hello,

sometimes, usually when my notebook is using battery, and I'm not using it, it automatically suspends itself to ram.

At this point I canot resume the system and all I can do is to keep power button pressed and power off the notebook, then power on again.

This thing happens since I use Ubuntu 5.04, now with 5.10 is still present. I tried to submit this bug a lot of times but no one has fixed it yet.

My notebook is a Toshiba Satellite M30-742.

Anyone please can tell me how to resume my system after a suspend to ram?

Thanks!

---

### Post by anil_robo on 2005-11-30
I tried the same on my laptop by the following steps:

System-->LOgout-->SUspend the computer

The conputer suspends.

Then I tried all the keys, and mouse movements and clicks etc. but nothing worked. However, when I pressed the power button of laptop "once", the password propmpt appeared. I entered my password and was taken back to the session.

However, since I saw some garbled characters momentarily during re-logging in, I suppose there can be a problem with the display drivers on some machines.

MY recommendation: SUspend your computer by the same method as I did (listed above) and when your computer is totally suspended, press the power button once. You should get a password prompt. If you don't, please post your experiences in this thread and let's see what can we do!

Oh by the way, I lost my internet connection after resuming from suspension ;)

Good luck! :)

---

### Post by Rob2687 on 2005-11-30
It should resume from suspend to RAM when you open your laptop screen. So when the lid switch is triggered. And your network is just a matter of setting up the scripts right. (Which I haven't figured out to do yet)

---

### Post by andy80 on 2005-12-01
Suspend to disk doesn't work for me.

When I suspend to disk, the next time I press Power button I see that Ubuntu try to resume from disk to my ram, showing a progress bar.

Then it tries to load the system. At this point I hear a BEEP and the screen is BLACK!

I cannot do anything :(

The other thing works for me: if I close the notebook the open it again I'm prompted to enter my password, but I don't know if this is a real suspend to ram.

Fn+F3 (suspend to ram) do nothing, Fn+F4 (suspend to disk) really suspend my notebook (even if I cannot resume).

The question is: when I use battery and I don't use my PC what does ubuntu? Does it suspend to ram or to disk?

---

### Post by anil_robo on 2005-12-01
I'm a noob, just trying to apply my "intuition" to your problem. Please also consult someone more experienced.

Open a text editor, and type something. DOn't save the file.

Now close your laptop lid, disconnect it from power supply. The battery will start draining. Now go out of your room, play a squash game or whatever, and come back. The laptop battery would have discharged completely.

Reconnect the laptop to AC, let it charge for 10 mins. Now open the laptop cover, and boot in Ubuntu. If you're able to see the unsaved file, I guess Ubuntu saved changes to your hard disk. If there's no trace of that file, I guess Ubuntu saved changes to RAM only, that's why it lost them after battery depletion.

Others please comment.

---

