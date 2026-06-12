---
title: "Sound volume of M1330 is too small?"
date: 2007-11-23
forum: Dell  Ubuntu Support
---

### Post by levis on 2007-11-23
The sound volume of my M1330 in ubuntu is too smaller then in Vista. Does some body know how to increase it's volume? :guitar:

And i can not install the fix to make the internal microphone to work. Does somebody successfully made the internal microphone  of M1330 work? :confused:

---

### Post by jdelaros1 on 2007-11-24
See [https://bugs.launchpad.net/dell/+bug/163360](https://bugs.launchpad.net/dell/+bug/163360)

---

### Post by levis on 2007-11-25
Thanks for the answer but it does not work for me :(

---

### Post by ninocass on 2007-12-10
> **levis said:**
> Thanks for the answer but it does not work for me :(

also having this issue and im unable to find a solution

---

### Post by animamia on 2008-04-06
me too :(

---

### Post by sdennie on 2008-04-06
You could try updating to the latest alsa drivers ([http://www.alsa-project.org/main/index.php/Main_Page](http://www.alsa-project.org/main/index.php/Main_Page)).  I don't think upgrading to the Hardy kernel will work at the moment (I have no sound on my XPS m1330 with the default Hardy kernel) but, upgrading alsa-drivers to the latest version gives me decent sound output and the builtin mic works just fine.

---

### Post by nightfrost on 2008-05-11
With the latest alsa, do you mean 1.0.16? Isn't that the version in the current Hardy kernel?

I'm also having issues with the m1330's internal mic - volume is way too low.

EDIT: Yep, cat /proc/asound/version gives:

```
Advanced Linux Sound Architecture Driver Version 1.0.16.
Compiled on May  6 2008 for kernel 2.6.24-17-generic (SMP).
```

And I still have problem with very low volume on the internal microphone. Seems like nobody else is having this problem anymore. Is it possibly a hardware problem I've stumbled upon?

---

### Post by oasis on 2008-05-12
Also adjust the 'Front' volume level in the mixer.

---

### Post by nightfrost on 2008-05-13
> **oasis said:**
> Also adjust the 'Front' volume level in the mixer.

I've enabled every controler available in the mixer and maxed everything. Still, the volume is very very low when recording with the internal mic. I don't have Windows installed so I can't easily compare and make sure it is a hardware issue. That's why I'm wondering, am I the only one left with this problem?

---

### Post by ninocass on 2008-05-14
I can confirm that i still have this issue, your not alone :)

---

### Post by nightfrost on 2008-05-15
> **ninocass said:**
> I can confirm that i still have this issue, your not alone :)

Ah, good to know (though sad to hear) :-)

I wonder, has anyone tried OSSv4 (which allegedly solves all problems on this earth) as a remedy for the low-mic issue?

---

### Post by ninocass on 2008-05-19
I got it workingggggggggg!!!!!!!!!!!!!!!!!1

Not exactly sure how i got it working tho!

i installed ossv4 and totally fudged my system and spend a few hours getting alsa installed.

i ran this script

[http://www.schugy.de/forenlinks/alsaconf](http://www.schugy.de/forenlinks/alsaconf)

and it seems to have my volume working working the full range 0% to 100% opposed to the original 50% to 100% 

w00000p

---

### Post by ninocass on 2008-05-23
dont know what ive done but my sound is only working between the 50% and 100% range.

ive ran the alsaconf script again but no  change!

help!!

---

### Post by nightfrost on 2008-05-24
Here's something that might help: [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/198453/comments/77](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/198453/comments/77)

I haven't had time to try it out myself...

---

### Post by nightfrost on 2008-05-25
I have this working now!

I don't know if both of these steps are required:
1) I recompiled libasound2 and libasound2-plugins from debian unstable's source debs.
2) I opened gstreamer-properties and changed sound input to ALSA. I think the problem previously was that sound input was going through pulse.

---

