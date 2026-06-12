---
title: "How to see all 4GB?"
date: 2009-01-04
forum: Desktop Environments
---

### Post by jmacdonald801 on 2009-01-04
I know this question has been asked a thousand times, but for me, I have not been able to solve it.

I'm runing 32bit Ubuntu 8.10 on a Dell Latitude with 4GB on ram.

I was running 64bit kernel, and all the ram was visible (free -m).  That was ok for the most part, but even with the new 64bit Flash plug-in, I would still get grey boxes.  Worse yet, for me at least, Java "Client" performance was absolutely abysmal.  I tried a number of 32bit and 64bit JVM's and performance in eclipse wasn't to great.  Under 32bit, using a standard Sun Java 6 "client" VM, It's quite a bit faster.

So I figured, what could be so bad about 32bit?  PAE is not suppose to make any noticeable difference.

Everything works great but I can only see 3283 MB of ram.

This is AFTER I compiled a 2.6.28 kernel with PAE enabled, Highmem (64GB).  I compiled it again and enables 64BIT_RESOURCES, wondering if that would make a difference.

So I'm stumped.  64bit can see the memory just fine, I've got a recent bios that supports up to 8GB ram, but the standard remedies, as in enabling PAE don't seem to work.

I did indeed try the "standard" Ubuntu 8.10 32bit server kernel image.  No difference.  Still can't see all 4GB of ram.

I tried looking for kernel parameters that I might have to enable, and didn't find anyone who was having issues "after" compiling a kernel with PAE.

So at this point I'm asking for help.

Please don't be a zealot and tell me to run 64bit again.  It's got it's issues, and the programs I run don't need to access 4GB in of themselves, but having the full 4GB of ram visible would be nice.

-James

---

### Post by Havek on 2009-01-04
A 32-bit kernal can only see what it can address.  A good explaination - [http://tech.yahoo.com/blog/null/2314](http://tech.yahoo.com/blog/null/2314)

---

### Post by jmacdonald801 on 2009-01-04
> **Havek said:**
> A 32-bit kernal can only see what it can address.  A good explaination - [http://tech.yahoo.com/blog/null/2314](http://tech.yahoo.com/blog/null/2314)

And in turn, I must reply that 32bit operating systems, including linux, have had a way to address up to and over 4GB of memory for some time.  I think my post says I enabled PAE.  It's all over google that people use PAE and/or a combination of highmem support in their kernel, all the time with success.

[http://en.wikipedia.org/wiki/Physical_Address_Extension](http://en.wikipedia.org/wiki/Physical_Address_Extension)

Any body else?

-James

---

### Post by AKoehler on 2009-01-04
Is any of your memory reserved for your video card? You said it was a laptop?

---

### Post by jmacdonald801 on 2009-01-05
> **AKoehler said:**
> Is any of your memory reserved for your video card? You said it was a laptop?

If the bios is to be believed, it says Video Memory: 8MB.

It's an Intel Integrated 945GM (according to bios).

8MB seems unlikely, seeing that I can enable and use Compiz just fine, then again, maybe the memory allocation is up to the video driver since I believe the integrated graphics uses system ram.  That being said, I would expect to see 4096MB available (after compiling in PAE and himem support) but it always reports 3270 (free -m).

Bios says 4096 installed, and 3319 available.  64bit didn't have this issue, it saw all the memory.  Of course I really want to avoid 64bit because of the additional memory usage and the poor Java client performance (server VM is ok).

-James

---

### Post by jmacdonald801 on 2009-01-05
I should add, that upon further reading, it turns out that typically a bios has to support "memory remapping" in order for a 32bit kernel (even with PAE) to see all 4GB of ram.

Now I was hoping there was a workaround for this, but I haven't found anything yet.

-James

---

### Post by binbash on 2009-01-05
[http://ubuntuforums.org/showthread.php?t=855511&highlight=4gb](http://ubuntuforums.org/showthread.php?t=855511&highlight=4gb)

---

### Post by jim_p on 2009-01-05
Go fully to 64bits, not just on the kernel.

Even if you have 64bit flash, you do have 32 bit firefox and that may be causing the grey flash boxes.

---

### Post by jmacdonald801 on 2009-01-05
> **jim_p said:**
> Go fully to 64bits, not just on the kernel.

Even if you have 64bit flash, you do have 32 bit firefox and that may be causing the grey flash boxes.

64-bit firefox with 64-bit flash does cause grey boxes on occasion.  I was sure to remove the npviewer link to the 32bit flash plugin to verify.  I tried 32bit firefox running under 64bit Ubuntu but it's such a pain.  I wanted to install Oracle XE database... and again, another piece of software with no 64-bit binary.  It's just a bloody pain.  64-bit on the desktop, especially a laptop, is dead to me, at least for now.  That's neither here nor there though, I'm just trying to make 32bit work reasonable well for me.

I'm not interested in 64bit kernel, simply for the sake of going 64bit.  It's great on a server platform where you need the memory but doesn't help me on my laptop.  My development platform is Java, which has no good "client" vm for 64-bit as of yet.  At least everything I tried was slow.

Just want all my memory accessible.

-James

---

### Post by richwales on 2009-04-19
I've seen people report that they can see all 4GB of RAM by running the (32-bit) "server" kernel.  Apparently, the server kernel has PAE support enabled.

There are, however, several drawbacks to running the server kernel on a desktop (slower clock-tick interrupt rate, lack of preemption, etc.).

What I don't understand is why the distributed "desktop" kernel doesn't have PAE support enabled.  Would anything in the desktop system be worse if PAE were turned on in the desktop kernel?

---

