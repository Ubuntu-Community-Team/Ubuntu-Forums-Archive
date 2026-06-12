---
title: "Ubuntu Feisty on Optiplex 745 but no sound"
date: 2007-06-05
forum: Dell  Ubuntu Support
---

### Post by stephenb on 2007-06-05
I've had few problems with a duel boot system since installing Ubuntu on my new Dell Optiplex 745 a few months ago. There were some issues that required attention concerning video display, the ATI card and something called mtrr, but nothing that couldn't be fixed even with my limited knowledge. However, I've never had sound working. 

Does anyone have sound working with Ubuntu on an Optiplex 745? If not, does anyone know if support is on the way? 

Is there any alternative other than installing a sound card that is definitely Linux compatible? 

If installing another sound card is the only alternative, which one is recommended?

---

### Post by Crafty Kisses on 2007-06-06
> **stephenb said:**
> I've had few problems with a duel boot system since installing Ubuntu on my new Dell Optiplex 745 a few months ago. There were some issues that required attention concerning video display, the ATI card and something called mtrr, but nothing that couldn't be fixed even with my limited knowledge. However, I've never had sound working. 

Does anyone have sound working with Ubuntu on an Optiplex 745? If not, does anyone know if support is on the way? 

Is there any alternative other than installing a sound card that is definitely Linux compatible? 

If installing another sound card is the only alternative, which one is recommended?

Could be a lot of issues, drivers, codecs, it can be a lot of stuff. Try installing your drivers.

---

### Post by stephenb on 2007-06-07
OK, I've posted this elsewhere, but I'll put it here too since it's relevant.

Here's how I got sound working on my Optiplex 745

First of all, when I did sudo modprobe snd-hda-intel it didn't hang and when I did aplay -l I got the playback hardware devices listed. So everything seemed in order there. But I still couldn't get sound.

Then following this post:
[http://ubuntuforums.org/showpost.php?p=2515443&postcount=20](http://ubuntuforums.org/showpost.php?p=2515443&postcount=20)

I got a device in use error with sudo rmmod snd-hda-intel
No problem. Then I simply ran this command to see what would happen:

**sudo modprobe snd-hda-intel probe_mask=8 model=auto**

After that my sound worked.

It was recommend that this line be added at the end of the /etc/modprobe.d/alsa-base file and to a new file called /etc/modprobe.d/snd-hda-intel.modprobe:

**options snd-hda-intel probe_mask=8 model=auto**

The probe_mask=8 is to overcome a laptop modem issue. So, I didn't think I needed it when I added the recommended line at the end of my **/etc/modprobe.d/alsa-base** file, like this:

**options snd-hda-intel model=auto**

I didn't even need to create a /etc/modprobe.d/snd-hda-intel.modprobe file.

I just rebooted and heard the beating drums of Ubuntu for the first time on my Optiplex 745.

---

### Post by tgalati4 on 2007-06-07
It's a good feeling when the yoke of software repression is lifted from your shoulders.

---

