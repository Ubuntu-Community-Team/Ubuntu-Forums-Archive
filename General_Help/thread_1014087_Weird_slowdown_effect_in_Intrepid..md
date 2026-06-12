---
title: "Weird slowdown effect in Intrepid."
date: 2008-12-17
forum: General Help
---

### Post by Midnightsun on 2008-12-17
Hi guys,

I recently installed Intrepid and am having a weird problem. It's pretty hard to describe so please bear with me.

Periodically the system starts experiencing a very odd slowdown.  I can't figure out what is triggering it but just using the computer normally for a while seems to lead to it happening.

The most noticeable thing that happens is the minimise "animation" becomes very slow and clunky.  I'm not using any desktop effects at all, so I'm just referring to the basic black window outline that gets progressively smaller after minimising.  

Also dragging icons or windows around the desktop becomes very difficult as the mouse click does not immediately register so when I click and move the mouse the target will not have been selected.  I have to click the icon, wait for it to highlight and then move it.  It's probably only a second but the effect is hugely noticeable.

I was using Hardy previously and never had this problem.  I was using the 2D SiS video driver for the Mirage 3 but the problem persisted even after reverting to vesa.  Restarting X has no effect and again the issue is very noticeable as after re-logging in the mouse icon stays in "thinking mode" for much longer and it takes longer for the internet icon to pop up and tell me I'm connected.

Rebooting DOES solve the problem but only temporarily.  After a random amount of time it will just start happening again.

In "System Monitor" there is no indication of anything happening.  My CPU usage is in low single digits and I'm using only 15% of 2 gig of ram.  

I realise that this is probably a very hard problem to diagnose given what little information I've provided but I would really appreciate it if anyone is able to help me!

---

### Post by Midnightsun on 2008-12-17
Also - I've just noticed that watching video becomes unbearable.  Video's played both locally and on the web get stuttering video and audio.

Really hope someone knows how to figure this out as I can't stand too much of this and don't really want to downgrade again to Hardy

---

### Post by hal8000 on 2008-12-17
I think system update is not real time and updates in 5 second intervals.
Its either some memory leak or perhaps you have too many visual effects enabled that your graphics card cany cope.

Not yet tried intrepid, so you need to try a few things first:
First disable compiz if youre using it and test your system for an hour or so.

You may also want to try a new monitor:-
apt-get install qps
is another utility similar to top

Hope that helps, youll possibly receive more detailed help but for now try and reduce visual effects systematically and see if you can find the cause of the problem

---

### Post by Midnightsun on 2008-12-17
Thanks for the reply Hal!

Unfortunately I'm not using compiz/visual effects at all, so that can't be it. The problem persists even using just the vesa driver.  I'll try out that system monitor you mentioned.  Is there some way to diagnose a memory leak to figure out what's causing the problem?

---

### Post by Midnightsun on 2008-12-17
Hi guys,

I've discovered a new and weird symptom of this problem.  It quite literally makes time slow down.

I noticed that my taskbar clock was showing the wrong time and then checked other places.  Typing "date" into the terminal returns the same, incorrect time.  I then went to the website onlineclock.net and the seconds there, though ticking by, are doing so at about 1/3 of the speed they should be.  According to my computer it's currently 2:23 when in fact it's 2:30.  

I have no idea about the inner workings of the system clock but this seems totally bizarre!!!

Hopefully this can in some way assist someone in diagnosing this extremely infuriating problem.

---

### Post by Snow986 on 2008-12-17
If you don't mind me asking, what are your system specs... 
Processor, ram etc.  I updated to intrepid without issue.  Did this start right after the update or like a few days.

---

### Post by Midnightsun on 2008-12-17
Thanks for the reply!

My specs are:

Intel Core 2 Duo 1.5ghz
2Gig of ram
120gig HDD
SiS Mirage 3 graphics. (currently using vesa driver)

It's an Advent 9315 laptop purchased about 12 months ago.

The problem started shortly after installing Intrepid.  I did a clean install on the HDD and the problem has persisted through one complete re-install of the OS.

---

### Post by Catalyst2Death on 2008-12-17
The funky system clock seems to point to a major memory leak, or hardware problems.  You mentioned that you never see more than 15% memory usage, but it sounds like your CPU is pegged at 100%.  Its a duel core so even this shouldn't be a problem unless something is killing both cores.  Could you do something like leave the system monitor open, go about your business on the computer, and then when it starts slowing down, take a picture of the graphs, preferably the Resource tab of the system monitor.  It should give some indication of exactly what goes on with the resources shortly before and after it starts freaking out. Also take try to include a picture of top running in a terminal. That way we can also try to pinpoint processes.

I'm sure there's a better way to give us more diagnostic data, but those are my ideas.

---

### Post by grdnwsl on 2008-12-17
It's possible that your problems might be two separate problems.  

I'll focus on the graphics choppiness first.  It's possible that there is a background task running and causing a lot of I/O while your computer is being slow.  Does the choppiness happen at any particular time?  You might want to check for any background tasks running by opening a terminal window when your computer is being slow and running 'top'.  It will show you a list of processes, sorted by CPU usage.  It might give you a clue as to what is causing the problem.  My guess is that it might possibly be 'updatedb' that is causing your choppy graphics issues.  It's a pretty I/O intensive program that runs on your computer once a day.

Your second problem, the "slow time", might be caused by a dying or dead CMOS battery on your computer.  How old is your hardware?  Do you have Ubuntu set-up to keep the computer clock up-to-date via a time server?  If not, I would definitely recommend it.  It will sync your computer's clock with an internet time server periodically to make sure it's on the correct time.

---

### Post by Snow986 on 2008-12-17
I agree it definitely sounds like a hardware problem.  Do you monitor system temps? If you do whats your typical.  Also I agree, could you look and see what processes are running and post it. Also is it a dual boot or pure linux?

---

### Post by Midnightsun on 2008-12-17
Thanks for the replies chaps.  I'm currently experiencing the slowdown (once it starts it doesn't stop until I reboot).  I will include below the screenshots of my system monitor and "top" running in terminal.  

I suspect that the time problem is not the cmos battery as the clock runs fine after a reboot.  It only begins acting up once the slowdown begins.  I'm certainly no expert on the issue though.

No particular action seems to kick off the slowdown - it began the last time while reading the forums at imdb.com and prior to that while watching a youtube clip.  

Thanks for the time in helping.  It's very much appreciated.

Edit:  I should also note that whilst it may very well be a hardware problem it began almost immediately after installing intrepid...so if it is hardware it's quite a coincidence.  I'm hoping to avoid reinstalling Hardy to test this theory however.

---

### Post by grdnwsl on 2008-12-17
I wound up finishing my post after you posted your system specs.  I agree with a couple of the others here, you might be experiencing a hardware issue.  Make sure you machine is adequately cooled.  You might want to open the case quick (assuming it's a desktop) and make sure the CPU cooler fan is working correctly.  Also, double-check that your power supply is set to the correct voltage.  I've had it happen before where it's been set to 220V (instead of 110) from the factory.  Sometimes the machine will work, but will not work correctly.

Just some suggestions to start narrowing down your list of possible causes.  Remember, the first rule of troubleshooting is test one thing at a time.

---

### Post by Midnightsun on 2008-12-17
> **grdnwsl said:**
> I wound up finishing my post after you posted your system specs.  I agree with a couple of the others here, you might be experiencing a hardware issue.  Make sure you machine is adequately cooled.  You might want to open the case quick (assuming it's a desktop) and make sure the CPU cooler fan is working correctly.  Also, double-check that your power supply is set to the correct voltage.  I've had it happen before where it's been set to 220V (instead of 110) from the factory.  Sometimes the machine will work, but will not work correctly.

Just some suggestions to start narrowing down your list of possible causes.  Remember, the first rule of troubleshooting is test one thing at a time.

Thanks for the reply!

It's a laptop, so there's no opening it up, but the fan is definitely working as I can hear it and feel the warm air being blown out of the vent.  I've got the computer on my lap and it doesn't feel any different from usual.  I think that means it wouldn't be the voltage either.

I've just rebooted and once again everything is running hunky dory - but I've no idea how long this will last before it begins again.

---

### Post by Snow986 on 2008-12-17
Whenever I hear of computers doing things related to slowing down or freezing or shutting down it is always possible it could be a problem with the processor overheating.  I am just wondering if somehow your install of intrepid made your fan stop working.  Stranger things have happened.  I would search and download a temperature monitor utility and see what your temps are.  Also make sure everything is up to date.  You could always try reinstalling 8.04 and then just upgrading to intrepid so that you use the Hardy install.  Just keep trying to rule things out.

---

### Post by Midnightsun on 2008-12-18
Thanks for the suggestions Snuxoll.

I'm fairly certain the system isn't overheating.  Like I said it is a laptop and the fan is definitely working.  Unfortunately temperature apps I've tried to install have not worked.  I don't know if this is because I have to boot the machine with the "noapic" and "acpi=off" flags for it to work.

The system has been on all day and I was using it for several hours this evening before the problem just kicked in again.  I was just chatting on irssi so I can't see how that would have triggered it.  The clock has also been spot on all day until the slowdown kicked in so I'm also fairly confident it's not the cmos battery.

I'm interested by the idea it is a memory leak.  Would that still be possible if the system monitor is reporting only small memory usage?  Could anyone suggest a way to diagnose such a problem?

Really desperate for some help here.  Downgrading to Hardy again is something I want to avoid if it is at all possible.

---

### Post by Midnightsun on 2008-12-18
Well I'm afraid I'm giving up and re-installing Hardy.  This problem is making using the computer pretty impossible.  

On the upside I will at least be able to confirm or refute my suspicion that this is software, not hardware related.  

I will post a follow up in a few days if the problem does not reoccur so as to confirm the existence of this bug for future people with this problem.  Hopefully someone else is able to get to the bottom of it if it happens to them and I'll be able to come back to Intrepid.  

Thanks to the people who attempted to help.

---

### Post by FrostBlue on 2008-12-20
I had similar problems on my Alienware laptop with Intrepid a while ago.Video and sound became suddenly jerky and Photoshop on wine would get really slow,couldn't draw a smooth line at all.Also, sound server would crash and I had to reboot to get it to work again.Also had some problems with network manager not being able to detect wireless networks and such.

I am not ranting here,I love Kubuntu,its just that I have been checking forums since I had these problems and people are still having such issues.
So for now I am sticking with Hardy,even though I cant really get KDE 4.2.

If this continues I might just wait for a solid Jaunty release.

---

### Post by Midnightsun on 2008-12-20
Well I'm now fairly certain I can confirm it was a software issue in Intrepid as opposed to a hardware one.

Since downgrading to hardy 2 days ago there has been no problem whatsoever.  Everything has worked exactly as before (i.e perfectly)

Wish I had some comprehension of what exactly the problem was and how to fix it, but I guess that will have to be someone elses problem now :)  Just hope it's not someone trying linux for the first time who decides to move back to Windows.

Thanks to those who tried to help.  Hopefully Jaunty will be a better experience.

---

### Post by mimimotor on 2008-12-21
Hi Folks, Thanks for this discussion, I have the same problem on my 

Intel Core 2 Duo 1.80 ghz
 1001,2 MiB of ram
 36,4 gig HDD.

I have installed Xubuntu intrepid yesterday from Xubuntu hardy. Hardy worked fine, intrepid is awfully slow. Nothing special is installed; only Firefox is running. I'm prety sure it's not hardware, everything works fine in XP. In xubutu has one CPU working at full capacity, the other at 20%.. They reverse roles occasionally.
 I have
Intel Core 2 Duo 1.80 ghz
 1001,2 MiB of ram
 36,4 gig HDD
I want to go back to hardy. Could somebody provide me with information on how to do that? 
Yours,
Johan

---

### Post by digger95 on 2008-12-21
Don't know if this is applicable to your machine(s) but the kernel that ships with Intrepid has some sort of acpi bug that prevents my cooling fans from operating properly, which causes my processor to overheat after a while.  This is especially true while watching flash video (youtube, etc) or using processor-intensive software.

Take a look at your boot messages and see if you have the issue:

```
dmesg | grep -i acpi
```

Many systems are dependent on acpi for fan control.

Dig

---

### Post by lobo-tuerto on 2009-01-10
I have had this very same problem since 8.04.

In 7.10 all worked alright, never had this problem. I have been thinking that it might be a driver issue, maybe something that went into the kernel. 

I had this idea because the energy management panel on 7.10 was more complete than the one that came with 8.04 (it was missing a few sliders to control the monitor brightness, well, not missing, but grayed out).

My computer is an HP dv9000 laptop. And it's being terrible to have this problem since 8.04... now must I endure it through 8.10 too? :(

Anyone with an idea or something?:confused:

---

