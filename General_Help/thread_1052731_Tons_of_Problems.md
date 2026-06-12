---
title: "Tons of Problems"
date: 2009-01-28
forum: General Help
---

### Post by AG28 on 2009-01-28
I have been a user of Debian for my home server for years.  I started using Ubuntu at version 6.10.  It worked perfectly through every upgrade until now.  I'm running 8.10 and it is operating horribly.  My login window often tells me the application has failed, firefox crashes every time I use it (actually it freezes), the system will spontaneously crash and go back to the login page and applications close on their own.  It really is to the point that the system is mostly unusable.  I have looked through the logs in /var but nothing jumps out.  (I would probably be considered an advanced beginner in terms of ability).  Is there any troubleshooting tips that anyone could recommend?  (In general, as I would like to learn along the way).  I have never had problems with Ubuntu until now which is why my troubleshooting skill are, well, minimal.

Thanks for any help/points.  :)

---

### Post by Peter09 on 2009-01-28
It could be your graphics drivers.

Post the output of

```
lshw -C display
```

so that we can see what set up you have there.

---

### Post by AG28 on 2009-01-28
Certainly, here is the output:

 sudo lshw -C display
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: CyberBlade/i1
       vendor: Trident Microsystems
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: agp agp-1.0 pm bus_master cap_list
       configuration: latency=32

I think it's a default SIS onboard/shared video.

---

### Post by Peter09 on 2009-01-29
Hi,
perhaps the discussion here will help

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-trident/+bug/223774](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-trident/+bug/223774)

---

### Post by jcroblesemanuelli on 2009-01-29
> **AG28 said:**
> I have been a user of Debian for my home server for years.  I started using Ubuntu at version 6.10.  It worked perfectly through every upgrade until now.  I'm running 8.10 and it is operating horribly.  My login window often tells me the application has failed, firefox crashes every time I use it (actually it freezes), the system will spontaneously crash and go back to the login page and applications close on their own.  It really is to the point that the system is mostly unusable.  I have looked through the logs in /var but nothing jumps out.  (I would probably be considered an advanced beginner in terms of ability).  Is there any troubleshooting tips that anyone could recommend?  (In general, as I would like to learn along the way).  I have never had problems with Ubuntu until now which is why my troubleshooting skill are, well, minimal.

Thanks for any help/points.  :)

I am having the same issues as you are.  I was very happy with my ubuntu machine but all of a sudden it is exhibiting similar behaviors. Ubuntu is so customizable and relatively foreign to me that I don't know how to trouble shoot my machine.  

> Hi,
perhaps the discussion here will help

[https://bugs.launchpad.net/ubuntu/+s...nt/+bug/223774](https://bugs.launchpad.net/ubuntu/+s...nt/+bug/223774)

Peter I hit the link you recommended and appreciate your help, however is there a way to stepwise trouble shoot any machine?

---

### Post by Peter09 on 2009-01-30
First 
Check if you have a driver waiting to be enabled in:

System->Administration->Hardware Drivers

If not then try rebooting in safe mode and selecting the fix X option - cannot remeber what its called offhand.

---

### Post by hyper_ch on 2009-01-30
It is advised to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

See the forums policy, especially section II.2: [http://ubuntuforums.org/index.php?page=policy](http://ubuntuforums.org/index.php?page=policy)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---

### Post by jcroblesemanuelli on 2009-01-30
Hyper,

Thanks for your comments and guidance.  I guess my problem is that I don't know where to start trouble shooting.  I don't know which 'specific thread' is the appropriate to start.  I guess I was hoping someone of vast knowledge could lead me in the right direction like:

"The first thing you need to do to troubleshoot you're crashing ubuntu machine is to..."

I have looked through specific problems people have through out the forums and it seems that there are many different ways to troubleshoot a specific problem when you know what that problem is.  My problem is that I don't know what that problem is so I can't say that my machine crashes because it has problems with: the kernel, hardware, a specific application, etc.  

I will appreciate any help and I apologize for my noviceness; however every journey has the first couple of steps.

---

### Post by AG28 on 2009-01-30
Peter09 - Thanks for the input.  I'll check the link out.  I love the challenge but this one kind of took me by surprise.  Hopefully I'll learn a little something on the way.  :)

hyper_ch - I'll try and remember to post a 100 line header the next time.  You see, if EVERYTHING is crashing and messing up, exactly how descriptive are you going to be?  But you do have my sincere apologies on the code /code thing.  I'll also look up and make sure my tabs on paragraphs are correct as well.  :roll:

---

