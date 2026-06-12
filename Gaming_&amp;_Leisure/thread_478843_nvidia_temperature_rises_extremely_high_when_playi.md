---
title: "nvidia temperature rises extremely high when playing ut2004"
date: 2007-06-19
forum: Gaming &amp; Leisure
---

### Post by Cubicegg on 2007-06-19
when playing ut2004 on my laptop under ubuntu the temperature of the nvidia gpu rises extremely quickly. it has on one occasion reached 105degrees which resulted in ubuntu shutting down the machine (i got the criticial temperature message).

under xp it works fine.

does any body have any ideas please?

thanks James

---

### Post by jusmurph on 2007-06-19
Play in the freezer?


Seriously though,
Have you tried turning down the graphics? Updating drivers? You may also want to look into one of those laptop coolers if your going to be gaming on the laptop.

---

### Post by orb9220 on 2007-06-20
> one occasion reached 105degrees is that celsius?

which is 221 F.

---

### Post by eiskalt on 2007-06-20
what model is the card?

---

### Post by Motoxrdude on 2007-06-20
When playing games, suspend your laptop for better cooling, maybe even putting a house fan nearby. Just put some blocks under your laptop to add airflow. Im pretty sure that you will get the same temps in xp, but xp doesn't have anything to protect against temperature damage. Maybe invest in a laptop cooler as well.

---

### Post by Cappy on 2007-06-20
Yes, but I think he is saying his GPU fan (or maybe another one) isn't coming on while he is playing in Ubuntu but it does in XP.

---

### Post by ShadowFlar3 on 2007-06-20
I have brand new Asus F3T laptop and when I tried Feisty on it, I had similar problems. Nvidia-settings showed the VGA temp as 75 idle and when I ran glxgears for some time they went up to 90ish. Also my dual core temps were being reported as 62 and 75 when running glxgears. So I just used recovery and installed Vista back and it never reports temperatures higher than VGA 45 and core >70 (core temp measured with speedfan, asus software just says core temp is "ok") even when after many hours of gaming. (HL2, and FEAR)

I was told it's just that ubuntu reads the temperatures wrong, and I could believe it since the laptop feels equally warm on both Vista and Ubuntu. But I didn't actually try any games on Ubuntu, nvidia-settings has critical temp of 110 degrees, and if it reaches that I think I'm in for the same thing that happens to you, regardelss on whether the temperatures are read correctly or not.

My graphics card is nvidia Geforce go 7600, CPU AMD Turion 64 x 2 TL-52 @ 1600 Mhz, all the temperatures are (unfortunately) in celcius degrees.

---

### Post by Cubicegg on 2007-06-21
i think this might just be a feisty issue. i installed sabyson linux last night on the laptop and it worked like a treat..........

---

