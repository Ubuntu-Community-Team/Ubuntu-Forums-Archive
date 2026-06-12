---
title: "Debian Sid - what does &quot;broken&quot; mean?"
date: 2008-05-20
forum: Debian
---

### Post by oaul on 2008-05-20
If you want to skip my rant just scroll down to the bottom where i finally ask my question.  
I have used debian sid (100% binary reps) for a few months now.  So far I love it.  I have read *countless* warnings, however, that say it "breaks".  I am very worried about Sid breaking on me and rendering my system unusable.  What the heck does break mean? 

One website says a package is broken if any of these apply:
1 - Package has broken dependencies
2 - Package can't be installed altogether
3 - Package behaves abnormally.  

But what about broken SYSTEMS??? I can't even count how many random posts that say "its only a matter of time before your sid desktop breaks. You'll be back using ubuntu in no time"  But just how severe are these breaks?  Nobody gives a f**king example (well, most people don't).

I have scourged around the internet looking for specific examples of Sid breaking a system and causing brown paper bag moments:
-grep won't function.  Boot process hangs. 
-some library related to logging in 'breaks', preventing any logins. 
-dpkg goes rogue while setting up package X and starts forcing recursive removes in /.

But thats about it.  Sure, i suppose i have experienced "breaks" - but they're far less severe and easy to fix (or wait for a fix):
- .config for 2.6.25 doesn't have support for legacy /proc/acpi dirs.  Battery meter won't work unless you enable the option and recompile
- xorg 7.3 changed the way SendCoreEvents works for non core pointers.  Mice won't work from a 7.2 xorg.conf
- Some python-based packages (miro) couldn't be installed for a DAY OR TWO after the transition to python2.5.

These examples are hardly reason for me to worry.  I've checked the Debian mailing lists and anything "broken" seems pretty easy to fix and similar to my experience of the severity of "broken" ubuntu packages:
-pypanel won't run after installing (python xlibs were at fault)
-.config in 2.6.24 headers package has NO SOUND DRIVERS ENABLED :confused:
-"waiting for root partition" if using mkinitramfs on a new kernel boot (using update-initramfs instead worked for me)

My question : Does anybody have a nightmare story or know of one where a bleeding edge distro (recent Ubuntu or Debian sid) made your SYSTEM UNUSABLE in any way?  (Please avoid 'X won't start'-like posts unless you can convince me that the distribution was at fault - be it a packaged kernel update, etc.).

---

### Post by K.Mandla on 2008-05-20
Moved to Debian subforum.

---

### Post by jdhore on 2008-05-20
Here are a few from me:

1. When the 2.6.20 and 2.6.21 kernels came out with the paravirtops/nvidia bug, it was never fixed until 2.6.22 so that was a big pain.
2. I ran into the grep issue that you stated above
3. When Xorg 7.3 first hit Sid, i couldn't get it to start X AT ALL...Tried with no xorg.conf, tried with 5-10 different variations of my 7.2 xorg.conf, tried with recompiling the nVidia binary driver and doing nvidia-xconfig, tried pulling the xorg.conf from Fedora 8 with Xorg 7.3...and more (i forget how much)...This was without a doubt the fault of the new xorg...

I'd say, if you wanna run Debian, run Testing...It's quite up-to-date and it has very few issues...

---

### Post by anystupidname on 2008-05-20
I've had plenty of borked package problems and errors from apt (sometimes a PEBCAK issue or just a known problem) but always managed to rectify the problem with good old fashioned troubleshooting. Debian and Ubuntu are the most damn stable OSes I've ever worked with... After rereading, I see that you're specifically talking about the unstable releases. I've run sid before but most of the time I run testing so I guess nevermind this post...

---

### Post by kerry_s on 2008-05-20
+1 stability & up to date lenny/testing is the way to go. i haven't had no problems, nothing, nada, and there's been updates at least every other day. the kernel update was flawless, runs like a champ.

---

### Post by oaul on 2008-05-20
Yeah i've been a lenny/testing user for 1-2 years since i migrated to unstable on my laptop.  I agree with the stability and up-to-dateness of lenny, but i got frustrated with some packages that haven't made it into testing after 180 days +.  And as strange as it may seem, "good old fashioned troubleshooting" when something goes wrong keeps me on my toes.  I prefer unstable (though i say that cautiously because it's only been three months). 

> 2. I ran into the grep issue that you stated above
I just pulled that grep example from a Debian Sid faq.  I know nothing about it.  Would you mind elaborating?  How did you fix it?  Was grep the problem or the Std. C library, etc.?  

Keep 'em coming. Thanks

---

### Post by p_quarles on 2008-05-21
While I wouldn't highly recommend it for any kind of mission critical computer, you might take a look at Sidux. It is based on -- and uses the repositories for -- Debian Sid, but includes a number of fixes and stability measures that make it more suitable for actual usage (Sid is simply not intended to be used in any ordinary sense).

---

### Post by jdhore on 2008-05-21
> **oaul said:**
> I just pulled that grep example from a Debian Sid faq.  I know nothing about it.  Would you mind elaborating?  How did you fix it?  Was grep the problem or the Std. C library, etc.?  

Keep 'em coming. Thanks

I don't bloody remember...It was a long while back and it was a pain.

---

### Post by RedSquirrel on 2008-05-21
> **oaul said:**
> I have used debian sid (100% binary reps) for a few months now.  So far I love it.  I have read *countless* warnings, however, that say it "breaks".  I am very worried about Sid breaking on me and rendering my system unusable.

I read similar warnings when I was looking into sid. In my view, an acceptable solution is to run a dual- or multi-boot system so that you have a fallback OS at your disposal (in case you were working on something important).

Even if I did not dual boot, I wouldn't be too concerned. Debian is easy to install, as you know. For me, if a major catastrophe occurred and a full reinstall was necessary it wouldn't take more than a few minutes. I keep all of my personal files on a separate partition (and backed up elsewhere), so restoring to the point where I can get back to work is not very difficult.

---

### Post by kevCast on 2008-08-25
```
#nano /etc/apt/apt.conf
```

In this file, type the following:

```
APT::Default-Release "testing";
```

It will still pull things from sid, but it will focus mainly on testing. Just watch those sid dependencies.

---

### Post by SunnyRabbiera on 2008-08-27
Well actually debian sid can be made stable if you dont use all the experimental crap.
On sid I usually use the testing repositories

---

### Post by oswaldkelso on 2008-09-03
The best description of Debian Sid that I've ever seen. Enjoy.

"It's your machine, after all. Just don't cry if it breaks."

[http://wooledge.org/~greg/sidfaq.html](http://wooledge.org/~greg/sidfaq.html)

---

