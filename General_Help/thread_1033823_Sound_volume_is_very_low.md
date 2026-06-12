---
title: "Sound volume is very low"
date: 2009-01-07
forum: General Help
---

### Post by butterandguns on 2009-01-07
I have been away from Ubuntu for a very long time and decided I just couldnt take windows anymore.  I have reinstalled Ubuntu but the maximum volume from my laptops speakers is very low. Any help? I am new to this and will probably need an in depth explanation.

---

### Post by Drubie on 2009-01-07
Obvious answer: turn it up!

I am suffering from a similar thing.  I am runnign ubuntu 8.04 on a dell inspiron 9 mini and the maximum volume really is very low, even for external speakers (powered by the computer.  this obviously is not a problem with an external amplifier).

---

### Post by bobleny on 2009-01-07
When I had the issue, I simply needed to turn the volume up....

No, I'm serious!

Try this:
Click on the little speaker icon.
Click on option: Mixer.
Turn PCM all the way up.
Turn Master half way up.
Turn Line in Boost all the way up.
Turn the other options all the way down (Unless you need to use the mic...).
Click on tab: Input.
Turn Line in Boost all the way up.
Turn the other options all the way down (Unless you need to use the mic...).
-----------

Hopefully that will solver your problem as it did mine.

Oh, and one more thing, make sure the externals are turned up all the way and your not muted.

Good luck!

---

### Post by Ripose on 2009-01-07
Changing the settings under Volume Control still does not produce even half of the volume that the same system does under Windows.:(

I would think that we need to look into the sound drivers, not system settings.:confused:

If I ever do find an answer to this I'll post again.:)

---

### Post by thyraios on 2009-01-08
I had the same problem on my inspiron and after some research I found that the Front volume meter was quite low. Simple enough for me. Put all playback tracks visible and try changing all of them in volume control (Alsa-mixer) one by one. There shouldn't be a problem with the driver if you are using onboard sound

---

### Post by namdung on 2009-01-08
In terminal
```
alsamixer
```

Use the arrow keys to maximize the volume (*Master, PCM, Front*).

---

### Post by John Jason Jordan on 2009-01-14
> **namdung said:**
> In terminal
```
alsamixer
```

Use the arrow keys to maximize the volume (*Master, PCM, Front*).

What if you're using pulseaudio on Intrepid? When you use pulseaudi alsamixer shows only master and capture. I have both set to 100%, but my volume is still less than half what it is supposed to be.

---

### Post by R3p1h on 2011-05-14
Hi, I was looking hard to solve this problem, I am sure that you already fixed

but for the user that coming for search engine websites this is the solution

[http://ubuntuforums.org/showpost.php...47&postcount=4]("http://ubuntuforums.org/showpost.php?p=8314847&postcount=4")

work for me and I think work for anyone that have dell laptop inspiron.
I have Dell Inspiron E1705 / 9400 in ubuntu 10.4

---

