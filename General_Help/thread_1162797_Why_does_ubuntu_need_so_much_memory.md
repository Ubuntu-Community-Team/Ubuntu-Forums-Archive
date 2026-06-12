---
title: "Why does ubuntu need so much memory?"
date: 2009-05-18
forum: General Help
---

### Post by infinities on 2009-05-18
it said something like 384 mb is recommended? XP only requires like 64? Why is it so much?

---

### Post by Bindsa on 2009-05-18
It's because Ubuntu has **realistic** requirements, everyone knows that XP will barely run with 64 mb, Ubuntu runs smoothyly with 384 mb.

---

### Post by dmizer on 2009-05-18
Ubuntu Jaunty was released a month ago. [XP was released in 2001](http://en.wikipedia.org/wiki/Windows_XP).

Hardware has changed quite a bit between then and now.

---

### Post by evermooingcow on 2009-05-18
Also you have the choice of stripping it down to as little as you want...probably a reasonalble min of 7-10MB with just CLI. XP is mostly fixed.

---

### Post by infinities on 2009-05-18
also: I just installed it on a new laptop with 4gb of memory, but in the system monitor it's telling me I only have 2.8. Is that because a whole 1.2 is being consumed, or what?

---

### Post by dmizer on 2009-05-18
> **infinities said:**
> also: I just installed it on a new laptop with 4gb of memory, but in the system monitor it's telling me I only have 2.8. Is that because a whole 1.2 is being consumed, or what?

Linux uses memory much differently than Windows. Most of that is reserved for buffers and cache. Linux uses free RAM to speed things up, and this is why you will ALWAYS show low free ram in Linux.

You can see what memory is being used where by running this command in terminal:
```
free
```

This is perfectly normal.

---

### Post by Kevbert on 2009-05-18
You probably have 32 bit Ubuntu and not enabled your bios to allow memory readdressing (memory hole). This is a historical problem that originally anything above 3.2Gb was unlikely to ever be used and anything above this would be allocated to other peripherals (such as I/O for example) - a bit like the Y2K problem. With 64 bit Ubuntu and 4Gb RAM I get 3956Mb reported using
```
free -m
```
in terminal.

---

### Post by infinities on 2009-05-18
it's telling me my total is 2.8

i'm certain that this computers support 64 bit OS's, i just don't know whether I was supposed to configure it at some point?

---

### Post by dmizer on 2009-05-18
More information than you could possibly hope for with Linux memory usage: [http://forums.gentoo.org/viewtopic-t-175419-postdays-0-postorder-asc-start-0.html?sid=619cda6e4dae2a0651c474f9f5e4dfcf](http://forums.gentoo.org/viewtopic-t-175419-postdays-0-postorder-asc-start-0.html?sid=619cda6e4dae2a0651c474f9f5e4dfcf)

Please post the output of:
```
free
```

---

### Post by infinities on 2009-05-18
total: 2.9
used: .9
buffer: .081
cached: .5


also guys, this question isn't relevant, but how do I install updates when the root account is disabled? what do i use as the password?

---

### Post by Bindsa on 2009-05-18
Brand of your RAM? Are it 2 bars of 2gb or 1 of 4gb?

---

### Post by dmizer on 2009-05-18
Are you on a laptop? If so, your laptop bios could be reserving RAM for video.

---

### Post by infinities on 2009-05-18
> **dmizer said:**
> Are you on a laptop? If so, your laptop bios could be reserving RAM for VRAM.
hopefully not

> **Bindsa said:**
> Brand of your RAM? Are it 2 bars of 2gb or 1 of 4gb?
not sure

also, i had a question that i posted on the last post of the first page

---

### Post by dmizer on 2009-05-18
> **infinities said:**
> hopefully not
Hopefully you're not on a laptop? Or hopefully your laptop is not reserving RAM for video?

This is an extremely common practice for laptop manufactures. You get the benefit of faster video without having to pay for expensive video RAM. This is not a Linux thing, this is a laptop manufacture thing. If this concerns you, you can decrease the amount of memory allocated to video by changing the bios settings.

---

### Post by infinities on 2009-05-18
yes, hopefully it's not reserving ram for vram

i'm not going to be doing anything even remotely graphic intensive

---

### Post by starcannon on 2009-05-18
For updates:
System>Administration>Update Manager

Put in your login password and go.

---

### Post by dmizer on 2009-05-18
> **infinities said:**
> yes, hopefully it's not reserving ram for vram

i'm not going to be doing anything even remotely graphic intensive

Then as I said before, you'll have to modify your bios settings to decrease the amount of RAM allocated to video.

---

### Post by infinities on 2009-05-18
nevermind the root thing, i'm an idiot

---

### Post by dmizer on 2009-05-18
Please post the output of this command:
```
grep -i ram /var/log/Xorg.0.log; grep -i mem /var/log/Xorg.0.log
```
It will show the amount of memory allocated to video.

---

### Post by infinities on 2009-05-18
> ...

(==) intel(0): VideoRam: 262000 KB

...

(II) intel(0): detected 131000 kB stolen memory


if it's possible to copy and paste from a terminal, let me know. I remember you had to tube the output or something. :/

that still doesn't account for much

---

### Post by dmizer on 2009-05-18
> **infinities said:**
> if it's possible to copy and paste from a terminal, let me know. I remember you had to tube the output or something. :/

that still doesn't account for much

You could use xterm instead of switching to terminal display. Then you can simply copy/paste.

> (II) intel(0): detected 131000 kB stolen memory
There's the rest of your memory.

---

### Post by mcduck on 2009-05-18
> **infinities said:**
> if it's possible to copy and paste from a terminal, let me know. I remember you had to tube the output or something. :/

that still doesn't account for much

Just highlight the text you want to copy and then middle-click to paste it. Or use shift-ctrl-c & shift-ctrl-v, or the copy/paste options from the right-click menu.

or redirect the output to a text file: *command > file.txt*

---

### Post by infinities on 2009-05-18
laptop has 4 gb

ubuntu is recogizing 2.8-2.9

.1 of that is used for vram

where's the other gig?

---

### Post by dmizer on 2009-05-18
Please post the output of:
```
cat /proc/meminfo
```

You can direct the output to a file with this command:
```
cat /proc/meminfo > meminfo.txt
```

---

### Post by infinities on 2009-05-18
MemTotal is still 2.96


i'm going to bed, i'll dig this thread up tomorrow

---

### Post by Arup on 2009-05-18
XP hardly runs on 64mb of mem, 2K did but with issues, only NT ran with 64mb of memory.

---

### Post by dcstar on 2009-05-18
> **Arup said:**
> XP hardly runs on 64mb of mem, 2K did but with issues, **only NT ran with 64mb of memory**.

Like a three-legged dog with a bad foot........

---

### Post by msflying on 2009-05-18
> **dmizer said:**
> More information than you could possibly hope for with Linux memory usage: [http://forums.gentoo.org/viewtopic-t-175419-postdays-0-postorder-asc-start-0.html?sid=619cda6e4dae2a0651c474f9f5e4dfcf](http://forums.gentoo.org/viewtopic-t-175419-postdays-0-postorder-asc-start-0.html?sid=619cda6e4dae2a0651c474f9f5e4dfcf)

Please post the output of:
```
free
```

That's very helpful.Thanks a lot

---

### Post by ibuclaw on 2009-05-22
@infinities, are you still having a problem?

lshw will tell you for definite how much RAM you have:
```
sudo lshw -short | grep memory
```
Do you think you could you have easily mistaken 3GB for 4GB?

Assuming there are only two RAM chips in your Laptop, can you confirm that all are seated properly?

And, if your doubt still persists, could you show where you got the information about your Laptop having 4GBs of Memory? (ie: in Window's System Monitor)

Regards
Iain

---

### Post by tpmoney on 2009-05-22
In addtion to what's already been said, did the computer come with 4GB of RAM (and from a reputable shop) or was it added later / built from scratch? I seem to recall a few motherboards that used an intel chipset (945 maybe?) that could only support up to 3GB of RAM

---

### Post by DeMus on 2009-05-22
> **infinities said:**
> it said something like 384 mb is recommended? XP only requires like 64? Why is it so much?

Do you really think you can get XP running with only 64MB ram? Be serious. This is the MS marketing machine speaking.
I have an old laptop (Compaq Armada E500 with a P3-600MHz processor and have recently increased memory from 128MB to 256MB. Only now XP is running like I can expect on this old laptop.
Even with the 128MB it is slow and the disc is running all the time. (swap memory).
And this is a minimal XP configuration where all unnecessary items have been removed.

Also, there is a big difference between Windows and Linux (well there are plenty) and that is that Windows tries to keep memory empty. As soon as you stop a program it is removed from memory to make this available for something else. That is nice if you have little memory. Whenever you have like 4GB you love it when, just as Linux does, things stay in memory until it is full, to make it faster. A program which has been running before and which is started again is already in memory and can start straight away.
Why should you buy 4GB when you will never use it? Go with Linux and fill your memory, that's what it is there fore.

---

### Post by ibuclaw on 2009-05-22
> **DeMus said:**
> Do you really think you can get XP running with only 64MB ram? Be serious. This is the MS marketing machine speaking.
I have an old laptop (Compaq Armada E500 with a P3-600MHz processor and have recently increased memory from 128MB to 256MB. Only now XP is running like I can expect on this old laptop.
Even with the 128MB it is slow and the disc is running all the time. (swap memory).
And this is a minimal XP configuration where all unnecessary items have been removed.

Have you seen this answer to that question?
> **dmizer said:**
> Ubuntu Jaunty was released a month ago. [XP was released in 2001](http://en.wikipedia.org/wiki/Windows_XP).

Hardware has changed quite a bit between then and now.
I think that better explains the low hardware spec.

---

### Post by TURBO_TURBINA on 2009-05-22
What I understand is that 32BIT OS can read up to 3gb of ram, while 64bit OS can read more than that (dont remember the limit). Have you try the 64BIT Ubuntu?

---

### Post by dmizer on 2009-05-22
> **TURBO_TURBINA said:**
> What I understand is that 32BIT OS can read up to 3gb of ram, while 64bit OS can read more than that (dont remember the limit). Have you try the 64BIT Ubuntu?

32bit has a 4gig memory address space limit. ALL memory counts for that total including video RAM, and anything else that makes use of that space (memory or otherwise). 32bit Windows (pre Vista) can only address up to 3gig of RAM because it uses the memory address space for other things.

---

