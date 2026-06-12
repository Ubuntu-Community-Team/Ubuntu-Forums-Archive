---
title: "[SOLVED] kernal panic - ubuntu won't startup"
date: 2009-01-07
forum: General Help
---

### Post by rmausser on 2009-01-07
Hey guys.

Welp, somehow today my computer decided to Brick on me. 

I am running Ubuntu Studio on an HP Pavilion dv2000 laptop.

I was trying to install LiVes from getdeb.net when it said that it couldnt install all of the dependencies.

Then my computer froze with the blinking caps lock key.

When I try to reboot my machine, the system hangs and the caps lock key flashes, and the message:

> /sbin/init:error while loaded shared libraries:libc.so.6: wrong ELF class: ELFCLASS32 [6.590651] Kernal Panic -not syncing: Attempted to kill init!

appears. 

Trying different Kernels and the Rescue modes do not work. Same message.

Someone please help! I have some important data on my machine and I need it working. 

I'm willing to pay someone with paypal to help me fix it if interested, I really need it fixed!

Thanks so much.

Rob

---

### Post by dcstar on 2009-01-07
> **rmausser said:**
> Hey guys.

Welp, somehow today my computer decided to Brick on me. 

I am running Ubuntu Studio on an HP Pavilion dv2000 laptop.

I was trying to install LiVes from getdeb.net when it said that it couldnt install all of the dependencies.

Then my computer froze with the blinking caps lock key.

When I try to reboot my machine, the system hangs and the caps lock key flashes, and the message:
.........

Try booting off a Live CD and copy the file mentioned there onto your hard disk.

Just because packages are available for Debian systems does not mean that they work on Ubuntu systems.

---

### Post by thedarkwinter on 2009-01-07
Are you running a 64bit installation? Because that library is 32bit and the error looks to me like (from my limited exp) like architecture problem.

if you do have important data, i would recommend that you boot a live CD and back up your data before doing any damage.

---

### Post by rmausser on 2009-01-07
hey, yes I am running 64 bit Ubuntu Studio.

I occasionally install 32 bit apps with --force-architecture when there is no 64-bit version available. 

How can I most easily solve this? should I just remove that dependancy?

---

### Post by rmausser on 2009-01-07
FIXED... phew that was hairy for a while. 

Basically I had installed a 32-bit program that reinstalled some system lib files that the kernal and the rest of my 64 bit Ubuntu didnt like very much. Libc6 was affected, so I reinstalled it off the Live CD. This in turn created more lib errors, which I replaced, and then this replacement created more errors. 

I was starting to realize that a reinstall was on its way (which would stink, this is my studio comptuer and I JUST got Flash CS3, Reason 3, my midi controllers and everything working after 4 weeks straight of working on it)

So I was like "well if its broken, lets break it some more and see what happens." So I copied the entire Libs folder from the Live CD and replaced all of the Libs files in my broken OS.

And Voila! It works. 

It...actually works better...it boots up a lot quicker...which I am scared of a bit...im sure some problems are going to need to be fixed and patched...some programs reinstalled, but for now it works. IT WORKS!!!  

So, lesson learned, be careful with forcing 32 bit programs on 64 bit OS

Thanks everyone for the help.

how do I mark this as SOLVED?

---

### Post by albinootje on 2009-01-07
> **rmausser said:**
> 
It...actually works better...it boots up a lot quicker...which I am scared of a bit...

Hmm. Interesting. I wonder why that is.
> 
how do I mark this as SOLVED?
It should be under the "Thread tools" at the right top of this thread.

And congrats with fixing it yourself. Well done!

---

