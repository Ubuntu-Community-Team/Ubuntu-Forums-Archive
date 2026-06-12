---
title: "DVD output pauses in 0.2sec every 1sec"
date: 2005-10-26
forum: Desktop Environments
---

### Post by mikuskuikku on 2005-10-26
When looking at a DVD the picture looks good in the beginning, but after a while the picture pauses about 0.1-0.2sec every 1sec.
I installed Breezy some days ago.
Created (automaticly) a swap partition on 329Mb and a root partition on 6.7Gb.
After some days i bought more memory to my computer (had 256 and added 512).

I'm not sure if it is a swaping problem or if it is libdvdcss2 that creates this problem.
Got Totem, vlc and kaffeine working but with the same problem.

Sound comes out just nice.

Suggestions? :shock:

---

### Post by Staesys on 2005-10-26
To me it sounds like DMA is not enabled on your DVD drive. If you type the following at a terminal window (assuming /dev/hdc is your CD-ROM/DVD drive):

```
sudo hdparm -d /dev/hdc
```

If DMA is enabled it should say something like:

```
/dev/hdc:
 using_dma    =  1 (on)
```

If not, try typing in:

```
sudo hdparm -d 1 /dev/hdc
```

and it should respond with:

```
/dev/hdc:
 setting using_dma to 1 (on)
 using_dma    =  1 (on)
```

Try playing a DVD again, and if that works, let's make it permanent by modifying the hdparm.conf file:

```
sudo gedit /etc/hdparm.conf
```

and add this to the end of the file:

```
/dev/hdc {
	dma = on
}
```

This should make it permanent.

Hope this helps!

---

### Post by mikuskuikku on 2005-10-27
[QUOTE=Staesys]
Try playing a DVD again, and if that works, let's make it permanent by modifying the hdparm.conf file:
[/QUOTE]

It solved the problem and I modified the .conf file so it will work in the future!

Thanks!

---

### Post by Staesys on 2005-10-27
No problem, I'm glad I could help! :-)

---

