---
title: "M1330 brightness control always goes two steps"
date: 2008-05-20
forum: Dell Ubuntu Support (CLOSED)
---

### Post by scotty64 on 2008-05-20
Everything works fine on my M1330 (LED backlight, Nvidia graphics, A10 Bios), but I notice that when I try to adjust the display brightness via Fn + ArrowUP/Down, it always goes two steps. This is sometimes difficult as the display is either too bright or not bright enough.
Any ideas how to fix this?

---

### Post by sdennie on 2008-05-21
I think most of the buttons on the m1330 are handled in BIOS so, it's possible that the BIOS is trying to turn down the brightness and linux is trying to turn down the brightness at the same time (I use a custom kernel so I can't actually test this).  One thing you could try would be to turn off the Ubuntu acpi brightness scripts.  Something like this:

```

sudo chmod -x /etc/acpi/video_brightness*.sh

```

If that doesn't work, reset those files with:

```

sudo chmod +x /etc/acpi/video_brightness*.sh

```

No idea if that will work but, it's worth a try.

---

### Post by Technoviking on 2008-05-21
The video module screws this up, you need to remove it.

1. Edit /etc/modprobe.d/blacklist
```
sudo gedit /etc/modprobe.d/blacklist
```
2. Add to bottom of file
```
# fix brightness adjustment
blacklist video
```
3. Save and reboot.

---

### Post by ethanay on 2008-06-04
blacklisting "video" is not an option for me, as it creates several more serious problems on my install:  graphical errors (e.g., disappearing graphics/windows) and artifacts, and some control issues.  Furthermore, many of these issues persisted even after I had delisted the video module.

I've tried Vor's proposed solution -- it definitely changes the behavior, but it doesn't fix the problem.  With the scripts active, you can see the brightness move up/down a step, then a few more steps afterwards.  With the scripts disabled, the brightness immediately jumps to the same end value with no apparent intermediary steps.

oh well.  i can wait for an official fix.

---

### Post by scotty64 on 2008-06-05
Blacklisting "video" worked fine for me. The brightness control is o.k. now. The only thing that bothers me (and I do not know if that is related) is that the powermanagement is not recognizing activity on an external second screen. The screen just fades black from time to time, even when I am working on it and I have to move the cursor to the built in LCD in order to get the display back or to avoid the blanking.

---

### Post by atlas95 on 2008-06-05
Do you know if this will be repair and when?
Thanks

---

### Post by Technoviking on 2008-06-05
> **atlas95 said:**
> Do you know if this will be repair and when?
Thanks
Did you file a bug?

Mike

---

### Post by ethanay on 2008-07-29
> **Mike said:**
> Did you file a bug?

Mike

[bug #226981]("https://bugs.launchpad.net/dell/+bug/226981") deals with this issue specifically, but this bug report and others seem to end only with people saying "workaround: blacklist video" but at least in my experience the problems that occur after blacklisting are more serious (e.g., parts of or whole objects on the screen disappearing completely) than the constant annoyance of having overly-sensitive fn - brightness controls.

so I'm hoping it gets triaged soon and at least put in the queue.

---

### Post by undoIT on 2008-10-30
Unfortunately, this is still an issue in Kubuntu 8.10 Intrepid. I'm not installing Ubuntu on my M1330 this time around so I don't know if it was fixed in Gnome or not (Ubuntu is going on my other laptop which doesn't have this problem).

I have the latest A12 bios installed. Screen brightness is set to dimmest in bios and Guidance power manager. Yet, the screen still insists on blasting my eyeballs with the brightest setting each reboot.

---

### Post by Technoviking on 2008-10-30
This fix will NOT work in Intrepid, at least in Gnome.

> **Technoviking said:**
> The video module screws this up, you need to remove it.

1. Edit /etc/modprobe.d/blacklist
```
sudo gedit /etc/modprobe.d/blacklist
```
2. Add to bottom of file
```
# fix brightness adjustment
blacklist video
```
3. Save and reboot.

---

### Post by drsaamah on 2008-11-01
If blacklisting the video semi fixes the problem, doesn't that indicate that this is a driver issue?

---

### Post by undoIT on 2008-11-26
As Technoviking noted, blacklisting video does not work in Ubuntu Intrepid. However, it does work in Kubuntu Intrepid, which seems to indicate that something in Gnome is different. Has anyone come up with a brightness fix for the M1330 that works in Ubuntu 8.10?

---

### Post by Technoviking on 2008-11-27
I think it is a problem with gnome-power-manager.

---

### Post by nwadams on 2008-11-27
> **vor said:**
> I think most of the buttons on the m1330 are handled in BIOS so, it's possible that the BIOS is trying to turn down the brightness and linux is trying to turn down the brightness at the same time (I use a custom kernel so I can't actually test this).  One thing you could try would be to turn off the Ubuntu acpi brightness scripts.  Something like this:

```

sudo chmod -x /etc/acpi/video_brightness*.sh

```

If that doesn't work, reset those files with:

```

sudo chmod +x /etc/acpi/video_brightness*.sh

```


No idea if that will work but, it's worth a try.

That worked perfectly for me, how do I make this permanent so I dont' have to issue the command every time i reboot?

---

### Post by sdennie on 2008-11-27
> **nwadams said:**
> That worked perfectly for me, how do I make this permanent so I dont' have to issue the command every time i reboot?

If that worked (I admit I'm surprised), you shouldn't need to reissue the command.  "chmod -x" should prevent that script from being run across reboots unless you then issue a "chmod +x".

---

### Post by EvanR on 2008-11-28
> **vor said:**
> I think most of the buttons on the m1330 are handled in BIOS so, it's possible that the BIOS is trying to turn down the brightness and linux is trying to turn down the brightness at the same time (I use a custom kernel so I can't actually test this).  One thing you could try would be to turn off the Ubuntu acpi brightness scripts.  Something like this:

```

sudo chmod -x /etc/acpi/video_brightness*.sh

```

If that doesn't work, reset those files with:

```

sudo chmod +x /etc/acpi/video_brightness*.sh

```

No idea if that will work but, it's worth a try.

This worked fine for me, on ubuntu 8.10 gnome on xps m1330.

---

### Post by ethanay on 2008-11-28
> **EvanR said:**
> This worked fine for me, on ubuntu 8.10 gnome on xps m1330.

Hmm, interesting.  It didn't resolve the problem totally for me, but making the brightness scripts non-executable gave me one extra layer of brightness to cycle through (three down, three up total).  With the scripts executable, fn+up/dwn cycles through the entire brightness spectrum in just two presses.

So it makes it better, but something else is still weird

---

### Post by GeoMX on 2008-11-30
Hi, I got the same problem, blacklisting the video module worked fine in Ubuntu 8.04, however, in 8.10 my system would ["freeze"]("http://ubuntuforums.org/showthread.php?t=966492"). A frozen system is worst, so I enabled the video module but my brightness keys don't work as they should.

Next time I reboot I'll try disabling the acpi video scripts.

Edit...
I've just tried chmod -x for the video_brightness scripts and it seems to work! Thank you :).

Just a question, can we really say this is a "good" fix? Well, it's "good" since it works for me, but I mean, shouldn't it be done another way?

---

### Post by danf_1979 on 2008-11-30
```

sudo chmod -x /etc/acpi/video_brightness*.sh

```

did improve things in here too (DELL Inspiron 9400 and jaunty).

---

### Post by undoIT on 2008-11-30
```
sudo chmod -x /etc/acpi/video_brightness*.sh
```

This did give a wider range of adjustments on my M1330, however it is a bit quirky. Sometimes it flashes to the brightest setting for a split second while adjusting to the next level of brightness.

Also, I have the brightness set to the dimmest setting. When GDM loads it gets reset to the brightest level and stays at that level until the desktop is loaded.

So, this does work, but not as well as blacklisting video did in 8.04.

---

### Post by pormogo on 2008-12-14
Unfortunately the birghtness adjustment levels aren't consistant but it's much better then it was.

Actually after using the chmod -x fix posted earlie I noticed that sometimes especially after changing brightness after returning from a suspend my little brightness meter gets "stuck" on the screen :(

---

### Post by x C0MMAND0 x on 2008-12-15
> **undoIT said:**
> ```
sudo chmod -x /etc/acpi/video_brightness*.sh
```

This did give a wider range of adjustments on my M1330, however it is a bit quirky. Sometimes it flashes to the brightest setting for a split second while adjusting to the next level of brightness.

Also, I have the brightness set to the dimmest setting. When GDM loads it gets reset to the brightest level and stays at that level until the desktop is loaded.

So, this does work, but not as well as blacklisting video did in 8.04.

I have the exact same experience.

---

### Post by MikeyUbun2 on 2008-12-15
Yo this might not help you at all but on my inspiron the brightness skips too but do this easy trick that anybody could figure out if they thought for two seconds.
My trick is: the settings are 1-8 and i want it on six, so i  go from 8 to 6 to 4 to 2 to 1 then from 1 to 3 to 5 to 7
|-<-|---<---|---<---|---<---O
O--->---|--->---|--->---|
1   2   3   4   5   6   7   8

so in the meantime i'm gonna use this trick and it isn't too much of a pain.

(you can also change your brightness settings in the setup just press f2 at startup)

---

### Post by edwardTheGreat on 2008-12-16
> **undoIT said:**
> ```
sudo chmod -x /etc/acpi/video_brightness*.sh
```

This did give a wider range of adjustments on my M1330, however it is a bit quirky. Sometimes it flashes to the brightest setting for a split second while adjusting to the next level of brightness.

Also, I have the brightness set to the dimmest setting. When GDM loads it gets reset to the brightest level and stays at that level until the desktop is loaded.

So, this does work, but not as well as blacklisting video did in 8.04.

> **x C0MMAND0 x said:**
> I have the exact same experience.

+1 me too

---

### Post by kevyin_ on 2008-12-19
> **scotty64 said:**
> Blacklisting "video" worked fine for me. The brightness control is o.k. now. The only thing that bothers me (and I do not know if that is related) is that the powermanagement is not recognizing activity on an external second screen. The screen just fades black from time to time, even when I am working on it and I have to move the cursor to the built in LCD in order to get the display back or to avoid the blanking.

try checking your screensaver settings? that was what happened to me.

---

