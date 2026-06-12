---
title: "continous freezing ubuntu"
date: 2009-02-22
forum: General Help
---

### Post by Z3r0t0l0rEnCe on 2009-02-22
Well I've been using ubuntu for a while.  My computer keeps freezing under ubuntu no matter what I'm doing.  Any suggestions would be helpfull.

---

### Post by tehforum on 2009-02-22
Any memory hogging applications running that might make Ubuntu freeze?

I use "System Monitor", like a Task Manager. Right click on the panel at the top > Add to Panel > System & Hardware > System Monitor > Click on it > Add > Done.

---

### Post by DeadRobot on 2009-02-22
This used to happen to me.  It always happend when I was using Firefox.  I just switched to Opera and I haven't had a freeze since.

---

### Post by Z3r0t0l0rEnCe on 2009-02-22
Avant Window Navigator and gDesklets are 2 programs that I set to run but it does happen only when there all running and using firefox. I have Avant Window Navi running while I'm using firefox to see if that is the problem.  But it hasn't done it yet.  I'm starting to think that gDesklets is causing it as it not running right now.

---

### Post by Gatorade on 2009-02-22
I've just started to notice this as well . pages take forever to load.

I'm using firefox as well. it wasn't like this before,pages used to load in the blink of an eye. I have opera as well , but its not much better.

---

### Post by Z3r0t0l0rEnCe on 2009-02-22
Well I just got back from it freezing again for the fourth time this morning. All I did was minimize firefox and bam froze. I don't know what to do. This is even a fresh install with all updates. Help please!

---

### Post by Gatorade on 2009-02-22
thankfully , my problems aren't that bad. doesn't usually freeze up completely , its just slow loading when I click a link.

---

### Post by Z3r0t0l0rEnCe on 2009-02-23
Well two more freezes this morning! WTF!!! Its more like a hardware problem. Any clues how to check for hardware issues as I'm a noob(Work in progress) still. Here are my specs:

Antec PSU 400 Watt
Intel P4 3.0 HT Socket 775
OEM Board D915 PCY
PNY DDR2 667 2x1 GB
ATI x300
Sound Blaster Live 24 Bit
IDE WD 100GB
Seagate SATA 160 GB
Seagate SATA 320 GB
Maxtor  SATA 250 GB

---

### Post by VoodooSteve on 2009-02-23
> **Z3r0t0l0rEnCe said:**
> Well two more freezes this morning! WTF!!! Its more like a hardware problem. Any clues how to check for hardware issues as I'm a noob(Work in progress) still. Here are my specs:

Antec PSU 400 Watt
Intel P4 3.0 HT Socket 775
OEM Board D915 PCY
PNY DDR2 667 2x1 GB
ATI x300
Sound Blaster Live 24 Bit
IDE WD 100GB
Seagate SATA 160 GB
Seagate SATA 320 GB
Maxtor  SATA 250 GB

Interesting, I recently did a wubi install on one of my desktops with very similar hardware and I am having random freezing issues as well. Have you had any luck checking for hardware issues?

---

### Post by Z3r0t0l0rEnCe on 2009-02-24
> **VoodooSteve said:**
> Interesting, I recently did a wubi install on one of my desktops with very similar hardware and I am having random freezing issues as well. Have you had any luck checking for hardware issues?

No I'm still working on it.  It happened 2 times this morning again. I ran memtest and found a bunch of errors but none that would cause these freezes! I still have no clue what the issue is.

---

### Post by Slim Odds on 2009-02-24
> **Z3r0t0l0rEnCe said:**
> No I'm still working on it.  It happened 2 times this morning again. I ran memtest and found a bunch of errors but none that would cause these freezes! I still have no clue what the issue is.

What? any memtest errors could cause freezing.

What where the errors?

---

### Post by lisati on 2009-02-24
> **Z3r0t0l0rEnCe said:**
> Well two more freezes this morning! WTF!!! Its more like a hardware problem. Any clues how to check for hardware issues as I'm a noob(Work in progress) still. Here are my specs:

Antec PSU 400 Watt
Intel P4 3.0 HT Socket 775
OEM Board D915 PCY
PNY DDR2 667 2x1 GB
ATI x300
Sound Blaster Live 24 Bit
IDE WD 100GB
Seagate SATA 160 GB
Seagate SATA 320 GB
Maxtor  SATA 250 GB

I initially thought maybe not enough RAM but this rules it out (my Ubuntu mmachine happily works with 222Mb available RAM!!!, as long as I don't expect it to do too many things at once.....)

---

### Post by Z3r0t0l0rEnCe on 2009-02-24
When you run memtest, go to configure and there is a config for checking errors.

---

### Post by Z3r0t0l0rEnCe on 2009-02-24
> **Slim Odds said:**
> What? any memtest errors could cause freezing.

What where the errors?

When you run memtest there is a config section were you can check for errors. The only problem is it froze through part of the test. Could this indicate that the problem lies in the memory?

---

### Post by dsmithnc on 2009-02-27
I noticed in your specs that you are using at ATI videoboard?

In a new install of 8.10, I was having a terrible time with freezes until I unistalled the ATI driver that 8.10 had installed, so far so good.  I'll let it hum a while before I know for sure, but you might want to take a look at it.

Dick

---

### Post by ed1963 on 2009-03-04
I also had constant and frustrating freezes. Changing video card worked for me.

---

