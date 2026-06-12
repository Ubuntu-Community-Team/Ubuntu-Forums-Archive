---
title: "Linux on old computer(Lubuntu with Openbox)"
date: 2013-04-30
forum: Desktop Environments
---

### Post by adrian89 on 2013-04-30
I want to revive an old pc P2-P3 don't know the model(it is not for me and the ideea just poped in my head) of it around 128 or 256 MB of ram.The point is that the person is old and is using computer just for documenting on things,most for history and I am thinking of installing lubuntu with openbox,is it ok if I use it this way?I want to get as much "juice" from the pc as I can get.

---

### Post by snowpine on 2013-04-30
You could probably find a computer with much better specs for low cost/free from: Craigslist, Freecycle, family, friends, co-workers, or in the trash. I personally will not even touch hardware unless it has pentium 4 (or, preferably, better) and minimum 1gb ram; anything less goes off to the recycling center. 

Here is a discussion of Ubuntu family on old hardware: [http://ubuntuforums.org/showthread.php?t=2130640](http://ubuntuforums.org/showthread.php?t=2130640)

I especially do not think that an elderly person with no Linux experience is up to the challenge of running Openbox on antiquated hardware; this sounds like an exercise in frustration to me. However, if you are a Linux expert prepared to do a lot of hand-holding when the inevitable tech support questions arise, then go for it! We have some older users on these forums who will tell you how great Linux can be for seniors. :)

---

### Post by adrian89 on 2013-04-30
Ok,thank you for your response,that was my first thing I said when I saw it, but I let the owners decide what to do with it,but today it poped in my head....."What if I install Lubuntu and then use it with Openbox".The problem wasn't about learning, they're not that old :D(around 60's) and all they needed to do with it is :Start/Shutdown, Browser opening and in some exceptionally cases write on office which they know already.:).But again,thank you

---

### Post by VanillaMozilla on 2013-04-30
> **adrian89 said:**
> "What if I install Lubuntu and then use it with Openbox"
I don't know what you are trying to accomplish.  Lubuntu uses OpenBox by default.  Lubuntu is the Ubuntu release of the LXDE desktop, which uses the OpenBox window manager already.

If that computer really has only 128 or 256 MB of memory, that's really not enough.  I routinely run Lubuntu in 384 MB, and that's OK.  256 might be adequate for really small stuff, but it's probably not going to be very nice.

Be prepared to spend a few hours customizing just the basic system.  On my system, for example, I still don't know how to do some basic stuff like searching for files (it wouldn't be hard to fix this, but you have to get around to doing it).

There's another problem.  That computer lacks PAE, and unless you are willing to jump through hoops, you can't install a currently supported Lubuntu on it.

But I agree, Lubuntu is nice in low-memory situations.  In particular, the system UI often works well even during heavy memory swapping, in situations where others bog down.  It has some other very nice, and sometimes unique features too, for those who are willing and able to explore the computer.

---

### Post by mörgæs on 2013-04-30
> **VanillaMozilla said:**
> That computer lacks PAE...

No, all Pentium 2 and 3 have PAE, but as mentioned above it's simply too slow to be of any practical use.

---

### Post by ibjsb4 on 2013-04-30
It seems you never really know until you try it.

[http://ubuntuforums.org/showthread.php?t=2140653](http://ubuntuforums.org/showthread.php?t=2140653)

---

### Post by VanillaMozilla on 2013-04-30
> **mörgæs said:**
> No, all Pentium 2 and 3 have PAE, but as mentioned above it's simply too slow to be of any practical use.
I thought my Pentium III did not have it, but it turns out you are correct.  I now have it installed and running fine.  Thanks.

Just for reference, I just rebooted, and Lubuntu uses 146 MB (or MiB? -- whatever the 'free' command shows) immediately.  That seems a little high.  I would expect maybe 110, but this is a hybrid system, with maybe some Ubuntu components running.  The computer has 384 total.  Now, with Firefox running and only this site open, it's using 242 MB or MiB.  With Abiword also running, it's 264, or 253 after closing.  With LibreOffice running, it's 270, and after closing, it's back to 244, and now 234.  And it's OK to use with a little swapped memory.

So what the heck.  I guess I changed my mind.  If you can muster 256 MB, give it a try.  Lubuntu is beautiful -- my favorite system on older machines.  For really low memory, there's DSL and maybe Puppy, but I think those are comparitively rather primitive.  But I wouldn't foist it off onto other people before you've really given it a shakedown yourself.

---

### Post by claracc on 2013-05-01
I have lubuntu 12.04 installed on 1 GHz PIII laptop, 512 MB RAM, 64 MB sis 630/730 graphics card and 20 GB HDD. Lubuntu makes this ancient (2002) laptop still usable to play music, surfing web and office tasks.

One recommendation, although I have installed firefox on it, I prefer to use chromium to surf web since it consumes less resources. About office software abiword 2.9.2 has serious drawbacks since the forementioned release consumes a lot of RAM and CPU, so it is advisable to try libreoffice or apache openoffice in order to see more efficiency.

The only problem is when I tried to upgrade from lubuntu 12.04 to 12.10, the laptop is affected by a bug ( [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-mach64/+bug/1077975](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-mach64/+bug/1077975) ) which makes the system unusable. Still waiting a patch,  although the bug affects few people, I am not sure it will be fixed.

Anycase, I agree with you, I think lubuntu is one of the best OS to make usable old computers with low specifications.

---

### Post by adrian89 on 2013-05-02
> **VanillaMozilla said:**
> I don't know what you are trying to accomplish.  Lubuntu uses OpenBox by default.  Lubuntu is the Ubuntu release of the LXDE desktop, which uses the OpenBox window manager already.
 
Well i said Openbox because I installed it  on a server and use it as DE(selection from session selector at starting screen), do not ask why I have a DE on a server :D........learning purposes,experiments, etc.

Thank you for all interventions :).

---

### Post by irw on 2013-05-02
I recently discovered [Bodhi]("http://www.bodhilinux.com/") - ubuntu base with Enlightenment - this has worked well on a low spec sytem I tried it on.

The website lists min spec as: 300+MHz CPU, 128MB RAM, and 2.5GB hard drive space

---

### Post by VanillaMozilla on 2013-05-02
One other thing.  I got a little confused between the PAE kernel and the NX bit.

The main function of the PAE kernel is to get address extension beyond 4 GB.  The second function is that it gives you the NX (No data eXecution) bit.

That old processor has pae capability, but not much memory, and no NX bit capability.  Consequently, I believe there is no reason to run the pae kernel on an old Pentium II or III.  Since it uses a more complex addressing scheme, theoretically it may run a little more slowly than the non-pae kernel.  It probably will be installed by default with whatever new version you install, but once it is installed, you can probably install the non-pae version instead.

---

