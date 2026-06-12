---
title: "Sound Card issue on XPS 1530"
date: 2008-03-17
forum: Dell  Ubuntu Support
---

### Post by Drenux on 2008-03-17
Hi Experts

Hope you are doing fine!

I am new using Ubuntu and new on this forum so I would like to apologize if my question is a repost.

I have the following issue; my 1530XPS was working fine with Ubuntu 7.10 except for the built-in microphone so I applied:

$ sudo dpkg -i linux-backports-modules-2.6.22-14-generic_2.6.22-14.50_i386.deb, and then reboot the PC and the microphone start working fine however my sound card stop working and now there is no Audio.

I already verify ALSA properties, output options and when I tried to test there is still no sound.

I would like to know if there is any workaround that I could apply, any assistance would be greatly appreciated.


Thanks in advance.

---

### Post by AMDATI on 2008-03-18
Which sound card do you get? High Definition Audio 2.0, Sound Blaster Audigy HD, or Sound Blaster X-Fi Xtreme?

---

### Post by Drenux on 2008-03-18
Hi Amdati, I forget to include that, it is High Definition Audio 2.0.

---

### Post by jdelaros1 on 2008-03-19
That custom backports package you installed from Dell was not meant for the XPS M1530, so it's unknown what the side-effects might be. It should just work, but be aware of unexpected behavior.

---

### Post by Drenux on 2008-03-20
Is there a way I can revert this?

---

### Post by sygram on 2008-03-20
i am not exactly sure how to do this ,  but is there anyone that knows if the microphone issue is going to be fixed in the future ? Is it submitted as a bug ?

We would really like this update ;)

Regards

---

### Post by arioch_yu on 2008-03-23
Unfortunately, I tried to do the same thing before seeing this post and now the sound on my XPS 1530 doesn't work. Can anyone suggest how to get at least the sound back? Thanks

---

### Post by sygram on 2008-03-30
i know that it sounds obvious but what if you uninstall all sound modules and put the back....

Perhaps alsa packages....

Leon

---

### Post by jespdj on 2008-03-31
Have a look at this to fix the XPS M1530 microphone problem: [HOWTO: XPS M1530 internal microphone](http://ubuntuforums.org/showthread.php?t=702642)

---

### Post by sygram on 2008-05-03
i think this issue involves fixing the internal microphone. I am connecting the microphone to the output next to the speakers but even that does not work. Does anyone have any idea how to make that mic input to work ?

Regards,

Leon

---

### Post by sygram on 2008-05-04
Small update.

I managed to get the mic working but with a lot of noise. I did not install any package . Opened the volume control and chose to view everything. I opened the Recording tab and enabled everything.
At the Switches tab i chose ADCMux.

I went to sound recorder and chose ADCMux input. Now i can record but with a LOT of noise. I tried to mute a few options but it seems that it is either that or nothing. Skype is working but has noise. The mic is working fine under windows.

Any ideas regarding noise ?

Regards,

Leonidas

---

