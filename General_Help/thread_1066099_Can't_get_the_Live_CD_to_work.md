---
title: "Can't get the Live CD to work"
date: 2009-02-10
forum: General Help
---

### Post by Jimmy1 on 2009-02-10
Hello everyone,
I just download Ubunto and burned it to the CD, after I start the CD and select the "try Ubunto without any changes" (forget word for word what the option is). It shows the orange bar moving back and forth for about a minute or two and then the orange bar goes away and then starts from the left moving to the right. After it gets to the 4th little box it just sits there for about 5 minutes, and then the screen goes black and then comes up with a lot of text saying some things are missing or can't load and at the bottom of all of this says "status 255".

I did not get all of the text it shows, if you need it I will load it back up and get all of it.


Does anyone know what is causing this? I would like to try out Ubunto before installing it just to make sure it will work.


If you need any info please let me know, and I will get it back to you ASAP.

---

### Post by taurus on 2009-02-10
1.  Did you remember to run the checksum to check the integrity of the ISO image that you have just downloaded?

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

2.  Did you burn it at a slow speed like 4x?

3.  Did you pick the check cd for defects option at the initial screen?

4.  What's the spec of your machine?

---

### Post by JK3mp on 2009-02-10
Probably got damaged at download. That or wasn't properly burned as mentioned above. Just give in redownload it on a strong connection and burn it using a slow burn process as mentioned above.

---

### Post by Jimmy1 on 2009-02-10
> 1. Did you remember to run the checksum to check the integrity of the ISO image that you have just downloaded?
Yes, and it came back good.
> 2. Did you burn it at a slow speed like 4x?

Yes.
> 3. Did you pick the check cd for defects option at the initial screen?
Yes, it said the CD was fine.
> 4. What's the spec of your machine? 
Intel Pentium 4 processor, 3.06GHz
1016MB RAM
The graphics card is a NVIDIA GeForce FX 5500 with 256MB of memory.

I have Windows XP on it right now. If I did not list the specs you wanted please let me know I will get them.


Thanks for the help so far :)

---

### Post by taurus on 2009-02-10
At the initial boot screen from the LiveCD, press F4 and pick the safe graphic mode.  See if that works.

---

### Post by Jimmy1 on 2009-02-10
I tryed it, and it does the same thing as before.

---

### Post by taurus on 2009-02-10
Maybe try the alternate CD.

---

### Post by Jimmy1 on 2009-02-11
If I try the alternate CD, you can't try out Ubunto first to make sure it works right?

And do you know why the live CD won't load up, is it just something in the live CD or is there some thing wrong with my computer that it won't work with Ubunto?

One last question, if I use the alternate CD. Is the install process the same as with the live CD I have now?


Thank you again for your help

---

### Post by jespdj on 2009-02-11
It's Ubunt**u**, not Ubunt**o**.

Can you tell us more about the error messages you get? Those error messages can contain important clues to the source of the problem. With more information, we might find a workaround for you.

Maybe you have some hardware in your computer that's not fully compatible with Ubuntu.

---

### Post by Jimmy1 on 2009-02-11
> It's Ubuntu, not Ubunto.
I am very sorry about that, did not notice I was using the "O".
> Can you tell us more about the error messages you get?
Sure, here is what it shows.

```
udevd-event[4539] /run program: exec of program '/sbin/mobprobe' failed
udevd-event[4541] /run program: exec of program '/sbin/mobprobe' failed
udevd-event[4543] /run program: exec of program '/sbin/mobprobe' failed
udevd-event[4622] /run program: exec of program '/sbin/mobprobe' failed
udevd-event[4625] /run program: exec of program '/sbin/mobprobe' failed
udevd-event[4627] /lib/udev/path_id
udevd-event[4629] /lib/udev/path_id
udevd-event[5244] /sbin/modprobe
udevd-event[5246] /sbin/modprobe

/etc/rcs.d/sloudev: 105: usplash_write: Permission denied
/etc/rcs.d/sloudev: 105: read link: Permission denied

Segmentation fault

init res main process[4057] killed by SEGV signal
init unable to execute "/bin/sh" for rc default Permission denied
init rc-default main process[5255] terminated with status 255
```

---

### Post by Jimmy1 on 2009-02-16
Hello,

Does anyone have any ideas?

---

