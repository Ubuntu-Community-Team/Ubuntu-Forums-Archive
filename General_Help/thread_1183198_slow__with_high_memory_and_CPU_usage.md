---
title: "slow  with high memory and CPU usage"
date: 2009-06-09
forum: General Help
---

### Post by coolhandluke on 2009-06-09
Hi.

Hoping someone can give me some _specific_ help with this.

Ubuntu 8.1, Kernel Linux 2.6.27-14-generic, Gnome 2.24.1
Memory: 502.1MB, CPU: Pentium 2.20GHz
Available disk space: 27GB
Laptop.

When starting or actioning a process (whether that's opening an app, or clicking a link!) there is a 50/50 chance the pc will take an age to carry the action out. Momentary screen blackouts etc.

I believe the issue stems from the fact that (within the System Monitor) my CPU is often at >80%, my mem is usually between 65-80%, and even my swap hovers at about 22%.  All this while I perhaps only have a f.fox browser open and am surfing, or maybe a file browser window and a doc. or two.

The reason for reconsidering XP is that Ubuntu gives me (the layman) no way to correlate the seemingly high demand with a process, so in no way am I better off with Linux. System Monitor is useless, as is free and htop - the stats seem relatively normal and _none of these give me a direct avenue for finding the fault_.

Ubu. has been great in many regards but I'm totally frustrated with this issue.

Cheers if you can help.
Matt

---

### Post by Tipped OuT on 2009-06-09
Not the operating systems fault, you just have a slow PC. Try Xubuntu.

---

### Post by sdennie on 2009-06-09
That sounds very much like what you would see on a system without a lot of RAM and a slow disk that is swapping to disk a lot.  Using Xubuntu or something even more lightweight might help but, you could also try setting your swappiness to a lower value.  After rebooting try:

```

sudo sh -c "echo 0 > /proc/sys/vm/swappiness"

```

If that makes a difference you can make that permanent by adding the following to the bottom of /etc/sysctl.conf:

```

vm.swappiness=0

```

(As a side note, it's generally not necessary to threaten to return to Windows if you don't get a satisfactory answer on these forums.  People will help if they know the answer and the threat may actually be a deterrent to getting the help you need)

---

### Post by rlj1965 on 2009-06-09
You have a Pentium 2.2 with only 1/2gig of ram. What can you expect from any OS? OK, so maybe you want to preserve this machine before you upgrade. At a minimum, add RAM and switch to Xbuntu since its more lightweight in the resource department. I'd be surprised if XP runs well with that hardware. MS said 1GB Ram was a minimum for XP.

Good Luck.

---

### Post by coolhandluke on 2009-06-09
Thanks for prompt feedback.
**sdennie:** > ..try setting your swappiness to a lower value..
Tried this and yes - swap reduced to ~0.4%.
Havent been able to add line to file as I'm not root(?). Not sure how to do that (safely) yet...  Still have slow performance though.

> ..threaten to return to Windows..
Good point. Not meant as a threat but as a feedback to the 'powers that be' - but perhaps another forum...

**All:** re switching to Xubuntu.
True, 500MB isn't great but it should be adequate for what I'm using it for. And isn't that one of Linux's selling points? That its processes aren't so resource hungry..?

Windows XP ran fine on this machine, and more importantly, Ubuntu was ticking along nicely until a few weeks ago when this 'speed' issue started. In fact I previously had it set up with all the fancy desktop settings which I've since removed. So I know it *can* work fine.  So you say: "what did you change a few weeks ago Matt?". Well, nothing. Or maybe I downloaded something during regular use which is tying up resources, or a virus etc.. I doubt it but who knows?

And that's where my frustration stems from.  Without being a Linux guru, I have pretty much no way of finding out what it is, specifically, that's tying up my memory.  If was running some major apps - then sure I'd need to upgrade.  But just a browser?! As I type this (with only ffox running), my mem is at 85% - that just doesn't make sense.

Cheers

---

### Post by infallible on 2009-06-09
For me, this problem on a number of systems has been the graphics portion of the OS, xorg. Try 'top' in a terminal to see the processes that the system monitor won't show you to get a better idea of where trim the fat. Disabling the window effects helped a lot for me, but a newer video card helped a lot more.

---

### Post by jbruced on 2009-06-09
Wow, weird.

I'm no guru, but can I suggest trying launchpad.net, the Ubuntu section?

In the past I got some real smart geek types to give some short qualified answers to this kind of deep issue.

GL
Bruce

[edit] I've got 512MB on an old PC and mine screams(as in good), something's wrong there.

---

### Post by DeMus on 2009-06-09
> **coolhandluke said:**
> Hi.

Unless someone can give me some _specific_ help with this, I'm back to XP. Better the devil you know etc...

Ubuntu 8.1, Kernel Linux 2.6.27-14-generic, Gnome 2.24.1
Memory: 502.1MB, CPU: Pentium 2.20GHz
Available disk space: 27GB
Laptop.


In a thread some days ago people also complained about Ubuntu being relatively slow compared to Windows, so did I.
I have an old P3-600MHz laptop with 256MB ram and using XP it is a nice computer, trying out Ubuntu or Xubuntu makes me drink a lot of coffee.
I've always heard Linux is better on older computers but this simply is not so. When I write this I get answers like:
XP is 8 years old, Jaunty 1 month: you can't compare those two.
Why not? What is the difference? They are both OS's with GUI's.
No, when using old(er) computers you have to use an OS like Damn Small Linux, or another very small OS (forgot their names).
Yes, I also still have DOS 6.2 disks here which I can use. Is that what I want? No, I want a GUI. So why tell me I have to use Damn Small Linux?

I love Linux, especially Ubuntu which I use for more than a year now. I'm Windows free and hope to stay that, but I know I have to keep upgrading my computer to keep up with the OS.

---

### Post by coolhandluke on 2009-06-09
Thanks again for the responses.

Perhaps (jbruced) this would be better in a Launchpad forum. I'll switch to that and see what happens. Although I, and many other threads, agree; 512MB on an old pc shouldnt be a problem.

My understanding though was this:
MSWindows, with each application, puts a .dll type file in just about every system folder which makes removing apps and tracing problems a bit of a nightmare.
Linux instead places its apps in a folder. Obviously there's overlap with dependancies, but not to the extent of Windows.  This should go some way to increasing the transparency of the OS, ie cause & effect.

If that's so, then when a process is causing a problem, surely the much touted transparency of the Linux OS would enable you to see where the problem was coming from..?

So while I agree you need the right machine for the job, it's not so much an issue of upgrading to a more powerful machine but being able to identify the cause of my issue. (Why would I want to upgrade my memory or 'downgrade' to Xubu. when I have previously had Ubu. running fine.?!)

terminal: 'top' does show Xorg consuming a fair chunk of the memory. But that could be the norm for this pc... Unfortunately I don't have an idea of what its requirements were a few weeks back when it all was well to compare.

I can see this going a little off topic - even with my lousy subject header (right machine for the job vs IDENTIFYING THE CAUSE OF A SYSTEM ISSUE).
In my happy place, I can see myself opening the system monitor (or receiving a warning notice) and it reporting to me that "resources for 'Application A' have been running at 300% > the average for the last 3 months", with options for correction etc. Or better yet "Oi! Reinstall App A 'cos it's buggered". Dreaming, I know.

Thanks all

---

### Post by DeMus on 2009-06-10
You say TOP shows Xorg eats away a fair chunck of the CPU. Can it be you don't have the right driver installed for your video-card, making the CPU do a lot of work the GPU would normally do?
Take a look at that (and hope for the best)

---

### Post by coolhandluke on 2009-06-10
Hmmm, have run hardware and driver tests with nothing to report. Will try to tinker with it and see what happens though.

---

### Post by coolhandluke on 2009-06-10
So I'm wondering about my graphics driver...
Terminal command (~$ lspci -x | grep -i "vga\|display") shows:
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]

The driver was initially automatically recognised by Ubu. and has always worked fine. Like I said, the performance problems only started a few weeks ago and I've made NO changes to the driver settings. I've only turned off Compiz effects..

But, when I check **System ->Admin-> Hardware Drivers**, there are no drivers listed. Its only wants to list _proprietary_ drivers, but I'd have thought ATI is proprietary - so shouldn't it be listed..?

Any ideas on how I can check and perhaps reinstall the video driver?  Hoping that might reset things...

---

### Post by DeMus on 2009-06-10
> **coolhandluke said:**
> So I'm wondering about my graphics driver...
Terminal command (~$ lspci -x | grep -i "vga\|display") shows:
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]

The driver was initially automatically recognised by Ubu. and has always worked fine. Like I said, the performance problems only started a few weeks ago and I've made NO changes to the driver settings. I've only turned off Compiz effects..

But, when I check **System ->Admin-> Hardware Drivers**, there are no drivers listed. Its only wants to list _proprietary_ drivers, but I'd have thought ATI is proprietary - so shouldn't it be listed..?

Any ideas on how I can check and perhaps reinstall the video driver?  Hoping that might reset things...

No answer since 9 hours? Wow, I was hoping somebody else with knowledge of proprietary drivers would have respond by now. I just came home from work and saw your latest post, but I can't help you with it. In my list I see my nVidia driver listed but this doesn't help you.
Please anyone, help this original New Zealand Kiwi.

---

### Post by mrtomservo on 2009-06-10
> **coolhandluke said:**
> So I'm wondering about my graphics driver...
Terminal command (~$ lspci -x | grep -i "vga\|display") shows:
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]

The driver was initially automatically recognised by Ubu. and has always worked fine. Like I said, the performance problems only started a few weeks ago and I've made NO changes to the driver settings. I've only turned off Compiz effects..

But, when I check **System ->Admin-> Hardware Drivers**, there are no drivers listed. Its only wants to list _proprietary_ drivers, but I'd have thought ATI is proprietary - so shouldn't it be listed..?

Any ideas on how I can check and perhaps reinstall the video driver?  Hoping that might reset things...

To check which video driver you are currently using, you can try:
```
glxinfo | grep render
```

It seems narrowed down to xorg, maybe you should post another thread specific to xorg to attract more xorg experts.

---

### Post by coolhandluke on 2009-06-10
Thanks again (esp lately DeMus:)

mrtom.. output was:
```
direct rendering: Yes
OpenGL renderer string: Mesa DRI Radeon 20061018 AGP 4x x86/MMX/SSE2 TCL
```

but I take your point - will leave this thread and try another with "Xorg" - see what happens.

Cheers

---

### Post by aliojjati on 2010-09-04
Actually, I have kind of similar problem. My problem is extremely slow write on hard disk and 100% cpu usage and it happens when I want to write something on the hard derive not any other external derive. 

Tried a fresh ubuntu install. No chance? I am not even sure if it is a software or hardware problem.

Can any body help?

Thanks

---

