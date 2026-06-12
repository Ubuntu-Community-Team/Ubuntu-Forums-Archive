---
title: "All package management software lower priority!"
date: 2008-04-22
forum: Desktop Environments
---

### Post by nullmind on 2008-04-22
I have a few systems I use at work and home with Ubuntu (Hardy and Gutsy), but they share one irritation: Package management operations chug the system! In no event have I had to install an update with haste, but the package manager has the same priority as most of my applications.

Originally I was looking into using AND (Auto Nice Daemon), but this is clumsy considering it will scan ALL my processes. Why scan them all, etc., when I know exactly which ones I want with a different nice value!

I also tried setting some of my core services to less nice, such as my Xorg service, GNOME-stuff, etc., but again this is working in the wrong direction. My desktop applications aren't the problem, the package manager not sharing nicely is! Go back to kindergarten apt!

If my only option (currently) is to create scripts that simply run the command with "nice -x", I will, but that's unfortunate. Is there a way to do this or possibly "override" bash to do this using a simple hash lookup ?

Cheers,
Kris

---

### Post by nullmind on 2008-04-24
Is nobody else having these problems? Does my post not make sense? I really just need a way to have processes start with a different nice value! I know about renice, but as you can see it doesn't fit my needs, as AND (Auto Nice Daemon) didn't.

Cheers,
Kris

---

### Post by kellemes on 2008-04-25
Never used "nice" myself, never needed it I guess.
PM-operations indeed may slow down the system..
I pull in needed updates every other day or so, whenever I don't have anything important to do, this instead of scheduling.
If I'd go for scheduling I'd probably have it done somewhere during the night, knowing it won't interfere with other processes.

So I guess my question is why it's important for you to tweak priorities?

---

### Post by davbslim on 2008-04-25
> **nullmind said:**
> I have a few systems I use at work and home with Ubuntu (Hardy and Gutsy), but they share one irritation: Package management operations chug the system! In no event have I had to install an update with haste, but the package manager has the same priority as most of my applications.

Originally I was looking into using AND (Auto Nice Daemon), but this is clumsy considering it will scan ALL my processes. Why scan them all, etc., when I know exactly which ones I want with a different nice value!

I also tried setting some of my core services to less nice, such as my Xorg service, GNOME-stuff, etc., but again this is working in the wrong direction. My desktop applications aren't the problem, the package manager not sharing nicely is! Go back to kindergarten apt!

If my only option (currently) is to create scripts that simply run the command with "nice -x", I will, but that's unfortunate. Is there a way to do this or possibly "override" bash to do this using a simple hash lookup ?

Cheers,
Kris

This is probably not what you are looking for, but it may help to speed thigs up.  You can do checks weekly bi-weekly or not at all.
[http://www.techthrob.com/tech/updatefreq.php]("http://www.techthrob.com/tech/updatefreq.php")

In alot of cases, scripts are the only way to go.  Unless of course somebody out there created a program that simplifies the process.

Hope this helps

---

### Post by nullmind on 2008-04-26
I am now looking into creating my own solution. Possible ideas include:

[LIST]
[*]Providing a $PATH higher than /usr/bin or other paths, which includes scripts that in turn execute the real targets later in the $PATH list. This may not work because I noticed many processes are started with absolute locations, such as /usr/sbin/synaptic
[*]Overriding the shell environment. Like how sh was "replaced" by dash this would replace the default shell and in turn call the original shell with a different nice value. This may not work for the same reasons as the previous solution.
[*]Manually modify an existing shell or even the kernel to perform this. I don't want to do this.
[*]Using $LD_PRELOAD to allow a shared library to check if the host process should be reniced. If not the shared library would return from the shared library entry point indicating it shouldn't be loaded. This seems like it could have overhead
[/LIST]

Please let me know what you guys think and if these options seem to be heading in the right direction. Anyone interested in developing a solution with me is more than welcome to contact me via my e-mail and (preferred) instant messaging.

Cheers,
Kris

---

### Post by ravon on 2008-04-27
I'm experiencing the exact same symptoms when I'm compiling. The GUI comes to a grinding halt and I can either sit and watch windows redraw or go and do something else. Gutsy handled the exact same hardware just fine.

If you find any solution to this poor scheduler, please let me know.

---

### Post by crazybilly on 2008-07-15
Oh man.  This is my biggest frustration with Ubuntu: updating packages and (worse) running update db slow my system to a crawl.

Ugh.

---

