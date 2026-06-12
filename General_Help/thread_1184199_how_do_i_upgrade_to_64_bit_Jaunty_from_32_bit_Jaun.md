---
title: "how do i upgrade to 64 bit Jaunty from 32 bit Jaunty"
date: 2009-06-10
forum: General Help
---

### Post by SillyKirby on 2009-06-10
I mistakenly upgraded to a 32 bit Jaunty, so now it doesn't recognize my 8 gig of memory. So I need to change jaunty versions. What is an easy way to do this without of course loosing any files or settings?

---

### Post by Therion on 2009-06-10
You can't upgrade from 32-bit to 64-bit, it's going to require a fresh install.

Data will need to backed up of course, any way you wish.  As for config files and settings... I suppose you could use something like QuickStart to make a .tar compressed backup of your .config file and folders and that MIGHT work when you restore them on your fresh install, but I don't know if that's such a good idea or not.

If it were me, I'd suck it up, do a fresh install, and simply learn from the mistake.

---

### Post by Slim Odds on 2009-06-10
> **Therion said:**
> You can't upgrade from 32-bit to 64-bit, it's going to require a fresh install.

I second that motion......

---

### Post by xfearxnxloathing on 2009-06-10
same thing happened to me just haven't happened to do it yet.  LoL

=[
=]

---

### Post by SillyKirby on 2009-06-10
Thanks for the quick response. YIKES. I have an iso backup from remastersys that i did before i upgraded with the adept upgrade prompt. Can i reinstall that then go to the update manager and somehow tell it to do a 64 bit update? I hate to suck it up:) sillly

---

### Post by Therion on 2009-06-10
> **SillyKirby said:**
> Thanks for the quick response. YIKES. I have an iso backup from remastersys that i did before i upgraded with the adept upgrade prompt. Can i reinstall that then go to the update manager and somehow tell it to do a 64 bit update? I hate to suck it up:) sillly
Okay, now I'm confused...

You have a 64-bit .iso backup (I'm assuming of Hardy or Intrepid) that you did using Remasterysys, correct?  If you use that to reinstall, obviously you'll be running whatever version of Ubuntu it is, 64 bit.  You could then do an online dist-upgrade that would leave you with 64-bit Jaunty installed.

I'm about death on online dist-upgrades, personally, but it's your system.  Do as you will.

---

### Post by SillyKirby on 2009-06-10
Therion, thanks for your info. I'm confusing cuz I'm confused. Yes, I have a 64 bit Intrepid .iso image from remastersys that i made today. I will reinstall it, and then try the online dist upgrade, this time being sure to find the checkbox for 64 Bit Jaunty, Then I should be golden, and have the same setup and files i have now in the 32 bit Jaunty i mistakenly upgraded to. Thanks. Silly


> **Therion said:**
> Okay, now I'm confused...

You have a 64-bit .iso backup (I'm assuming of Hardy or Intrepid) that you did using Remasterysys, correct?  If you use that to reinstall, obviously you'll be running whatever version of Ubuntu it is, 64 bit.  You could then do an online dist-upgrade that would leave you with 64-bit Jaunty installed.

I'm about death on online dist-upgrades, personally, but it's your system.  Do as you will.

---

### Post by Therion on 2009-06-10
> **SillyKirby said:**
> Therion, thanks for your info. I'm confusing cuz I'm confused. Yes, I have a 64 bit Intrepid .iso image from remastersys that i made today. I will reinstall it, and then try the online dist upgrade, this time being sure to find the checkbox for 64 Bit Jaunty, Then I should be golden, and have the same setup and files i have now in the 32 bit Jaunty i mistakenly upgraded to. Thanks. Silly
Okay, would you backup for a minute and explain what you had installed, and what you did to get where you are now?  

I ask because if you've only done **online upgrades** this whole time you could NOT have gone from a 64-bit install to a 32 bit install.

It sounds to me like this is the chain of events:  You had 64-bit Intrepid installed.  You then made a backup .iso CD/DVD.  You then did.. What?  An online upgrade?  That would have brought you to a 64-bit install of Jaunty (assuming all went well).  Is that what you did?  Please explain...

---

### Post by Yellow Pasque on 2009-06-10
Are you sure you have 32-bit installed? What does this output?:
```
uname -m
```

---

### Post by SillyKirby on 2009-06-10
All, 
silly@bluetit:~/Documents$ uname -m
i686

silly@bluetit:~/Documents$ getconf LONG_BIT
32

But, While I had always assumed I had a 64 bit Intrepid, I must confess I don't recall checking it. And since I also upgraded my memory from 4 gig to 8 gig today, It may be that I never noticed that I actually had a 32 bit Intrepid. When I reinstall it from my remastersys .iso image, I will check to be sure it is 64 bit. In any case that seems like the best bet.

The upgrade I did today was from an upgrade prompt that appeared in my tray when I restarted the computer. It certainly did not prompt for anything, It just ran with one error that concerned my Hardy CD that was in my adept source file. once I unchecked that and restarted the prompt for update returned and I upgraded. Resulting in a 32 bit system. 

So i guess the best idea, is that I never had a 64 bit Ubuntu to go with my AMD Phenom X4 9650 CPU. thanks everyone. it helps knowing people are willing to help me.

---

### Post by Therion on 2009-06-11
> silly@bluetit:~/Documents$ uname -m
i686
That means you have a 32-bit distro installed. 

Output from a 64-bit distro:```
therion@obelisk2:~$ uname -m
x86_64
```
Once again... My suggestion to you would be download a 64-bit install CD and a perform a fresh install.

---

