---
title: "Video Re-encoding Problems"
date: 2006-07-22
forum: Desktop Environments
---

### Post by boywondr16 on 2006-07-22
I'm getting thisclose to punting Breezy alltogether and going back to freakin' Windoze ME, because at least I'd get something out of re-encoding video files.

I have reinstalled Dapper six times since first starting to use it because each time, somewhere along the line, Avidemux and the Video Convert script in Nautilus begin crashing in the middle of re-encoding XviD and DIVX files to DVD compatible mpegs.

The longest I've been able to go with Dapper actually handling this job without reinstalling has been three weeks.  

I've been looking at Linux for a year in an effort to keep a pc running well without having to purchase anything else.  The last Windoze mode it'll handle is ME, which is like openly inviting people to sneak in and take it over.

I've spent too many weekends, especially, on this issue.  Can someone help me figure out what's going on that Dapper doesn't like?

---

### Post by boywondr16 on 2006-07-25
Hello? Anyone?

---

### Post by JoWilly on 2006-07-25
What version of avidemux are you using (I am always getting the latest one from the avidemux website an compile it myself with all the features I need).

Why do you use a nautilus script ? You can just load the file in avidemux, select dvd mpeg for video, mpeg2 for audio and mpeg+PS as container; nothing else needed. It works everytime here.

---

### Post by boywondr16 on 2006-07-25
I compiled the latest Avidemux today, having done a fresh install of Dapper on Sunday--2.1 branch.

The nautilus script was as a test while having issues, 'cause I'm trying to find something that works.  Only, at this point, nothing seems to.  Devede, tovid, etc.; everything crashes at some point while encoding.

---

### Post by JoWilly on 2006-07-25
> **boywondr16 said:**
> I compiled the latest Avidemux today, having done a fresh install of Dapper on Sunday--2.1 branch.

The nautilus script was as a test while having issues, 'cause I'm trying to find something that works.  Only, at this point, nothing seems to.  Devede, tovid, etc.; everything crashes at some point while encoding.

If you start avidemux in a terminal (shell), what is the output when it crashes ?

Also, have you tried to report the crashes on the avidemux forum ? The author is always around and very helpfull to fix things asap.

---

### Post by boywondr16 on 2006-07-26
Here's the output from terminal...

```
Mpeg12 settings:
____________
FF Max rate   (header) : 8000 kbps
FF Buffer Size(header) : 1966080 bits / 240 kB
FF Max rate   (rc) : 8000 kbps
FF Buffer Size(rc) : 1966080 bits / 240 kB
FF GOP Size    : 12
[mpeg2video @ 0x8477028]removing common factors from framerate

[mpeg2video @ 0x8477028]rc buffer underflow
 ffmpeg Encoder , w: 352 h:240 mode:1Images stat:___________Max memory consumed (MB)     : 1608
Current memory consumed (MB) : 1608
Max image used               : 13
Cur image used               : 14
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb71c0463 in __waitpid_nocancel () from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb7796485 in g_on_error_stack_trace () from /usr/lib/libglib-2.0.so.0
#3  0x08059b41 in sig_segfault_handler (signo=11) at main.cpp:224
#4  <signal handler called>
#5  MPV_motion (s=Cannot access memory at address 0xffc74814
Memory stat:
Images stat:___________Max memory consumed (MB)     : 1608
Current memory consumed (MB) : 1608
Max image used               : 13
Cur image used               : 14
Global mem stat
        Memory consumed :8 (MB)

 Goodbye...

```

---

### Post by boywondr16 on 2006-07-26
So, given that result, I ran memtest86+ and about 74% in began getting red-scrolling results and the memtest didn't advance beyond that...

Looks like I'm doing some shopping, then will try again...I was surprised at how hot the unit was when I opened it up fully, considering I have one side partially open from my last hardware work and one inbound fan and one outbound, but, who knows...

I just know I don't need to be looking at a new box...

Am I on the right track here?

---

### Post by exif on 2006-07-26
Your RAM is defineatly faulty if memtest is turning it red. I would look into replacing it. RAM is fairly cheap these days.

---

### Post by JoWilly on 2006-07-26
> **boywondr16 said:**
> So, given that result, I ran memtest86+ and about 74% in began getting red-scrolling results and the memtest didn't advance beyond that...

Looks like I'm doing some shopping, then will try again...I was surprised at how hot the unit was when I opened it up fully, considering I have one side partially open from my last hardware work and one inbound fan and one outbound, but, who knows...

I just know I don't need to be looking at a new box...

Am I on the right track here?

Yep, that was a good idea to check the ram...

Summer is once again very hot this year. Speaking only for hard disks, I have 4 disks in my system, gnome sensors is showing that 1 of them is running at 69°C non stop (should be 50°C), this is crazy for a HD... I don't even want to imagine the rest of the system.

---

