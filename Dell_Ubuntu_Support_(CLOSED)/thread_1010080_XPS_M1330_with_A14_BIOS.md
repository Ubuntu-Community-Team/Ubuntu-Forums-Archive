---
title: "XPS M1330 with A14 BIOS"
date: 2008-12-13
forum: Dell Ubuntu Support (CLOSED)
---

### Post by sdennie on 2008-12-13
Yesterday I upgraded to the A14 BIOS and I've noticed that /proc/acpi/thermal_zone/*/* is staying steady at 25C.  With the A12 BIOS, I would generally see temperatures hover between (approximately) 31C and 41C.  I believe the 25C number to be accurate because I compiled a kernel at -j3 earlier and the CPU temperature jumped to 52C.  I'm in a noisy place at the moment and so it's hard for me to judge the fan speed but, has anyone else noticed the A14 BIOS being excessive with the fan?  Has the policy with A14 just become, "Keep the fan on always?"

---

### Post by IamReck on 2008-12-13
I currently have the A12 BIOS, if you tell me what I need to do to check the temperatures that you are talking about I will do a comparison.

---

### Post by sdennie on 2008-12-13
It would be:

```

cat /proc/acpi/thermal_zone/*/*

```

The other components of my machine seem to be at the same temperatures they were before the upgrade to A14 so I'm wondering why the CPU is so cool (25C is cooler than the ambient temperature...)

---

### Post by thorcik on 2008-12-14
strange, I have 55 @ m1330/8.10/A14

---

### Post by sdennie on 2008-12-15
The GPU and disk temperatures are comparable to when I was running the A12 BIOS so, I have a feeling that the A14 BIOS has a bug when reporting CPU temperatures.  I can't imagine a drop in CPU temperature of 15C not also causing the rest of the system to drop in temperature.

---

### Post by Vegardlu on 2008-12-18
I have updated my m1330 to A14 and it keeps saying my temperature is 25 degrees also, it has to be wrong, and it can’t be 25 all the time. Could it hurt the system? Anyone have an idea of what I can do?

Also, the fan just keep spinning at a fairly high speed, it’s a very annoying sound.

---

### Post by sdennie on 2008-12-18
I think it's just a bug in the reported temperature.  The temperature does fluctuate with load and the fans seems to be doing the right thing still.  As always, my fans are almost always off when I'm on battery and the machine is cool to the touch so, yet the CPU temperature hasn't changed from 25C so, I have to believe it's a BIOS reporting problem.

---

### Post by Vegardlu on 2008-12-18
my fan seem to go on the same speed all the time, and never turns off, have you done some tweaking? it stay on the same speed when I leave the computer and when I use it with full load over time. Says 25 C no matter what also. would really love some help, the noise goes on my nerves :)

---

### Post by sdennie on 2008-12-18
This thread can potentially lower fan noise: [ HOWTO: XPS m1330 power savings]("http://ubuntuforums.org/showthread.php?t=847773")

---

### Post by Zeedok on 2008-12-20
Sounds like inaccurate reporting to me.  For the record my XPS m1330 (with the A12 Bios) is running at:

```
cat /proc/acpi/thermal_zone/*/*
<setting not supported>
<polling disabled>
state:                   ok
temperature:             49 C
critical (S5):           99 C
```

---

### Post by sdennie on 2008-12-20
Yes, I agree it's probably a bug with the A14 BIOS.  I've tried both a 2.6.24 kernel and the 2.6.28 kernel and they both report the same temperature.  Fortunately, the fans seem to be sensing the correct temperature and appear to be working as they did with the A12 BIOS.

---

### Post by sdennie on 2008-12-28
I've actually been noticing a lot more problems since upgrading to the A14 BIOS.  A machine that has been completely stable for the last 8 months is now very unstable.  The machine crashes from time to time, the webcam seems to randomly disconnect and then reconnect (I had to blacklist the uvcvideo module to fix this) and last night, the CDROM ejected for no apparent reason.  I'm currently using a 2.6.28 kernel but, I was getting the crashes and webcam oddness with the Ubuntu 2.6.24 as well so, I tend to think these problems are caused by the BIOS update.

---

### Post by eyime on 2009-01-02
Hi,

well this is the output for my computer (dell xps m1330, intel video card and wireless, A14 bios, Ubuntu 8.04LTS with latest updates)

<setting not supported>
<polling disabled>
state:                   ok
temperature:             47 C
critical (S5):           87 C

---

### Post by kungfoofool on 2009-01-06
I haven't noticed problems with temperature reporting (tends to be the same as it was with A12), but I have had a host of other issues (backlight on monitor sporadically not working, battery now reporting that it is old & busted) after upgrading to A14.

```

$ cat /proc/acpi/thermal_zone/*/*
<setting not supported>
<polling disabled>
state:                   ok
temperature:             66 C
critical (S5):           99 C

```

---

### Post by bigbrovar on 2009-01-06
I have been using the A14 bios for quite a while now and i have not had any problem with it. though i have not noticed any improvement neither  cat ```
/proc/acpi/thermal_zone/*/*
```

gave the following output

<setting not supported>
<polling disabled>
state:                   ok
temperature:             45 C
critical (S5):           87 C
dell xps m1330, intel video card and wireless, A14 bios, Ubuntu 8.04LTS with latest updates Linux version 2.6.24-22-generic

---

### Post by pejobe on 2009-01-07
Fan speed and Dell xps m1330 is an ongoing issue. 
Some can relate the problem to the Nvidia graffic drivers:

[http://launchpad.net/+search?field.text=interpid+%2B+nvidia+%2B+fan&field.actions.search=Search]("http://launchpad.net/+search?field.text=interpid+%2B+nvidia+%2B+fan&field.actions.search=Search")

Sometimes it helps to upgrade the BIOS. 

Or maybe Dell is trying to hide some flaws by increasing the speed of the fan, read:

[http://forums.whirlpool.net.au/forum-replies-archive.cfm/999668.html]("http://forums.whirlpool.net.au/forum-replies-archive.cfm/999668.html")

---

### Post by angelillo on 2009-01-09
There is a new version of the BIOS (A15), released two days ago. Maybe you should give it a try...

---

