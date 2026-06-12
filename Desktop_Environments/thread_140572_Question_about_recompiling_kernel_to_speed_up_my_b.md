---
title: "Question about recompiling kernel to speed up my boot"
date: 2006-03-06
forum: Desktop Environments
---

### Post by IndigoMontoya on 2006-03-06
I am thinking about ways to speed up my boot process.  It seems the longest part is spent on the splash screen that says "Loading modules".  My thoughts are to recompile the kernel (I have some experience doing so, but am in no way an expert - just barely adept) and using makeoldconfig see what is currently being loaded as a module and instead compile it into the kernel.  Which leads me to my questions:

1.  Will this actually speed up that screen?  After this I will experiment with       initNG.  I had used it once on a previous installation and it did not allow me to load my wireless for whatever reason.  I didn't spend much time trying to figure it out; I'm sure it is easily fixable with a good forum search.

2.  Is there a negative to doing this?  ie is a larger kernel bad?  Are some things better to be modules so incase they crash it doesn't bring down the system?  I plan on having my network devices as modules because I prefer to laod them by hand.  But should aything else be a module?  Sound?  Video? (This is a laptop).  I really don't know that much about the inner working (or outer lol) or linux.  Enough to get by I suppose.

Thanks for any tips I get.  Sorry if this was longwinded.

Scott

---

### Post by glug101 on 2006-03-06
Greetings! Welcome to the world of kernel recompiling.  Outside of Gentoo and other source based distributions, this has become something of a black art;)  Personally, I started in the days when compiling the kernel was considered about the hardest thing to do with linux, but it was the only way to get the latest harware drivers :D (oh the insane package dependencies I had to hand load in order to even get it to work!)

Anyway, you choose Ubuntu, and one of the things I love about Ubuntu is that it's a binary package distro that's easy to compile on.

There are few problems with compiling your own kernel, beyond setting up options that you don't understand and creating an unstable kernel.  Such things are rare these days, but I've managed it within the last year. (hint, vesa-ng does NOT work with the old ibm laptops ;) )  I would imagine that compiling in the drivers you need and skipping the modules would speed up your boot times.  There should also be a negligible change in performance (faster or slower, I can't guess).  

Back in the day it was explained to me that compiled in drivers worked faster, but that a small kernel will also run faster.  Distros almost ALLWAYS use modules because it would create an insanely large kernel to have everything in at the same time. (not to mention there would be conflicts)

Whatever you do, I recommend the ubuntu patched kernel source available in Synaptic.  The plain vanilla stuff from kernel.org won't be the same and will likely cause error messages (although the errors will also likely not be very minor).  Another pointer (which you are likely aware of) is to make sure you can dual boot with the stock Ubuntu kernel that you know works.  Otherwise you could end up with a non-booting system looking for a fresh in stall ;)

Hope this helps!

---

### Post by IndigoMontoya on 2006-03-06
Great pointers.  My plan is to look at everything compiled as modules currently and just compile them as part of the kernel.  I will take out a couple things that I know I don't use (like bluetooth, and uh, I don't know what else), but I was concerned with the possibility of making the kernel more easy to crash (if say one of the old modules has a problem, that causes a bigger kernel panis).  Like I said I really don't know much about this sort of thing.  Just feeling it out.

Thanks!

---

### Post by angkor on 2006-03-06
Or you could just wait a month or so and upgrade to Dapper. Dapper's boot speed has increased dramatically compared to Breezy's.

---

### Post by IndigoMontoya on 2006-03-06
touche ;) 

The tinkerer in me wants to do it myself......and now :twisted:

---

### Post by angkor on 2006-03-06
Cool, Have fun! :)

---

### Post by glug101 on 2006-03-06
Sounds like a good plan, just be aware that there are a LOT of options in a modern kernel.  I would actually wager that the first 2 end up locking up at boot, or missing a couple of crucial pieces of support;)  Don't worry, it's part of the learning process.  And don't worry if you compile and then see a bunch of error messages.  As long as everything works, your ok, and having to compile on a modern machine 2 or 3 times (I've heard reports of compilling a kernel in 15 minutes!) is not such a big deal.  

First machine I compiled a kernel successfully on was a P60 (yes, the bug filled grand daddy of the pentium II) and that took 6 to 8 hours, depending on features chosen.  The first 3 failed misreably, but the last one gave dozens of errors at boot and then worked flawlessly and swiftly.  Much faster than the pre-compiled redhat kernel.  

P.S. is your screen name a reference to the princess bride? ('you killed my father, now prepare to die')

---

### Post by IndigoMontoya on 2006-03-07
That is exactly what it is from.  I use it alot in multiplayer games as well.  It is always fun when somebody catches it and says exactly that, "You have killed my father, prepare to die."

I have compiled a hand full of kernels in my days (maybe 20).  So I have some, not quite skill, but experience (almost).  My thoughts are to "make oldconfig" to find out what is currently used by my running kernel and just include everything as part of the kernel (again unless it happens to be something I KNOW I wont use).  I was actually using gentoo for a while, but had a problem and wanted to try out ubuntu before I did the reinstallation of gentoo.  It's amazing how things "just work".

---

### Post by glug101 on 2006-03-07
Personally, I sometimes wax nostalgic for gentoo and how easy it was to compile packages, even ones that weren't part of the distro.  But, yeah, Ubuntu is almost as good for that and I can go from blank HD to a running desktop in less than an hour!

I currently have my brother and my parents running the stuff. (however, my brother was more reluctant.  He had lost his windows install disks and I refused to install it illegally.  WindowsXP just isn't worth it.)

Very fine work that the Ubuntu team does.

---

