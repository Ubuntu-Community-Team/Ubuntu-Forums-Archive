---
title: "dell xps m1330 fan stays on all the time after upgrade"
date: 2008-10-31
forum: Dell Ubuntu Support (CLOSED)
---

### Post by jlhughes on 2008-10-31
Upgraded to 8.10 Intrepid and now dell xps m1330 fan stays on all the time.

How to I restore control of fan?

---

### Post by Zeedok on 2008-11-01
I also have a Dell m1330 and my fan is coming on and off every 5-10 secs (really irritating)!!

I do have gkrell installed (which gives you control over your fans) but changing the temperature triggers doesn't seem to help.

Any help . . .???

---

### Post by jlhughes on 2008-11-01
Well, I don't know if this fixed the problem, but I reinstalled the i8kutils that come with the Dell and then restarted the computer.

Fan is off and the computer temperature monitor applet reports 40c

---

### Post by Zeedok on 2008-11-01
I tried that - it didn't help.

I'm going to try removing the gkrell-i8k module to see what difference that makes.

---

### Post by Zeedok on 2008-11-01
I've removed everything from gkrellm etc and I still have the fan going on and off - which makes me think that gkrellm (and the plugin it used) wasn't doing anything.

Can anyone help?

---

### Post by bigbrovar on 2008-11-01
I have the same problem .. read somewhere that it would help if you upgrade the bios which i tried but didnt work. i mean the dell use to be so quiet in hardy. the price we pay for leaving on the edge :(

---

### Post by Zeedok on 2008-11-01
I think I am a little closer to sorting this out.

If I remove gkrellm, gkrellm-i8k and i8k-utils and remove the line:

```
i8k force=1
```

from:

```
sudo gedit /etc/modules
```

Then my fan stays on all the time.

If I then re-install everything (and re-enter that line into /etc/modules), I can configure my fan settings using gkrellm - it doesn't come on and off anymore.

The packages seem the same, so I don't know why re-installing them helps.

Now I just need to work out the most appropriate temperature triggers for my fans . . .

---

### Post by Zeedok on 2008-11-01
After I wrote the last post, I realised that the fan was no better.

Then I found this [http://ubuntuforums.org/showthread.php?t=948556](http://ubuntuforums.org/showthread.php?t=948556), and after a bios upgrade (to a12 - I just installed it in windows - took 5-10 mins) the problem is solved.

Hope this works for you too jlhughes.

---

### Post by bigbrovar on 2008-11-01
i upgraded to A13 which is the latest bios but the problem still exist .. the default bios that came with my system was A13

---

### Post by Yeti can't ski on 2008-11-06
Bigbrovar, 

I also saw A13 in Dell's site, but I had read in other threads that A12 worked fined sob I sticked to it. And indeed, A12 works just like magic. It is perfectly silent now. 

Moreover, you don't need a Windows (argh!) boot do it. There is Dell Linux page for that:

[http://linux.dell.com/wiki/index.php/Tech/libsmbios_dellBiosUpdate](http://linux.dell.com/wiki/index.php/Tech/libsmbios_dellBiosUpdate)

The tutorial is just perfect. My only problem was the last command line. They say in their example "...bios.hdr-2.3.2" but in my case the name of the file was simply "bios.hdr" (ok, that's obvious, but I am a rookie and it took one minute to figure that out).

Good luck.

[EDIT]

Bigbrovar, 

Sorry, 

After I checked other forums, I saw your posts and realized that you already considered downgrading to A12 (did you do that?). I am only leaving this message here because it might help others.

---

### Post by Calmeida on 2008-11-08
Have had the same issue with my m1330, its the sucky Nvidia card. I solved it by using the older Nvidiadriver that is offered in hardwareconfig, 176 i believe.

Its tremendously annoying with that fan pumping. But, its due to craphardware on some m1330:s.

---

### Post by jesse0 on 2008-12-02
I can confirm that upgrading to bios A14 fixes this. After the Intrepid upgrade, my fan was pulsing: blowing for a period of time, pausing for just a moment then blowing again. Repeat.

---

### Post by edwardTheGreat on 2008-12-10
> **jesse0 said:**
> I can confirm that upgrading to bios A14 fixes this. After the Intrepid upgrade, my fan was pulsing: blowing for a period of time, pausing for just a moment then blowing again. Repeat.

+1
Same for me, Upgrade to A14 fixed it.

---

### Post by Bealer on 2009-04-13
It was ok for me on the A14 BIOS with Intrepid, but I'm now using Jaunty with the 180 NVidia drivers and the problem is back.

I've just upgraded to the A15 BIOS but no luck.

---

### Post by bbock on 2009-04-29
I can confirm that the annoying fan behavior reappears with the upgrade to Jaunty, even with latest BIOS.

---

### Post by bbock on 2009-04-29
Configuring i8kmon according to [http://ubuntuforums.org/showthread.php?p=5275415](http://ubuntuforums.org/showthread.php?p=5275415) helped a little bit for me. The fan still kicks in pretty regularly, but is silenced much faster.

---

### Post by pognonec on 2009-09-28
I found a (weird) solution: in system/administration/harware drivers:
Shift from NVIDIA version 180 to NVIDIA version 173.
Et voilà!
Quiet again :-)

---

