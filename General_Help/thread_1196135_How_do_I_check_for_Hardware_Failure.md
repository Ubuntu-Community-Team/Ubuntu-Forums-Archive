---
title: "How do I check for Hardware Failure?"
date: 2009-06-24
forum: General Help
---

### Post by Tindytim on 2009-06-24
I've been having random freezes on my new machine that uses my old Power Supply and Video Card from my previous machine. After doing some reading on the subject, it would appear it's most likely a hardware issue.

Regardless of whether or not hardware failure is the issue, I would like to know what sort of utilities I could use to check for failure of various components.

If you've had the same issue, and it there was something different causing it, I would like to know that aswell.

---

### Post by LowSky on 2009-06-24
random freezes are cause for concern, could be power supply, but I doubt it. Most likely bad memory or hard drive

I think running the SMART utility could maybe diagnose the hard drive, and a Ubuntu Live CD can test the RAM

---

### Post by Tindytim on 2009-06-24
> **LowSky said:**
> I think running the SMART utility could maybe diagnose the hard drive, and a Ubuntu Live CD can test the RAM
Where can I get the SMART utility?

All I can find is a package manager and a utility for OSX (I can't find a Linux version or source).

And I'm about to boot from a Live CD, how would I go about testing my RAM? I don't remember any specific options pertaining to RAM.

---

### Post by Tindytim on 2009-06-24
I just finished Memtest, and after 2 hours I got no errors. I doubted the Memory was the issue, and I doubt the Hard Drives are the issue aswell (I'll test them if I can).

But I suspect my Power Supply is the issue, what methods or utilities could I use to test it's function (or malfunction)?

---

### Post by nice_like_rice on 2009-06-24
I'm no expert, but when I had a similar problem the only way I found to check if it was working was replacing it, and seeing if this changed anything.

(Are you sure the problem isn't overheating, either of the power supply, cpu, gfx? There are many utilities to quickly check this.)

---

### Post by Tindytim on 2009-06-24
> **nice_like_rice said:**
> I'm no expert, but when I had a similar problem the only way I found to check if it was working was replacing it, and seeing if this changed anything.
I don't have any PSU's than can replace it at the moment.

> **nice_like_rice said:**
> (Are you sure the problem isn't overheating, either of the power supply, cpu, gfx? There are many utilities to quickly check this.)
I am. I Checked core temp, and even with the sweltering heat here, I haven't broke 45°C on any of my components that I can test. Not sure about the PSU as I don't have utilities to check it's temps (do they even exist?), but I just checked and it isn't warm to the touch (it was actually rather cool).

---

### Post by Wiebelhaus on 2009-06-24
Run Diagnostics contained on this [UBCD]("http://www.ultimatebootcd.com/")

---

### Post by lisati on 2009-07-07
> **Wiebelhaus said:**
> Run Diagnostics contained on this [UBCD]("http://www.ultimatebootcd.com/")
Thanks for the link - downloading it now (startup troubles on my desktop)

<aside>Gotta fly - Mrs Lisati wants to talk about something unrelated</aside>

---

### Post by c0mput3r_n3rD on 2009-07-07
You can check to see how much power your motherboard, video card etc. need, and how much your power supply is putting out.  But I agree with just replacing it, if you can you might as well, the power supplies constantly are getting better and better the keep up the new hard ware.

---

