---
title: "PLEASE HELP - Still no sound"
date: 2009-03-11
forum: General Help
---

### Post by Saltwaterfishin on 2009-03-11
Hi all,

I was in a different thread, but seemed to have gotten abandoned by those who were trying to help.  I'm having problems with sound using Creative Labs sound blaster sb0090.  I think I've basically figured it out.  I do have test sounds now when I go to the sound settings screen.  I think that the problem now is that when I type "alsamixer" into the terminal it says that the chipset and card is PulseAudio and I only see one "master" volume controller instead of a "mixer" type controller.   I think I have to somehow set it to alsa...does this sound right?  If so, please show me the exact commands to type into terminal.  I'm a total newbie to Ubuntu.  You can also send a reply to [email]Saltwaterfishin@aol.com[/email].  (Just in case I can't find my way back here..

Thanks,

Jay

---

### Post by kostkon on 2009-03-12
I can see from your other thread that your card is recognised and that is an *Audigy* one.

The first thing you need to do is to check if you see an speaker icon in your system tray. If yes, right click on it and select *Open Volume Control*.

Then, select the *Switches* tab and make sure that the *Analog/Digital* switch is *disabled*. If it isn't, disable it yourself. Then, check if your sound is working.

Also, check your volume levels there and try to increase the levels of any volume that you find necessary.

If you want to use *alsamixer* for a more thorough access to your volume levels, you need to run it like this
```
alsamixer -Dhw
```

Also, the sound playbacks in your sound preferences (i.e. *System &#8594; Preferences &#8594; Sound*) must be set to Autodetect.

Hope that helps.

---

### Post by Saltwaterfishin on 2009-03-12
kostkon,

Thank you for your reply.  I tried what you said and I finally have music (after two weeks of working on the problem for a couple of hours nightly)!!!  YIPPEE YAHOO!!!  I can play a CD now, but still can't hear sounds from the internet (AOL radio, you tube).  Do you have any suggestions that might help fix this problem.  I also used the command [ sudo alsactl store 0 ] as suggested by another thread to try to save the settings for the alsa mixer.  I hope this is right.

Thanks a bunch,

Jay

---

### Post by ed-koala on 2009-03-12
Check preferences/applications in Firefox also to make sure your browser is using the proper "app" to play sounds like mp3 and others.

---

### Post by Nano_ext3 on 2009-03-12
Firefox should not be an issue.  As far as I know, there is no option like in a linux app to choose your sound driver source.  

You may want to go to your settings and to the "Sound" manager in Ubuntu (System > Preferences > Sound). The ALSA driver is known to work on many occasions where the real driver fails to work. This happened to me on my desktop, which is understandable as it is choc full of custom hardware. Change each entry on the main page of the sound editor to ALSA. You can test the output by hitting the test button. Change your driver if ALSA does not work, one of the drivers in each drop down should work, but you want to keep the same driver for all if you can.

Also install alsamixer as suggested above, it will greatly help you out.  Turn all levels up from alsa mixer.  The command to istall alsamixer is:

"sudo apt-get install gnome-alsamixer"


Cheers!

-Nano

---

### Post by kostkon on 2009-03-12
> **Saltwaterfishin said:**
> kostkon,

Thank you for your reply.  I tried what you said and I finally have music (after two weeks of working on the problem for a couple of hours nightly)!!!  YIPPEE YAHOO!!!  I can play a CD now, but still can't hear sounds from the internet (AOL radio, you tube).  Do you have any suggestions that might help fix this problem.  I also used the command [ sudo alsactl store 0 ] as suggested by another thread to try to save the settings for the alsa mixer.  I hope this is right.

Thanks a bunch,

Jay
OK, it seems that you have problems with Flash. What version of Ubuntu do you have? 8.04 or 8.10?

---

### Post by Saltwaterfishin on 2009-03-13
Hi Kostkon and everyone who is trying to help me,

Thanks again for helping solve my sound problem. I am using UBUNTU 8.10.  I've done all the updates that were recommended.  I've tried all the settings in system/preferences/sound and have them all set to "Audigy 1 [SB0900](rev.3, serial:Ox531102) Multichannel Playback (ALSA).

Autodetect did not have any sound with test button.
ALSA - Advanced LINUX Sound Architecture NO SOUND either
OSS - Open Sound System DOES have sound.  

I've tried all these options and still no sound from the internet.

Now what about Flash?  What can I do to fix it??  You may be right regarding the type of player that is running.  I DO get sound when using Rhythmbox Music Player but get NO sound using Alsaplayer

Thanks,

Jay

---

### Post by jamesdcarroll on 2009-03-14
> **kostkon said:**
> 
Then, select the *Switches* tab and make sure that the *Analog/Digital* switch is *disabled*. If it isn't, disable it yourself. Then, check if your sound is working.

I was having the same problem when I upgraded to 8.10 last night.  Just wanted to say 'Thanks!'

---

### Post by Digrgrl on 2009-03-14
Hi!

My sound quit working tonight (I know it was working earlier today), and now the only sounds coming out of my computer are when I log in. I know the sound card is recognized and that the speakers are working. I've fiddled with the volume, gotten GNOME-Alsa mixer, played with the settings in Sound Preferences--nothing seems to be working! 

I do remember doing some updates earlier today, but I could have sworn the sound was working after those. Help! I'm running 8.10 on an Acer Extensa 4420.

Thanks!

---

