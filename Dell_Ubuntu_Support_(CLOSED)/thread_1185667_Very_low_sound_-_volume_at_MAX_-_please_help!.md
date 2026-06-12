---
title: "Very low sound - volume at MAX - please help!"
date: 2009-06-12
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Acid Burn on 2009-06-12
Lads and lasses,

I've just bought an Inspiron 1545 and installed a dual boot with Windows 7 and Ubuntu.
Unfortunately, the sound in Ubuntu is very very low to say the least. The volume is set at the highest but it doesn't make much of a difference.

I'm new to Ubuntu, so I would appreciate and recommendations to how I solve the problem.

I have version 9.04 installed.

Sound level is fine under Windows 7.

Hope you can help - cheers.

---

### Post by Vostrocity on 2009-06-12
I have almost the same laptop as you and had the same problem. I don't know if there's a real fix, but all I did was open up Volume Control (right click volume icon) and crank up Master and Front. The simple volume bar only changes PCM.

---

### Post by uidb4056 on 2009-06-12
> **Acid Burn said:**
> Lads and lasses,

I've just bought an Inspiron 1545 and installed a dual boot with Windows 7 and Ubuntu.
Unfortunately, the sound in Ubuntu is very very low to say the least. The volume is set at the highest but it doesn't make much of a difference.

I'm new to Ubuntu, so I would appreciate and recommendations to how I solve the problem.

I have version 9.04 installed.

Sound level is fine under Windows 7.

Hope you can help - cheers.

Have you checked when open the Volume applet if in the Playback section the PCM level is up and no mute is selected?

---

### Post by Acid Burn on 2009-06-12
> **Vostrocity said:**
> I have almost the same laptop as you and had the same problem. I don't know if there's a real fix, but all I did was open up Volume Control (right click volume icon) and crank up Master and Front. The simple volume bar only changes PCM.

Cheers mate that improved it a bit ... but still not quite enough.

---

### Post by Vostrocity on 2009-06-12
Are Master, PCM, and Front all at max?

---

### Post by alekese on 2009-08-21
> **Vostrocity said:**
> Are Master, PCM, and Front all at max?

I have Jaunty on a Dell Vostro 1500 and have had the same low-volume problem and this did the trick for me.  I had to switch "devices" to HDA Intel, then it showed the 3 scroll bars, and "Front" was set 2/3 up while the other two were already at max.  For some reason raising it the remaining 1/3 made a huge difference, and I can actually hear now.

Thanks!

Alec
[http://alekese.com](http://alekese.com)

---

### Post by MartynT on 2009-08-23
I had the same problem but setting PCM to 100% from ~66%, within the Volume Control dialog, solved my problem.

---

### Post by RabbitWho on 2009-08-23
Same laptop, Inspiron 1545 with Vista. (How did you get 7!? Damn you that's not fair!) 
What i did was left click on the volume control, then go to mixer then turn up all the knobs on the screen you get. 

(I'm using kubuntu not ubuntu though)

---

