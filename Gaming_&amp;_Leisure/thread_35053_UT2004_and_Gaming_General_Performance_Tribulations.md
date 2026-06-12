---
title: "UT2004 and Gaming General Performance: Tribulations"
date: 2005-05-17
forum: Gaming &amp; Leisure
---

### Post by Cmdr_K00n on 2005-05-17
Hey there, I just overcame a big problem that was turning me off Ubuntu quite a bit.
Slack Gaming Performance. Hopefully people who are having these problems may learn something

My rig is as follows:
AMD64 3000+ 939 Pin @ stock
1.5GB Dual Channel DDR400
200GB WD SATA Drive
Leadtek 6600GTTDH 128MB VIdeo

I am running the x86 version of ubuntu for the ease of use with web plugins and the like. I ran the 64 bit one for a bit, and i really cannot tell the diff.

In any case i was getting around about 3000 fps in glxgears.
UT2004 was acting rather strange by running reasonably ok when i was looking at a blank wall, but when i started moving round it was running at around 20fps on 1024x768 with normal settings.

After some searching around I came across a tip to use the nvagp driver instead of agpgart. I tried this by setting the appropriate options in xorg.conf, but could not get it working as it always reverted to agpgart. I then learned of blacklisting modules, so i blacklisted agpgart and a STRANGE module I saw called amd64_agp. 

When I rebooted my system, the modules nvidia and agpgar were loaded, but not amd64_agp.

I ran glxgears and got around 6480 fps!
Ran UT2004 and whola! 1280x1024, EVERYTHING set to the highest levels  and my average frame rate was around 50FPS on inferno invasion.

So if your having problems:


1:) if glxgears.output 
        < 1000 :: OpenGL problems
        About 3000 :: AGP module problems
       >5000 :: No Problems

2:) Apparently the latest nvidia driver which is synaptic has some major agpgart     improvements ver 7174 i think

3:) The latest ut2004 patch 3355 also has some graphic improvements as well.

In the end though I would like to hear from anyone that has got nvagp working.
Also, what sort of scores are people getting with my sort of configuration?


I tried manually from console ( ctrl+alt+F1)

sudo /etc/init.d/gdm stop
sudo rmmod nvidia
sudo rmmod agpgart
sudo modprobe nvagp

At this point I am told that this module does not exist!
I am guessing that it is not compiled in somewhere, but where? Ive had a look at the kernel source but could not see it, and i don't think it is in the nvidia driver package?

---

