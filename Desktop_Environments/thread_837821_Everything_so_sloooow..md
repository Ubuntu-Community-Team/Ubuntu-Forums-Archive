---
title: "Everything so sloooow."
date: 2008-06-22
forum: Desktop Environments
---

### Post by A Traveller on 2008-06-22
Hi All.

I've just installed (fully, not live) my first Linux OS (Ubuntu 6.06 LTS).

Is it normal that it takes so long to do anything? Whenever I click on any program or anything else for that matter, it takes a good few seconds to load. For example Open Office Word Processor takes about thirty seconds to load. It takes a long time to load even if I close it and immediately try to open it again.

Even simple things like the calculator takes a few seconds to load!

As asked before, is this normal or is something wrong? If a clean, new install with nothing whatsoever added yet is so sluggish, what will it be like when I actually start to use any space or install any programs?

Any help would be most appreciated!

Thanks.

---

### Post by jrusso2 on 2008-06-22
Would help to know what your system specs are.  Processor, graphics and memory at least.

---

### Post by sonofusion82 on 2008-06-22
> **A Traveller said:**
> 
I've just installed (fully, not live) my first Linux OS (Ubuntu 6.06 LTS).


If loading application are slow, it could be due to slow harddisk access. Perhaps you could check if you have harddisk DMA enabled?
[http://ubuntuforums.org/showthread.php?t=16360](http://ubuntuforums.org/showthread.php?t=16360)

Anyway, I am not sure why are you installing version of Ubuntu that is 2 years old. If you want LTS, you can still use Ubuntu 8.04 LTS.
If you have an old hardware (mine machine is > 5years old), you should also use Ubuntu 8.04, if you really need something light due to memory constrains, try Xubuntu.

---

### Post by A Traveller on 2008-06-23
Hi jrusso2. Sorry, it's an old machine (800-850Mhz processor, 256 RAM, Ti200 Card). However, it runs fine in terms of speed on W98SE and since I've always read that one of the advantages of Linux over Windows is that it runs better on old computers, I am wondering why W98SE is performing at a normal speed and Linux is too slow.

Hi sonofusion82. I'll take a look at the DMA thing as soon as I can. I've installed an old version because I had an original disc lying around and I just wanted a taste of Linux. Do Linux versions come with minimum requirements in terms of RAM?

Thanks.

---

### Post by jrusso2 on 2008-06-23
Sorry its going to be slow with 256 mb of ram.  Thats the minimum for Ubuntu.

I would recommend something lighter weight.  Maybe fluxbuntu or Xubuntu.

---

### Post by Sef on 2008-06-23
> Maybe fluxbuntu or Xubuntu

Download [Fluxbuntu]("http://fluxbuntu.org").

Download [Xubuntu]("http://xubuntu.org").

---

### Post by VMC on 2008-06-23
I don't want to stear you away from ubuntu, but have you tried any of the mini distros? Like Puppy or Slax. See how they preform and then you could install one of them, or get an very old Linux distro in the Windows 98 era.

---

### Post by Sawyer_ on 2008-06-23
Try adding

```
127.0.0.1 localhost hostname
```

in your /etc/hosts file.

---

### Post by Excalibre on 2008-06-23
I would agree with the recommendations to try Xubuntu or something (it's an Ubuntu variant that's meant for older equipment) and I would also recommend you use the current version, 8.04.

Note, though, that while generally Linux distributions are probably a bit less demanding than Windows in terms of system requirements, you're comparing a version of Ubuntu that came out 8 years after Win98, when speedier hardware was assumed. There are a lot of flavors of Linux and even several of Ubuntu, and not all of them are designed with yesterday's equipment in mind.

Also, you mention Open Office, and while it's a decent piece of software it's pretty notoriously slow. In my experience it does indeed take a long time to start, even on a pretty fast machine. Everything else shouldn't, though, once you install something like Xubuntu which will use your hardware more efficiently.

---

### Post by tel93 on 2008-06-23
NO NO NO!!! PLEASE never install Xubuntu with those kind of specs. I'd also go against Fluxbuntu because I tried it and it seems really incomplete (not to mention ugly).

Try Debian Testing with XFCE or Openbox. Or CrunchBang Linux 8.04.01 (I stress the version number).

---

### Post by Greyed on 2008-06-23
> **tel93 said:**
> NO NO NO!!! PLEASE never install Xubuntu with those kind of specs.

(Snippage....)

> Try Debian Testing with XFCE or Openbox.

...  Uhm, you do realize that XUbuntu is the XFCE variant of Ubuntu.  So in one sentence you're telling him not to use XFCE and in the other you're telling him to use XFCE.  :confused:

And for the original poster...

> **A Traveller said:**
> Hi jrusso2. Sorry, it's an old machine (800-850Mhz processor, 256 RAM, Ti200 Card). However, it runs fine in terms of speed on W98SE and since I've always read that one of the advantages of Linux over Windows is that it runs better on old computers, I am wondering why W98SE is performing at a normal speed and Linux is too slow.

There are certain physical limitations that no amount of programming will get around.  For example you mentioned that OOo was taking 30s to start up.  On my machine I'd be happy with a 30s startup time for OOo (667Mhz, 256Mb RAM laptop).  I doubt that falling back (rather horribly) to Win95 I doubt there is anything one can do in software to address that issue.  The hard drive only transfers data so fast, the processor only runs so many instructions in a second.

Aside from the loading speed which can have some hardware hiccups (which others have addressed) how does it run once started?  OOo runs fine for me on my machine.  I'm often running Pidgin, Thunderbird and Firefox all under KDE.  Something I imagine most people here would cringe at the mere thought of doing it.  Sure, it's slower than my main machine (AMD 2500+ OCed to 3200+, 1Gb RAM) but it isn't unbearably slow considering the alternative.

---

### Post by tel93 on 2008-06-23
No. Debian XFCE is vanilla XFCE. It is very fast. I'm sure that someone could confirm my point; it is very observable. There is even a huge difference between Ubuntu with plain XFCE and Xubuntu.

In Xubuntu, the developers tried to make their "lightweight" OS resemble GNOME and added all this crap which slows down the system. Not to mention tat it is built on the Ubunut base which is much slower than Debian.

---

### Post by A Traveller on 2008-06-25
Thanks for all the helpful replies. They have been very much appreciated!

Sawyer_, how do I add 127.0.0.1 localhost hostname in my /etc/hosts file and are those the exact words and spaces, etc?

Thanks.

---

### Post by A Traveller on 2009-02-15
Hi again.

As advised, I installed Xubuntu. The Xubuntu was MUCH slower than the Ubuntu. Maybe it could be due to the Ubuntu being an older version and the Xubuntu I installed was the latest one.

So, does anyone know what version of Ubunutu was around at the time of Windows 98SE? The earliest I've managed to find is version 4.10 (2006).

Thanks.

---

### Post by mikjp on 2009-02-15
> **A Traveller said:**
> 
So, does anyone know what version of Ubunutu was around at the time of Windows 98SE? The earliest I've managed to find is version 4.10 (2006).


There was no Ubuntu ten years ago. 4.10 was the first version and it was released in October 2004. 

Try antiX or some other lightweight distro (e.g. Vector Linux). See my signature for more info.

Mikko

---

### Post by yanom on 2009-02-15
this shell command will help you:

```

$   sudo apt-get install icewm

```

icewm is very nice for old computers. You could install it on your Ubuntu with my shell command and login to it instead of GNOME, or get Icebuntu


I tried Fluxbox, it was HORRIBLE.

some people like LXDE or Fvwm-Crystal. The latter I don't recommend.

---

### Post by A Traveller on 2009-02-15
Thanks mikjp / yanom.

I will look into those asap. I haven't got as advanced as knowing what 'shell command' means, but when I do come across it, I'm sure you nice people will be kind enough to point me in the right direction! Haha.

Thanks.

---

