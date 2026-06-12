---
title: "Audio stopped working. I only get static now."
date: 2008-12-22
forum: General Help
---

### Post by Penks on 2008-12-22
After an update the audio stopped working in Ibex. When a sound is supposed to play I only get static. I went to Sound Preferences and changed playback from autodetect to Open Sound System and now it sort of works. I can now hear music on Rhythmbox or movie player, but still get static when trying to listen to Last.fm or a youtube video for example. Any ideas on how to fix this?

---

### Post by Penks on 2008-12-23
Anyone?

---

### Post by redilyn on 2008-12-23
Have you tryed ALSA??

Try going through each of the options and clicking test to see what works best for you.

Also make sure the proper sound device is selected.

---

### Post by Penks on 2008-12-23
> **redilyn said:**
> Have you tryed ALSA??

Try going through each of the options and clicking test to see what works best for you.

Also make sure the proper sound device is selected.

I've tried every option, and the only one that sort of works is OSS.

I've also tried selecting every device on the list, but it doesn't seem to make a difference.

---

### Post by redilyn on 2008-12-23
Your sound card dosn't happen to have a jack which is used for both digital out and analog??

My Audigy does and I have to uncheck a setting.

Open your volume control and look to see if there is a tab called "Switchs"

---

### Post by DanSearle on 2008-12-23
I had this problem today as well, so hoping its the same fix :).It seamed that the volume of PCM was 0 when I increased the volume of the PCM to the max setting (in volume control) the audio was back. Furthermore my sound preferences are set to Autodetect.

---

### Post by Penks on 2008-12-23
> **redilyn said:**
> Your sound card dosn't happen to have a jack which is used for both digital out and analog??

My Audigy does and I have to uncheck a setting.

Open your volume control and look to see if there is a tab called "Switchs"

It does have the Switches tab. If I change the device, it still does nothing.

The worst part is thet it used to work, until one of the automatic updates when I had to restart. After restart it stopped working.

---

### Post by redilyn on 2008-12-23
I hear ya.

I should have asked earlier. 

What sound card do you have?

Is it possible one of the updates was a kernel?

If so try rebooting and selecting an older kernel (press esc when you see the message about grub.), probably the second newest one.

---

### Post by Zorael on 2008-12-23
Well, you want it using ALSA. Have a look at [http://ubuntuforums.org/showthread.php?p=5017453](http://ubuntuforums.org/showthread.php?p=5017453) and see if anything applies. Perhaps it's autodetecting the wrong model and producing static instead of sound.

---

### Post by quasimodo69 on 2008-12-23
Hi Gang,
I have the same problem with the static on the audio.But here is the thing.I pulled the audio input to my KVM switch..and that is when it started.I have had no audio problems until this.It was not after an update..the unplugging for the headfones seemed to precipitate the problem.It has worked fine before.I pulled the plug to hook up some headphones.When I got through and plugged the speakers back in  the static started.When I change the KVM back to my windoze box (only for a game I play I assure you)the sound is fine.
I went through the audio setup and detect and changed to EVERY option...none worked or cured the problem.
Now here is the weird part...4 or 5 reboots later,the static did not start at bootup like it started doing.The static got quieter with each bootup.But it is still so bad I have to crank down my speakers manually to keep from shooting my 2 idiot boxes.It has finally got to the point I can turn up the volume and get some voices from my Ubuntu box..and the test options in the audio setup work fine...except the sound capture test-no matter what I change it to..it has a stutter in the sound test like it did not have before.The sound tests are good...except for this.
I am a noobie an would like to know how to troubleshoot this...GOD I don't want to do the re-install thingy like windoze!
If you can direct me as to how to work this out plz let me know.
 Thanks to the whole team for crawling this and helping us!
Rick

---

### Post by quasimodo69 on 2009-04-08
> **Zorael said:**
> Well, you want it using ALSA. Have a look at [http://ubuntuforums.org/showthread.php?p=5017453](http://ubuntuforums.org/showthread.php?p=5017453) and see if anything applies. Perhaps it's autodetecting the wrong model and producing static instead of sound.
Hey..I got this solved...the old fashioned way..the windoze way..I did a re-install..and it has been quiet ever since.
The only problem I have now is a passing static...sometimes like a growling-low level.
It beats the hell out of the problem I had.
  Seems the winoze way of a re-install works....at least for us noobies...
now how do you mark this as solved?Firts time I had to do this..
Thanks for all the responses to try to hyelp gang!!!

---

