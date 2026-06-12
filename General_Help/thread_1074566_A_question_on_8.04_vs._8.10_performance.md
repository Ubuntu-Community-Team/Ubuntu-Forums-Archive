---
title: "A question on 8.04 vs. 8.10 performance"
date: 2009-02-19
forum: General Help
---

### Post by thehuman on 2009-02-19
Hello everyone. I have recently decided to give Ubuntu another try--I was using 7.04 when it was the newest version, and I ran into a few too many problems, so I had to ditch it. Since then, though, I have had a run in with Vista... which, naturally, made me realize there is no future in using MS's OS. I think once XP is too dated to use any more, that might just be the end.

Anyway... I am really liking the newer releases. In just a little over a year, they have come a long way in ease of use. But my problem: I have tried both Ubuntu and Kubuntu 8.10 on my laptop (specs listed below), and the performance with both is pretty bad. I did clean installs of both, installed all the updates, and found that the two main issues that I could not fix were:

1.) Slow redraws. Changing windows, minimizing/maxmizing, everything: just excrutianingly slow. I even disabled Compiz in Gnome and all extraneous effects in KDE, and nothing fixed it. Granted my graphics card isn't the best, but it ran Vista Ultimate with the extra junk turned on just fine, so it should be able to run these.

2.) The file explorers are VERY slow. When I switch from folder to folder in Nautilus, Dolphin, or Konquerer, it takes about a half second to bring up the new folder's window. Of course this isn't a HUGE deal, but it is annoying. I tried turning off indexing, and it didn't really help either.

I also have XP Pro on this machine, and even after six months of use, it still runs super fast. Everything is snappy, and there is no lag anywhere.

Now here's the kicker: just to try another variable, I did a clean install of Kubuntu 8.04. It runs great! Granted, I can't get any windows effects in KDE to work, but the performance, at least, is definitely what I was looking for. No lag anywhere.

So my question: was there something added in to Ubuntu itself, below the Desktop Environments that is slowing me down? Aside from the Intel graphics card, my system is more than adequate to get great performance. And part two of the question: since my testing seems to prove that the problem is in Ubutnu 8.10, and not either of the Desktop Environments, would it be safe (and am I able) to update KDE in 8.04 to version 4? There are some features (namely tabbed browsing in Dolphin) that I am missing from version 4, but I don't want to lose any speed. Any advice on this matter would be greatly appreciated, because I have been banging my head against the wall for two days now, trying to figure out why Ubuntu is lagging.

Anyway, thanks for reading. I know it was kind of long, but I appreciate it.

Laptop specs:
Levono Thinkpad r61
Core 2 Duo 2.4 GHz
Intel Integrated Graphics (not sure on the model number, but it's the one that was released around April last year. It was supposed to be a lot better, but it's still junk)
160GB SATA 7200RPM HDD (30GB for XP, 30GB for Ubuntu, 6GB for swap, and the rest for storage via NTFS)
4 GB RAM (obviously only 3, according to the OS's)

---

### Post by anjilslaire on 2009-02-19
Kubuntu 8.10 includes KDE4x by default, which in my experience brings significant overhead to the OS, and I'm a fan of KDE myelf. BUt, I had to swich to XFCE on my desktop & the Netbook REmix on my Mini to get acceptable (to me) performance.

---

### Post by thehuman on 2009-02-19
> **anjilslaire said:**
> BUt, I had to swich to XFCE on my desktop & the Netbook REmix on my Mini to get acceptable (to me) performance.


Was this switch new for you to 8.10, or have you had to do it with previous releases as well? I too prefer KDE to Gnome, and I'm happy to have it working well now, but I would like to use the newest version. I'm hoping someone knows if/how it will run on 8.04.

Thanks for the reply!

---

### Post by dcstar on 2009-02-19
> **thehuman said:**
> 
...........
Laptop specs:
**Levono Thinkpad r61**
Core 2 Duo 2.4 GHz
Intel Integrated Graphics (not sure on the model number, but it's the one that was released around April last year. It was supposed to be a lot better, but it's still junk)
160GB SATA 7200RPM HDD (30GB for XP, 30GB for Ubuntu, 6GB for swap, and the rest for storage via NTFS)
**4 GB RAM** (obviously only 3, according to the OS's)

I believe that this is 64 bit hardware, have you tried 64 bit Ubuntu versions?

---

### Post by thehuman on 2009-02-19
I considered it, but I was sort of under the impression that the pro's were still somewhat outweighed by the cons.

Frankly, I really just don't know too much about the 64-bit OS. Coming from Windows, I never even thought about it, since there is very little software ready for 64-bit.

Are you thinking it would improve my performance?

---

### Post by Yashiro on 2009-02-20
Probably not amazingly helpful but the upcoming 9.04 Ubuntu release is very fast. Of the dozen or so liveCD's I've tried this month the Jaunty alpha has been the most responsive. 
Granted it still looks disgusting with it's brown and orange theme but that's fixable.

---

### Post by dcstar on 2009-02-20
> **thehuman said:**
> I considered it, but I was sort of under the impression that the pro's were still somewhat outweighed by the cons.

Frankly, I really just don't know too much about the 64-bit OS. Coming from Windows, I never even thought about it, since there is very little software ready for 64-bit.

Are you thinking it would improve my performance?

That comment about "there is very little software ready for 64-bit" may apply to Windows, but not Linux. There is little that is not available now on 64-bit.

Your "impression" about 64-bit is years out of date and utilising the full potential of your hardware can't do any harm to performance issues. Download a 64-bit Live CD and try it.

---

### Post by thehuman on 2009-02-20
> **dcstar said:**
> That comment about "there is very little software ready for 64-bit" may apply to Windows, but not Linux. There is little that is not available now on 64-bit.

Your "impression" about 64-bit is years out of date and utilising the full potential of your hardware can't do any harm to performance issues. Download a 64-bit Live CD and try it.

Alrighty then. That's the kind of firm advice I like! I'll give it a try this weekend (maybe I'll combine advice and try and 64-bit version of Jaunty as well).

Thanks for all the advice and help. I will update the thread when I get to chance to try Jaunty/64 and see what happens.

---

### Post by anjilslaire on 2009-02-21
> **thehuman said:**
> Was this switch new for you to 8.10, or have you had to do it with previous releases as well? I too prefer KDE to Gnome, and I'm happy to have it working well now, but I would like to use the newest version. I'm hoping someone knows if/how it will run on 8.04.

Thanks for the reply!

It was new with 8.10. Previously on 8.04 and earlier, I ran KDE3.x

I'll probably try it again with 9.04.

---

### Post by Yashiro on 2009-02-21
> 1.) Slow redraws. Changing windows, minimizing/maxmizing, everything: just excrutianingly slow. I even disabled Compiz in Gnome and all extraneous effects in KDE, and nothing fixed it. Granted my graphics card isn't the best, but it ran Vista Ultimate with the extra junk turned on just fine, so it should be able to run these. If it's excruciatingly slow then it's almost certainly a video driver issue. 

> 2.) The file explorers are VERY slow. When I switch from folder to folder in Nautilus, Dolphin, or Konquerer, it takes about a half second to bring up the new folder's window. Of course this isn't a HUGE deal, but it is annoying. I tried turning off indexing, and it didn't really help either.
Linux file browsers are very slow, yes. They are getting faster but the never feel as snappy as windows.

---

### Post by jamesnmandy on 2009-02-21
> **Yashiro said:**
> Probably not amazingly helpful but the upcoming 9.04 Ubuntu release is very fast. Of the dozen or so liveCD's I've tried this month the Jaunty alpha has been the most responsive. 
Granted it still looks disgusting with it's brown and orange theme but that's fixable.

have they fixed the USB 2.0 support issue in it?

---

### Post by Yashiro on 2009-02-21
No idea what you mean by this. USB2 works fine here on Hardy.

---

### Post by jamesnmandy on 2009-02-21
i am talking about the many many threads here and abroad about how USB 2.0 support appears to be broken since a few releases ago....gimping USB 2.0 hard drives and memory sticks to USB 1.0 speed (1Mb/s)

lots of people are still waiting on a fix, including me, i simply cannot stand to put up with it taking two hours to transfer a 7Gb file from my external HDD to local....that took all of maybe 10-15 minutes tops on my windows machine with the identical hardware, right down to using the same cable and port for the external drive

---

### Post by Yashiro on 2009-02-21
Maybe test it on a LiveCD with a newer kernel. 
[http://cdimage.ubuntu.com/releases/jaunty/alpha-4/](http://cdimage.ubuntu.com/releases/jaunty/alpha-4/)
or if you're very brave try a kernel from here [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

I've not encountered that issue but I don't rely on using my ports fulltime. Speeds when I do use them are fine though (20-30mb/s, cruddy nforce4 board).

---

### Post by jamesnmandy on 2009-02-22
> **Yashiro said:**
> Maybe test it on a LiveCD with a newer kernel. 
[http://cdimage.ubuntu.com/releases/jaunty/alpha-4/](http://cdimage.ubuntu.com/releases/jaunty/alpha-4/)
or if you're very brave try a kernel from here [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

I've not encountered that issue but I don't rely on using my ports fulltime. Speeds when I do use them are fine though (20-30mb/s, cruddy nforce4 board).

newer than the latest stable release?  thats what i have, i only installed this freshly a few days ago....so it's the latest stable one, 8.10 Interpid Ibex i believe is what they call it

lots of people are reporting a few versions older fixes it, but nothing since then works right with USB 2.0 devices, it could be just a certain number of chipsets have the issue, i dont know, perhaps Nvidia chipsets are one of the few that work fine

i say this because 8.04 may not have USB issues where the latest release does

---

