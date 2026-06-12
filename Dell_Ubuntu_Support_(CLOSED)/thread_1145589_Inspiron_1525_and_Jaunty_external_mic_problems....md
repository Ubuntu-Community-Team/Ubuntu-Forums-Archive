---
title: "Inspiron 1525 and Jaunty: external mic problems..."
date: 2009-05-01
forum: Dell Ubuntu Support (CLOSED)
---

### Post by =E= on 2009-05-01
...and other weirdness.

My internal mic works fine.  The external (front mic) doesn't.  I did a clean install of Jaunty (twice) via USB key.  All the mixer settings have been triple checked.    Everything worked fine on Ubuntu 8.10.

lspci:

```
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)

```

Also, I noticed that there is no alsa-base file on either of the installations I did of Jaunty.

Skype works with the internal mic (not the external), and I hear out of only the left side.  When I play an mp3, I hear from both speakers.

The second external headphone jack doesn't work either.

I scoured the web and these forums, but I couldn't find a similar problem.  

Is there any way to get a copy of the alsa-base file?  I wonder how that did not get put there in the first place.  The only thing in the /etc/alsa directory is modprobe-post-install.d and the only thing in there is alsa-utils.

Thanks in advance.

---

### Post by chickendude1313 on 2009-05-15
In gnome-volume-control

under preferences, check a bunch of things and unmute them. I don't know why they default to being muted.

I believe you have to unmute center and LFE and some input stuff

---

### Post by ancow on 2009-05-25
Everything unmuted and set to capture. Tried every available input source. Nothing helped. (I'm using KDE 4.2.3 but everything else is the same as with the OP.)

I even tried a suggestion I found elsewhere adding "options snd-hda-intel model=dell-bios" to /etc/modprobe.d/alsa-base (@=E=: is that the one you were searching for?)

---

### Post by =E= on 2009-05-26
> **ancow said:**
> 
I even tried a suggestion I found elsewhere adding "options snd-hda-intel model=dell-bios" to /etc/modprobe.d/alsa-base (@=E=: is that the one you were searching for?)

Yeah, that was it.  I added that line too, but nothing worked.  I am wondering if it was the USB installation I did (clean install of the alternative ISO).  Seems few others are having this problem.

---

### Post by ancow on 2009-05-26
> **=E= said:**
> Seems few others are having this problem.

Or have noticed it... I at least do not use my external mic every day and the internal one works fine and is enough for Skype et al.

I have been using and upgrading the Ubuntu 8.04 that came pre-installed on my notebook. I doubt it has anything to do with the installation process - my external mic has never worked on this computer (Kubuntu 8.04 through 9.04).

I'd like to point out [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/315276](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/315276) (no fixes yet, though).

---

### Post by crfvendramini on 2009-05-26
About external mic I can confirm that simply doesn't work in my Inspiron 1525. Only the mic in both sides of the integrated webcam and the front mic between line input and SD card reader.

---

### Post by bobe84 on 2009-05-29
I'm also having troubles with dell 1525, i can't get external microphone working, and only i can use internal microphone near jacks...

---

### Post by ONEother on 2009-05-30
I can also confirm that the external mic input is not working.  The other two problems I have gotten around.

For the second external headphone output, the switch "swap center/lfe" (options tab) must be checked and both center and LFE (playback tab) must be unmuted.

For the second mic input (above screen, both sides of integrated webcam), "digital input source" (options tab) must be set to "digital mic 1" and input source must be "mic".

As far as the external mic -- it's probably some weird setting that nobody has stumbled upon, or some weird hardware issue.  Consider this a cry for help.  I had it working in 8.04, but after upgrade to 8.10 and 9.04... no more.  :-k

---

### Post by brendanpiater on 2009-06-02
I was struggling with the same thing on my new Studio XPS 16, I was tinkering around and activated "Analogue loopback", that worked for me.

Hope it works for you!

Cheers
B

---

### Post by ONEother on 2009-07-09
*Bump*

Still in the dark here.  Analogue loopback just plays the sound into the speakers, so no progress there. :confused::frown:](*,)

---

### Post by =E= on 2009-07-09
I gave up and went back to 8.04.  Everything seems to work fine.  I think 8.10 might work as well.

<rant mode on>
Why won't Dell make a special repository for the tweaks for their "Ubuntu ready" machines?  Why should I have to download an entire DVD?  I am in a third world country after all.  It would take decades to download.

But these Ubuntu-specific Dell machines should be tested before each Ubuntu is released.  Is it really that hard? 

I will probably never buy a Dell again.  It's absurd that the company is making a half-arsed effort to sling us their crappy unsupported products.  Worst thing is, I know Dell does not care.
<rant mode off>

---

### Post by bowsermail on 2009-07-10
Hi,

I had the same problem with the ext. mic. not working on my Dell Inspiron 1720. Considering you rolled back your OS I'm probably too late but anyway... 

The following solution worked for me:
[LIST]
[*]open volume control
[*]select the device "HDA Intel (Alsa mixer)"
[*]select preferences
[*]check the "digital input source" tab
[*]change "digital input source" to "Analog inputs"

**Note:** the "digital input source" mentioned above is different to that discussed earlier in this thread. I overlooked this workaround before because it was available in using other device selections and it did nothing. 

[/LIST]

This changed the input from the internal laptop mic to the external one plugged in from my headset.

Hope this helps,

Mark

---

### Post by jhofmann on 2009-08-11
I've been searching for several days now, so I want to post my results here.  This is the only thread I've found that actually understands the problem.  I have no solution to offer, and have tried everything suggested here and elsewhere.  

The next thing for me is to try a USB soundcard.  I shall post again to this thread if that works.  

I need to use a headset in a noisy environment to talk on internet phone, so it is important that some external mic jack works.

I'm using ubuntu 9.04 on Dell 1525.

Jim

---

### Post by ancow on 2009-08-11
> **jhofmann said:**
> I need to use a headset in a noisy environment to talk on internet phone, so it is important that some external mic jack works.

It's important whenever the laptop is on a table and the fan is running, which happens quite regularly when you use Skype with videochat. ;)

That said, does anybody know whether this is fixed in Karmic?

---

### Post by dansanti on 2009-08-18
fixed on karmic!!! :) cool!!!!

---

### Post by lemmyg on 2009-08-18
Hi, 
I have Dell Inspiron 1720, after kernel update 2.6.28.13, the problem was fixes. Now Skype works fine.

---

