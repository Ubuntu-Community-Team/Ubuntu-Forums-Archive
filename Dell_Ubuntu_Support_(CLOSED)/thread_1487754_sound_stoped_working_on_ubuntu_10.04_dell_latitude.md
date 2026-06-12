---
title: "sound stoped working on ubuntu 10.04 dell latitude d630"
date: 2010-05-19
forum: Dell Ubuntu Support (CLOSED)
---

### Post by aydee on 2010-05-19
sound stoped working on ubuntu 10.04 dell latitude d630
went to watch a movie and my volume buttens didn't work so I went to the sount applet in the notifacation area and the mute all button was unclickable and when I click on sound prefrances I get "Waiting for sound system to respond" no matter how I try to access it that is what I get!

Please Help

---

### Post by keithspg on 2010-06-08
Ditto. This worked very well under 9.10 even with the dock I use at work. Once, I got it confused and the audio would not be directed to the internal speakers, but a reboot under XP on the dock and all was back to normal and it worked up to when I loaded 10.04.

Under 10.04, I initially had the internal speakers working. Now, the microphone works, but I get no sound at all on any outputs: Internal speakers, Headphone jack, Headphone jack on the dock. I have it set to 'Analog Stereo Duplex' and have tried 'Analog Speakers', 'Analog Output', and 'Analog Headphones'. Please help, this is a reversion.

---

### Post by lsoros on 2010-06-08
I am having the same problem, also on the Dell Latitude D630. I didn't lose my sound - it was gone immediately after upgrade. When I go to System->Preferences->Sound, I get the "Waiting for sound system to respond" message.

---

### Post by noodles_x on 2010-06-20
Hey

I have d630, also.

Currently 9.10.

And decided to install 10.04

First I searched are there any problems,
and I found this thread :)

So, can someone with d630 tell me is this problem solved?

Thanks!

---

### Post by elewis on 2010-06-27
Here is a workaround I have been using:
Before shutting down, remove your .pulse directory. From a terminal: "cd ~", "rm -rf .pulse".
When re-starting sound should be working.
This is not a fix, however. I have to go through this procedure about once every 3-5 starts. There appears to be a bug in the startup scripts that corrupts part of the .pulse directory.
Good luck.

---

