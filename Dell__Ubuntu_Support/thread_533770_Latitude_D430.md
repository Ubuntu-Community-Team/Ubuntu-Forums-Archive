---
title: "Latitude D430?"
date: 2007-08-24
forum: Dell  Ubuntu Support
---

### Post by WhatToDo on 2007-08-24
My Company is going to buy me a laptop, and they only buy from Dell...

I want a tiny and lightweight machine that can dual boot XP and Ubuntu with as few headaches as possible...

I'm thinking of getting a Latitude D430.  Anybody have any experience with Ubuntu on this machine?  Any info on success, or disaster, would be much appreciated...

I was thinking of buying an M1210, as there have been good success stories with this machine on these forums, but Dell no longer sells it apparently, so I'm thinking (suspiciously) of the (newer and more unknown) D430...

Thanks much--

--Mark

---

### Post by ddrichardson on 2007-08-25
Have you looked at Dell's range of Ubuntu preloaded notebooks?

[US]("http://www.dell.com/content/topics/segtopic.aspx/linux_3x?c=us&cs=19&l=en&s=dhs")  or [UK]("http://configure.euro.dell.com/dellstore/config.aspx?b=&c=uk&cs=ukdhs1&l=en&oc=N08645L&s=dhs")

---

### Post by WhatToDo on 2007-08-25
Thanks; yes, I've looked...

Though the term "range" makes me chuckle, since it appears there's only one sold that way in the US, and one (different one) for the UK...

Anyway, I was looking for something with a 12" screen, hopefully.  The Ubuntu Dell notebook marketed here in the US is 14"; the UK one is 15"... more the standard common laptop size, whereas I'm hoping for tiny tiny...

Anyway, the D430 is kind of new, so it's not surprising me that nobody looking at these lists has experience with it...

Digging around, it looks to me like people have a lot of issues with machines having similar hardware configurations, so I wouldn't bet a lot on getting the D430 running Ubuntu without all kinds of fussing and fighting...

Maybe I will play stick-in-the-mud, and see if I can get them to buy from somebody else, like ZaReason, who sells the Asus Z33Ae (nice and small) configured to run Ubuntu right out of the box with no extra work fiddling with drivers, etc.  I never really liked Dell anyway, ever since they started making you wait hours in little phone queues, pressing buttons in menus, and forcing you to actually speak to a voice recognition machine, which is SO infuriating, and then in the end they route your call to India over this awful IP-phone connection that they must get for free, etc...

Well, there's my little rant...  ditto for Microsoft...

thanks--

--mark

---

### Post by ddrichardson on 2007-08-27
It doesn't surprise me that Dell are going for as few configurations as possible, it does greatly simplify support. 

If my company was springing for it then (to be honest regardless of how well Ubuntu ran on it) I'd be getting the  XPS1330 - I really like the super light sub notebooks.

---

### Post by crthomas on 2007-09-20
I just installed 7.04 on my new D430.  The wireless worked right out of the box (using restricted drivers).  The resolution was set to 1024x768, but I found a fix for it that was easy to use.  ([http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Issues/Intel_945GM_video_issues](http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Issues/Intel_945GM_video_issues))
I got bluetooth, but I haven't tested it yet.  The hardware switch for the wifi/bluetooth works.  Suspend works fine, but Hibernate is iffy.

If you have any other questions, I am happy to help.

---

### Post by lol on 2007-09-29
My only problem with Ubuntu on the D430 so far has been fan control. For some reason I cannot force the fan to run continuously at high speed and as a result the CPU is often around 70°C or more.

I tried using i8kutils but a few seconds after setting the speed to 2 something (bios, other software?) switch it back to 1...

Even when running i8kmon -a (with the proper setting in i8kmon.conf), the speed keeps changing from 2 to 1 to 2 to 1.. forever.

This seems to be a minor issue, but as a result the laptop is always way to warm to keep it on your lap and I don't like having the CPU at such high temperature most of the time: that's often a sign of a short life expectancy...

---

### Post by crthomas on 2007-09-29
There is a fan speed setting in the bios that affects the maximum speed of the fan.

---

### Post by lol on 2007-09-30
On the D430? I wish there was! But there is no control over the fan in the bios of this laptop. There isn't even a system health screen displaying the speed of the fan or the temperature of the CPU...

What is frustrating is that on my Inspiron 6000 I have no problem to control the fan with i8kutils and that the average temperature of the CPU is around 40°C.

Considering the fact that the Inspiron has a 2,13Ghz CPU and the D430 a small dual core 1.2Ghz that's a big disapointment. But I guess that the problem comes from the hardware, not from Ubuntu.

---

### Post by crthomas on 2007-09-30
Sorry, it wasn't the fan, it was a setting for the hard drive that I was thinking of.

---

