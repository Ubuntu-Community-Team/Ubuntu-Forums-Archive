---
title: "how do I tell if my system is 32bit or 63bit"
date: 2009-02-09
forum: General Help
---

### Post by ozguitarplayer on 2009-02-09
hey, a question from a novice...how do i tell if my system is 32 or 63bit
and what does it mean?

---

### Post by Therion on 2009-02-09
The difference is the processor.  The CPU itself is either a 32bit CPU or it's a 64bit CPU.

Do you want a technical breakdown of 32 bit registers vs. 64 bit registers?

Okay, good... A bit is short for &#8220;binary digit.&#8221; It is basically how a computer stores and makes references to data, memory, etc. A bit can have a value of 1 or 0, that&#8217;s it. So binary code is streams of 1&#8217;s and 0&#8217;s, such as this random sequence 100100100111. These bits are also how your processor does calculations. By using 32 bits your processor can represent numbers from 0 to 4,294,967,295 while a 64-bit machine can represent numbers from 0 to 18,446,744,073,709,551,615. Obviously this means your computer can do math with larger numbers, and be more efficient with smaller numbers.

The true benefits of this set up don&#8217;t come from the amount of bits, but by the improved structure of the 64 bit vs 32 bit processor's older structure. A 64-bit processor is made with more advanced silicon processes, have more transistors, and faster speeds. This is currently where the true benefit of switching to a 64-bit processor lays.

---

### Post by photon_man62 on 2009-02-09
Great, Therion, but that was useless, actually. :)

He asked how to check what version OS he is running. To do that, type

```
uname -m
```
in the terminal.

---

### Post by mb_webguy on 2009-02-09
Ditto Therion.  However, just because your computer has a 64-bit processor doesn't necessarily mean you have a "64-bit system".  In order to take advantage of the capabilities of a 64-bit processor, you have to use a 64-bit operating system and applications designed for a 64-bit system.

If you do have a 64-bit processor (which includes AMD64 and Intel Core 2 Duo processors, among others), then you'd do well to install the amd64 version of Ubuntu.

---

### Post by photon_man62 on 2009-02-09
Actually, I have a Core 2 Duo on this laptop and a Core 2 Quad on my desktop, and I run the 32-bit version, just because of compatibility.

---

### Post by mb_webguy on 2009-02-09
The oft-mentioned application compatibility issue -- which was once a valid argument against running 64-bit Linux -- is largely a thing of the past.  Flash continues to be the primary problem application when it comes to 64-bit Linux -- it occasionally goes gray, requiring a restart of the browser -- but Adobe is working on the 64-bit Flash plugin.

I recently switched to 64-bit Intrepid from 32-bit Intrepid as I do a lot of compiling and video transcoding, and was pleasantly surprised how well everything worked.

---

### Post by photon_man62 on 2009-02-09
Well, I meant Flash. JUST because of that I am usiing 32 bit :/

---

### Post by mb_webguy on 2009-02-09
> **photon_man62 said:**
> Well, I meant Flash. JUST because of that I am usiing 32 bit :/

Well, as I said, Flash does work for me -- most of the time.  Given the speed boost I get on various other activities, I don't mind restarting my browser from time to time.

And if Adobe would get the 64-bit Linux plugin out of beta, then there'd be no problem at all (one would hope).

---

### Post by gfulton on 2009-02-09
Woops - walked away for a min and then hit reply!

Anyway, I was assuming system referred to his hardware, in which case I was going to recommend looking at /dev/cpuinfo

-gf

---

### Post by steveneddy on 2009-02-10
> **photon_man62 said:**
> Well, I meant Flash. JUST because of that I am usiing 32 bit :/

I run 64 bit and I use the Flash 10 64 bit version from Adobe website and no issues here.

I recently upgraded two desktops in my home and used Adobe's 32 bit automatic installer for Flash 10 (the desktops were not 64 bit processors or OS's) and they also work great.

My opinion is that if you have 64 bit processors, run 64 bit Ubuntu. You will notice the difference.

---

### Post by photon_man62 on 2009-02-10
I'd rather not run 6 bit Ubuntu, that's a bit too old fashioned for me :/

---

### Post by steveneddy on 2009-02-10
> **photon_man62 said:**
> I'd rather not run 6 bit Ubuntu, that's a bit too old fashioned for me :/

My 4, R and P keys sometimes don't type. It a little worn in. lol

:)

---

### Post by photon_man62 on 2009-02-10
Just like my W and R keys. Welcome to the club :D

---

### Post by jespdj on 2009-02-10
> **photon_man62 said:**
> I'd rather not run 6 bit Ubuntu, that's a bit too old fashioned for me :/

And I'd also rather not run 63-bit Ubuntu... ;) I'd like to use that extra bit that my processor has also.

---

### Post by howlingmadhowie on 2009-02-10
> **gfulton said:**
> Woops - walked away for a min and then hit reply!

Anyway, I was assuming system referred to his hardware, in which case I was going to recommend looking at /dev/cpuinfo

-gf

*cough* *cough*

/proc/cpuinfo

---

### Post by geirha on 2009-02-10
To get info on hardware, I prefer to use the lshw (list hardware) command
```
sudo lshw -class cpu
```

As for whether your installed Ubuntu is 32-bit or 64-bit, just check any executable with the file-command
```
$ file /bin/bash
/bin/bash: ELF [COLOR="Blue"]32-bit[/COLOR] LSB executable, Intel 80386, version 1 (SYSV), for GNU/Linux 2.6.8, dynamically linked (uses shared libs), stripped

```

Your OS must be the same bitness, or lower, than the processor/architecture.

---

### Post by ozguitarplayer on 2009-02-10
many thanks geirha that's what I wanted...

---

### Post by rascal+1/2 on 2009-07-23
thanks! Btw, is 100% cpu usage spikes normal for certain apps, or problematic? I witnessed in system monitor, verified in top. For 64-bit processor (quad-core) 64-bit Jaunty.

Regards

---

