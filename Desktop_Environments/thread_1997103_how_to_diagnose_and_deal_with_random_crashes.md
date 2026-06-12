---
title: "how to diagnose and deal with random crashes?"
date: 2012-06-04
forum: Desktop Environments
---

### Post by idiotprogrammer on 2012-06-04
I have 12.04 and it works great. But I've noticed intermittent crashes that freeze the screen. They have been happening more frequently on this version of linux than any I have ever used. 

(I ran a memory test, without problem). 12.04 64 bit on a somewhat old amd system with Radeon HD 2600XT card. 

I have two issues: 

1)how do I escape when I see that the crash is occurring or will be about to occur? 

2)how do I gather clues for figuring out what is causing the problems?

Let me give some information about what I already know: 

[LIST]
[*]crashes when using Dropbox for the first time. (This is now fixed and no longer a problem). 

[*]crashed when loading music libraries in Amarok/RhythmBox for the first (and maybe the second time). 

[*]crashed multiple times (sometimes suddenly and unexpectedly) when using Firefox, often when it's using a lot of memory. (I have 4 gigs total, so sometimes the memory usage is very high). 

[*]crashed when loading video. (more than once)
[/LIST]
 

For the audio/video applications I was trying to access NTFS partitions which were unmounted by default. I suspect that the system freezing might be a result of trying to play files which are inaccessible because the partition was unmounted. However, I just set fstab so that this Windows drive will always mounted, so I should know if this has anything to do with it.  

Looking here, [https://wiki.ubuntu.com/X/FixingCrashes](https://wiki.ubuntu.com/X/FixingCrashes) I see two other potential issues: proprietary modules and overheating. I have loaded the fglrx proprietary drivers for Radeon, and honestly I don't remember if they were loaded until today. I guess I don't understand why a potential videocard problem could cause the whole keyboard to lock. Often I am unable to open System Monitor, and &#8216;Ctrl + Alt + Backspace&#8216; doesn't do anything in Ubuntu 12.04. If I do 'Alt + SysRq + K&#8217; it does something, but I'm not sure it's good. Instead, I see vertical red lines all over the screen and no apparent way to escape -- not even TTY. (Is this expected behavior?). 

I'd assume that I'd be able to drop to a console. Many times the system locks up before I had a chance, and besides I have two problems (dont' laugh!) 

1. Even if I were able to open up a console in a separate session, I'm not sure what application I'd want to kill. What is the name of the windows manager app  in Ubuntu 12.04 which I'd want to be killing or restarting  (I don't see gnome, dgm or kde; is it nautilus or unity (which one?)

2. During normal use, I can Ctl_Alt F1 to open TTY 1. My login can work here, and I see that if I create a dummy file, it is owned by root. But the command line shows a $, not a #, Why is that? 

Anyway, thanks for your help.

---

### Post by idiotprogrammer on 2012-06-06
Just to clarify: I'm not asking this forum for what the solution is. 

I'm just asking for how to collect crash data, how to recover from an X server crash. 

Sorry to be so trollish, but in my 15 years of running PC's, I have never seen so many  random crashes. Even Windows 98 and ME didn't crash this often. When I run Vista 64 with the same hardware, I never crash. **[SIZE="3"]Is Ubuntu 12.04 just not ready for prime time? [/SIZE]**

(The gui is great, and I prefer working in Ubuntu; I love everything else about it,  but I've lost several documents as a result of these crashes). 

It's possible that the video drivers are to blame, but my limited experience in the last two days suggests that it's the mplayer app, nautilus  and Firefox.  And Windows has almost never crashed because of a Firefox problem. 

These sound like application problems to me. But I thought the main appeal of linux was that it's rock solid reliable and impervious to app issues like this. 

What's happening?

Update: 
Ok, I can su to root via TTY in normal situations. But almost never when an crash is occurring. If I do 'Alt + SysRq + K&#8217;, I can cause the screen to turn completely red stripes. On one case when I did I was able to TTY, and then when I returned to this screen, the desktop returned to normal. But that is only one time.

---

### Post by 23senick on 2012-06-06
I get system crashes (some seem to have no effect) and freezes too. Xubuntu has the minor system crashes but no freezes, so is Unity to blame?  

I did find 11.10 did this at first and then improved...hope 12.04 goes same way!

---

### Post by arisp on 2012-06-07
I've got the exact same behavior as you. Random freezes, which when caught in time i can go to TTY1, logon, ran top, find nothing wrong, go back to X session to find it unfrozen and apport saying that some application crashed. If I too don't go fast enough to tty1 it freezes completely.
For the past week I switched from unity and compiz to gnome-shell and it stopped, so I'm inclined to say it's compiz that causes all that. Usually this happens when a compiz effect fires up, like when an application starts, or I hover over the launcher to switch to a task and mini-windows appear, but I can't derive anything from the logs. 
I'll try for a few days to disable some effects one by one to see if this disappears and report back.

Edit: Or it might just be Nvidia: [Ubuntu 12.04 and nVidia 295.40 driver warning](http://linuxforums.org.uk/index.php?topic=10109.0)

---

### Post by idiotprogrammer on 2012-06-08
Arisp, this is helpful information. I suspect that if it's Compiz, that will be fixed more quickly. 

I really don't know where to begin troubleshooting the fglrx proprietary drivers for Radeon. Or if the fglrx drivers will be updated. 

Just got another crash an hour ago doing something innocuous. As I said, I average one a day.

---

### Post by traditionalist on 2012-06-08
> **arisp said:**
> I've got the exact same behavior as you. Random freezes, which when caught in time i can go to TTY1, logon, ran top, find nothing wrong, go back to X session to find it unfrozen and apport saying that some application crashed. If I too don't go fast enough to tty1 it freezes completely.
For the past week I switched from unity and compiz to gnome-shell and it stopped, so I'm inclined to say it's compiz that causes all that. Usually this happens when a compiz effect fires up, like when an application starts, or I hover over the launcher to switch to a task and mini-windows appear, but I can't derive anything from the logs. 
I'll try for a few days to disable some effects one by one to see if this disappears and report back.

Edit: Or it might just be Nvidia: [Ubuntu 12.04 and nVidia 295.40 driver warning]("http://linuxforums.org.uk/index.php?topic=10109.0")

Same thing here, ( But with ATI Radeon cards) when i switched to GNOME Classic it stopped. I prefer the classic interface anyway. The generic drivers work for me. The proprietary drivers don't. I gave up trying to troubleshoot the ATI stuff, just use the generic drivers now.  No problems and the system is stable. No crashes, no warnings etc etc.

There is not much you can do about apparently completely random crashes as it is well nigh impossible to find out exactly what is causing them. But Unity and the graphics drivers are prime suspects. Compiz works fine for me in GNOME Classic. But it just kept crashing in Unity.

---

### Post by idiotprogrammer on 2012-06-08
Traditionalist, thanks for your reply, and purely by coincidence I stumbled upon your thread about ati drivers. 

[http://ubuntuforums.org/showthread.php?p=12010970#post12010970](http://ubuntuforums.org/showthread.php?p=12010970#post12010970)

Just one question: do you think the generic drivers will be more stable in Unity/Compiz as well? I quite like unity, and I'd like to keep that. 

For the record, System Settings --> Proprietary Drivers does not install the post-release drivers because the log says it cannot find them.

As ubuntu gets updated, do you think that this stability problem will improve? For both the free driver and the propreitary driver or only one of them?

---

### Post by idiotprogrammer on 2012-06-08
I should emphasize that my system crashes don't occur always as a result of video/Unity problems. 

For example, I just tried making updates to Eclipse editor and everything froze and crashed. I guess I can't blame ATI for that one....

---

### Post by traditionalist on 2012-06-08
> **idiotprogrammer said:**
> Traditionalist, thanks for your reply, and purely by coincidence I stumbled upon your thread about ati drivers. 

[http://ubuntuforums.org/showthread.php?p=12010970#post12010970](http://ubuntuforums.org/showthread.php?p=12010970#post12010970)

Just one question: do you think the generic drivers will be more stable in Unity/Compiz as well? I quite like unity, and I'd like to keep that. 

For the record, System Settings --> Proprietary Drivers does not install the post-release drivers because the log says it cannot find them.

As ubuntu gets updated, do you think that this stability problem will improve? For both the free driver and the propreitary driver or only one of them?

Sorry, I don't know. If you can get them to work with Unity they might be more stable, but the only way I could get my setup to run reasonably at all was to remove Unity. It just crashed all the time, often so badly that I was unable to recover the system and had to reinstall. I got sick of that pretty quickly.  GNOME shell worked alright, (although with very high CPU usage), but I didn't like it much, I don't want menus and stuff spread all over the desktop!  I am now using GNOME Classic and it works great. No problems at all.  Also easily customisable to a high degree.

I prefer my screens blank when I am not actually working, and preferably with a single menu/setup location. I don't want stuff in different positions. Doubtless one could get used to that, but I don't want to. For me, Unity is basically unusable for those two reasons. I couldn't get it to work properly, and I didn't like it even when it did work for short periods.

In the final analysis, if I had not got this system to work properly with GNOME Classic, as stated, then I would have looked for another graphics card.    The reason I have this one in my personal machine is that up to five weeks ago I was running Windows 7 on it as a dual monitor setup and the card worked really well for that, never had a crash.

I switched to Ubuntu mainly because of other recent problems with Windows 7, but I still run 7 in a VM on this machine. I only need it for my on-line banking.  If I had been setting up an Ubuntu machine to begin with I would have done some  research on suitable cards beforehand and most likely avoided ATI altogether. As it is now it works fine and is stable.  No crashes at all since I installed GNOME Classic.  Also in a dual monitor setup.

Trying to find out what exactly was causing the crashes was unsuccessful, and I really only tried these other things in desperation! :)  Otherwise I might well have persevered with Unity. I am pleased that GNOME Classic works so well and suits me though, so I don't consider it a loss.

There comes a point with all these things when you have to decide whether to cut your losses and go for something else.  My tolerance for such is very high, I was the chief of engineering and the top computer and electronics troubleshooter for a major international corporation, also responsible for a global area net, and there has rarely been anything I could not get to work which was workable at all. Even when many others failed. I also got the worst problems that nobody else had been able to solve of course! I am retired now and I have plenty of time to try things, which is just about all I do now, but the mess on with Unity and the graphics drivers exceeded even my tolerance for such things, more so here, as even when correctly installed the drivers do not work. It is completely pointless wasting time on things that obviously do not work even when set up correctly.

Had I been doing this on behalf of my previous employer, or a customer, I would have packed it in after an hour at most as the cost of my time would have far exceeded the cost of new or different hardware which would then have worked. As it is I spent a couple of weeks on it.  Unthinkable really.

---

### Post by traditionalist on 2012-06-09
Just by the way, what annoyed me most about the whole business is not that it didn't work, that can happen with all sorts of things, just how it is, but the fact that loads of people keep telling you "it will work if you do this.........."and similar. This causes one to waste a great deal of time and effort. With some things it is better to simply ignore what others say and rely on your own experience and instincts.

---

### Post by arisp on 2012-06-11
In my case the culprit proved to be compiz after all. After my previous message I went back to unity, disabled windows previews and animations and updated my nvidia drivers. 
After a few days without incident, I re-enabled animations and 10 minutes ago, windows previews. 
Sure enough a few seconds later, after playing around with firing up applications and hovering over their launcher icons my system froze completely, so in my case it was this one compiz plugin.

---

### Post by VanillaMozilla on 2012-06-21
With all those programs crashing, if you can't get a crash report, I would look for something in common.  First, I suggest that you do a memory test.  There's a test on the installation CD.  Second, I would uninstall any proprietary drivers.

---

