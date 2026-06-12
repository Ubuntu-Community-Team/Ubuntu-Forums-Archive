---
title: "Laptop Power consumption: KDE vs Gnome"
date: 2012-02-25
forum: Desktop Environments
---

### Post by nihonbun on 2012-02-25
A journey on my trail of OS's and desktop environments:

SKIP purple text to get to my point.
Note: if I don't say Gnome Shell, any reference to Gnome is a reference to any Gnome child, Gnome Shell included.

[COLOR="DarkSlateBlue"]I don't want to start a debate, by any means.  I simply want to share my two cents and receive some feedback from the community.):P

I have been in an operating system struggle for years now.  I got Windows 7 soon after I bought my Dell Inspiron 1545 (AMD), and of course, the first thing I did out of the box was to install Ubuntu alongside it (partitioned, not wubi).  Ubuntu is such a rich operating system, and I have loved to watch it evolve from synaptic to creating a very full, beautiful software center.

I used windows at college a lot, but over the last 2 & 1/2 years, i have had to reinstall windows about 5 times, including having to replace my hard drive tree times!  It's a broken wheel...

However, I have had issues with Ubuntu as well, which has driven me back and forth, Winders to Linux, and vice versa.  I noticed _**significantly**_ better power management in windows when compared to ubuntu on my computer, from version 8.04 all the way up to 11.10. Known issues? FGLRX (video card), cpu frequency scaling, and so on and so forth. It has also been a struggle to get my alps touchpad to be fully functional (middle click and side swipe scroll) each upgrade.

On the issue of power, the heat sink on my laptop runs right under my touchpad, and when it's really cranking out heat (I suppose this means the cpu is working hard {even when I scale it down with cpufreq applet}), the touchpad becomes quite hot to the touch.  windows 7 didn't have as much of an issue with this with all of the correct drivers installed.  however, even windows became sluggish and power hogging after a while.

I promise, I'm getting to my point. :roll:

So, after going to Linux Mint for a while (still on my other partition, now free of MS Windows all together), I enjoyed their implementation of the Gnome Shell a bit, and re-installed ubuntu 11.10 (yet again).  I put on gnome shell, and despite everyone else's complaints (including my father and his co-workers, an old time linux user, and the reason I use it today), I love it.  The way you can go to the top left corner and go through desktops, open windows, applications, and so much more, I LOVE it!  Gnome 3 is awesome!  so pretty! I've also tried other gnome 3 children, like cinnamon, etc.  What they built at gnome is really cool, really.  Unity has always been a bit of a bugger for me, so I don't want to mention it right now; suffice it to say, it's pretty, and I look forward to future development of it.[/COLOR]

Now here comes the kicker for me.  After installing fglrx, getting annoyed with it not letting me suspend and then removing it, and doing any iteration of putting and taking down the AMD/ATI graphics driver I could find, I heard that KDE doesn't have so much of an issue with fglrx.  So, I installed kubuntu-desktop on my Ubuntu system.

Yeah, plasma desktop is a bit ugly at first when compared to gnome shell's simplistic layout, but after putting my desktops up how I like them, setting keyboard shortcuts, and making it set my middle button emulation to true when I log in (tiny startup script), I like it okay.  I prefer nautilus to dolphin (with the exception of dophin's network ssh connector, that is nice).  I can complain, however, of the load time for KDE.  Gnome is usually faster for me.

Most importantly, my power consumption is WAY down in comparison to my gnome desktops.   
In terms of battery life: my battery is at 45% (broken, old), and under GNOME or its children, I get a battery life in the ballpark of 1 hour.   That's with everything turned down: cpu, screen, etc.
KDE: 2.5 hr average, sometimes when I am not fully charged to current capacity.

In terms of heat-
Gnome: plugged in or on battery, I use it for an hour, it's HOT (read: HOT!!!)
KDE: It's been hot once, I think.  I turned my cpu up to performance, and it heated up.  Normally, however, it's mildly warm (slightly warmer than my hands), and the fan rarely runs to the point where I noticeably hear it.

My conclusion: KDE is better at managing my computer's power than Gnome.
My dilemma: if I search for people who have found the same success as me, I find the opposite.  Everyone else is finding that gnome is giving them better power than KDE.

My question to everyone:  If I, a moderate novice user (everything I do in the terminal, my dad told me to type or I found via google) can make kde run more efficiently than gnome, what are more advanced users doing to make their gnome systems run more efficiently?  I really would love to run Gnome, but when I run a laptop, I expect to be able to unplug for a while.

If you want to know/gnow):P any statistics for my setup, you will have to provide the commands so that I know how to give it to you.

Long live freedom!

---

### Post by 23dornot23d on 2012-02-25
If you like both KDE and Gnome Shell ..... then what I do is this .....


Start up in KDE as normal ..... then once in Alt+F2 and run .....


gnome-shell --replace


If similar to my setup ..... then what happens is KDE remains as the front screen and when you go to the top left ..... you get the full functionality of gnome-shell


If you try it out let me know how it goes ......

As I run Nvidia Graphics 9300 gs m

You running ATI may - you may still run into problems ..... but it will be interesting to find out if it works ok .. see if the heat problem still arises .... and check the system
monitor so you know what is happening .... when you run it ..... ;)

It works very well for me ...... 

( but I only use it when I need it - as most of the time KDE is fine as it is )

running multiple apps for me I do like gnome-shell better than KDE for going to the top left - even though Kde has now built in something very similar to it.

[_**VIDEO of it running on mine**_]("http://www.youtube.com/watch?v=E0C64_Nak9Y&feature=youtu.be") .....

---

### Post by nihonbun on 2012-02-25
Note: I still do quite like my kde setup, but I want to try that.  But before I do, how will I return to my kde desktop if I so desire?
could I say something like this? 
  kubuntu-desktop --replace
Or what?  
Else will it go back to kde when I restart my computer?
I want to know the back door if I need one.

---

### Post by 23dornot23d on 2012-02-25
It will return back to normal after logging out ......

This is just a temporary thing that I do ....... as I like gnome-shell .......

Alt + PRt scrn + K

Will kill the X window if anything odd should happen ...... as I say I do not use ATI
the results may be different on that

---

### Post by nihonbun on 2012-02-25
I do like that idea, actually.  It sort of combines both desktops.  
I also like that you are well equipped with blender :)

Correct, however, on the assumption that I would have problems with my video card driver. On the gnome part, the text is jarmbled and the black toolbar is multicolored.  I tried to take a screenshot, but that just turned out black, so no help there.

Also, How did you get yours to autohide like that?

---

### Post by 23dornot23d on 2012-02-25
> 
I do like that idea, actually.  It sort of combines both desktops.  
I also like that you are well equipped with blender :smile:


Love it and could not be without Blender ..... but would love to be able to have both the old
version and the new one running together ..... ( it sort of works downloading one from blender - but does not integrate as well as being installed )


> 
Correct, however, on the assumption that I would have problems with my  video card driver. On the gnome part, the text is jarmbled and the black  toolbar is multicolored.  I tried to take a screenshot, but that just  turned out black, so no help there.


I have seen the problem with ATI pop up far too many times .... and some solve it with new drivers .... thing is I have not seen one proper answer that suits all yet - it can be done by swapping and changing video drivers ..... 

but google search for your ATI card and solved ( against Gnome Shell ) as it crops up
their more often.

> 
Also, How did you get yours to autohide like that? 	  	


The way this works just happened as I set it up and I like it ..... the version I am using though is the 12.04 test version ..... so it may be slightly different on the 11.10 version

Well sorry it did not work fully - maybe the next version and the graphics driver for the
ATI card may work better ...... in a terminal type

**lspci**
 
To see what you have .... we may be able to find a better graphics driver ..... or a solution to the odd colors in gnome-shell appearing.

---

### Post by nihonbun on 2012-02-27
01:00.0 VGA compatible controller: ATI Technologies Inc M92 LP [Mobility Radeon HD 4300 Series]

That is what i found.

Note:  it works in kde....

Is there any way that I can find what things in gnome are taking so much power and what in kde is acting more efficiently?

---

### Post by hildenbrandsteven on 2012-02-27
I'm running 12.04 Alpha 2 on an Acer Aspire and I see better battery life (I'd say roughly +30-40mins) while using Gnome w/ Unity.

---

### Post by JC Cheloven on 2012-02-27
> **nihonbun said:**
> 
Is there any way that I can find what things in gnome are taking so much power and what in kde is acting more efficiently?

Yes, powertop is meant for that. It's in the repos, so to install it ```
sudo apt-get install powertop
```

It must be run with root privileges: ```
sudo powertop
```

FYI: the linux kernel has had an issue with power consumption for almost all 2011 versions (that is, natty and oeniric in the ubuntu world). Now it is fixed in the 3.x versions of the kernel. So please check what kernel are you using, and eventually update it.

As to the rest, powertop will give you relevant info about the CPU wakeups/second, processes consuming more power, etc

Hope it helps
JC

---

