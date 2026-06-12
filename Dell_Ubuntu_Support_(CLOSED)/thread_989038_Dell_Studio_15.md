---
title: "Dell Studio 15"
date: 2008-11-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ponx on 2008-11-21
Hi,

Does anybody have Ubuntu running on a Dell Studio 15..?

If so, does the ATI card perform ok..?  Does the backlit keyboard work..?

Any other issues to be wary of..?

Cheers.

ponx

---

### Post by bohsocks on 2008-11-29
Yes, I do.

It depends on which Ubuntu you install on it.... 

When running Gutsy, the ethernet and wireless will not work... ouch

When running Hardy, the graphics are kind of as-is, I'm running 1280x800 with no issues, but customizing is pretty blech.  I got the internal bluetooth and the keyboard and mouse bundle... they work very well on Hardy and its bluetooth setup....

Ibex is another story... I can't seem to get my bluetooth stuff working in that version... but the ATI card is recognized and an ATI preferences thing is installed... it's nice for dual-head.... but isn't worth losing my keyboard.

I didn't get the backlit keyboard.... and in all versions the sound doesn't work the way it should.

There's no harm in trying it for yourself -- :-D

---

### Post by pah99 on 2008-12-03
Hey. I have a Studio 15. Um, first off, I have only used it under 8.10. 
The backlit keyboard works fine (god I love it). Ati 3450 card works awesome, and the ATI Catalyst Control Center works also. 
There are two big problems at the time.
1st- the two headphones jacks dont work fantastically. What I mean is that only one works (under Ubuntu), and you have to manually mute your laptop speakers to listen to the headphones.
2nd, there was a problem with the Fn key as whenever it was pressed it would kill the keyboard. This was solved in the 2.6.27-8-generic image, but then I upgraded to 2.6.27-9-generic and it went back to the same. Last I checked, at least. 
Other then those two annoyances, its a good laptop. I recommend it.
Hope this helps.

---

### Post by pah99 on 2008-12-04
Update:
The latest (proposed) kernel update solves both problems.

---

### Post by newcpu on 2008-12-08
> **pah99 said:**
> Update:
The latest (proposed) kernel update solves both problems.
My understanding is the headset problem is being addressed upstream in both the kernel (to auto identify the model=dell-m6) and in a TBD alsa version after 1.0.18a.  Hence the fix will not be Linux distribution specific, but rather applicable to all distributions.  I raised a bug report on what I believe to be the same audio problem here, and the dev who worked on this (for openSUSE) is also an alsa dev, and they plan to commit the fix upstream in the kernel/alsa so all distributions will benefit.
[https://bugzilla.novell.com/show_bug.cgi?id=446025](https://bugzilla.novell.com/show_bug.cgi?id=446025)
```
https://bugzilla.novell.com/show_bug.cgi?id=446025
```

With the alsa/kernel fix the mute on the two internal headphone jacks (on the side of the laptop) work properly.  Also the external mic works properly.

I have not been able to get the two internal integrated mics (on either side of the internal integrated webcam) to function yet (however the webcam does function with the uvc driver).

---

### Post by newcpu on 2008-12-08
> **ponx said:**
> Does anybody have Ubuntu running on a Dell Studio 15..?

If so, does the ATI card perform ok..? 
I have the Radeon 3450 HD working with the radeonhd opensource driver.  I have also read of users who have the Radeon 3450 HD working with the proprietary ATI driver on the Dell Studio 15.

Because one can procure the Studio 15 with Ubuntu pre-installed by Dell, my belief is Ubuntu users tend to have a slight edge in support for this laptop over the other distributions.  Although one's general Linux knowledge tends to be a bigger factor in the smooth functionality of this laptop under Linux, as opposed to any distribution specific factors.

---

### Post by wonderbriefs on 2008-12-11
I've been curious about getting the internal mics to work. The webcam didn't work at all with Flash sites like 12seconds.tv until I updated to Flash 10. I was hoping that would fix the mic, but it didn't. 
Kind of a bummer.

---

### Post by nascentmind on 2008-12-25
I too have the same problem with sound. Is it fixed yet

my kernel version : 2.6.27-9-generic

Is there any other way to fix this other than waiting for an update?

---

### Post by pah99 on 2008-12-25
The newest kernel update has fixed this (2.6.27-10-generic). Check the proposed updates if you can't find it.

---

### Post by nascentmind on 2008-12-26
Is it available now? I did a update, a upgrade and a dist-upgrade and I have not found the kernel 2.6.27-10-generic. When will it be released?

---

### Post by pah99 on 2008-12-26
You need to go into your repository settings in Synaptic and you will see a tab with updates (if I can recall correctly). Put a check next to the Proposed section, and then do a "refresh" in Synaptic. Mark all updates and you should see the 10 kernel.

---

### Post by nascentmind on 2008-12-27
Doesn't proposed updates cause instability?

---

### Post by pah99 on 2008-12-27
Yes they can. Thats why you only want to update the kernel image. Its stable enough for daily use right now, and it will fix the problems you are having. I reccomend that you upgrade the kernel and then turn off the proposed updates.

---

