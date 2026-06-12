---
title: "Ubuntu (Jaunty) generally lagging"
date: 2009-05-11
forum: General Help
---

### Post by Kiliankoe on 2009-05-11
Hi there,

I just installed Jaunty on my PC with the help of Wubi (a wonderful idea by the way). Because of my internet connection failing when Wubi downloaded Ubuntu I did a manual download and installed it with the ISO that I got. I don't believe that could be a cause for my problem though.

As I started Ubuntu I experienced some lag. I tested it with music and video playback, which both jump a little and are therefore not enjoyable. Also the mouse lags, which is probably the biggest problem.

Now I installed the newest available drivers for my Graphics Card (Nvidia Gefore 7600 GT), but that didn't help.

Now I don't know what else to do.

Does anybody have any ideas?

Thanks a lot in advance,
Kilian Koeltzsch

---

### Post by danwood76 on 2009-05-11
Did you install the hardware drivers through the hardware drivers manager?

Also what are the specs of your system? (CPU RAM etc)

If you open up the system monitor (System -> Administration -> System Monitor) and click on resources is the CPU usage high?

---

### Post by Yvan300 on 2009-05-11
The Wubi installer project maybe a breakthrough in ease of operation but it still has some bugs that need to be ironed out. Most likely the root of your problem may be from installing ubuntu through wubi. So i suggest you install the full ubuntu through the live cd. I would say it is as easy as making a sandwich. If you neeed any additional help please ask.

---

### Post by vgrisham on 2009-05-11
WUBI is really convenient, but in my experience, it is significantly slower than a grub-based dual boot environment. Some of Jaunty's gain in speed comes from the EXT4 file system; you're missing that jump in speed with WUBI. I used WUBI for about a week before reinstalling on a separate partition.

---

### Post by Kiliankoe on 2009-05-11
Oh, I seem to have mistakenly thought that Wubi was able to give me a fullspeed OS. 

I will try to install Ubuntu on a second partition with my LiveCD. How does the booting work though? How do I choose if I want Windows XP or Ubuntu?
Although I have had a few problems with installing a second OS on a second partition before resulting in me deleting my entire harddrive content. Now I do have an external HDD on which I am capable of saving my most important files, but I'd rather not have to reinstall Windows... again.

Thanks for the tips though!

---

### Post by danwood76 on 2009-05-11
Wubi gives you a full speed OS.
The only difference is disk speed which wouldnt affect overall speed like, laggy mouse etc.
Reinstalling will probably lead to the same issue so you will be back here!

---

### Post by briansrapier on 2009-05-11
Try disabling IPV6. This seems to be the culprit in many of the performance issues. It's built into the kernel instead of being a module in previous versions. Trying to disable it using sysctl.conf following the Ubuntu wiki won't work as the location of disable_ipv6 has moved.

Here is what I did:

Temp fix:
echo 1 > /proc/sys/net/ipv6/conf/all/disable_ipv6

More permanent workaround:
# vi /etc/sysctl.conf

add:

net.ipv6.conf.all.disable_ipv6 = 1

---

### Post by Yvan300 on 2009-05-11
Their are two ways you can dual boot with xp. First you can use ubuntu's bootlaoder called grub or windows xp's called 'I can't remember' :) Their is a program called easy bcd which makes it very easy to add linux to a windows [COLOR="black"]vista[/COLOR] bootloader but i'm not sure about xp. Check that out.

---

### Post by vgrisham on 2009-05-11
> **Kiliankoe said:**
> Oh, I seem to have mistakenly thought that Wubi was able to give me a fullspeed OS. 

I will try to install Ubuntu on a second partition with my LiveCD. How does the booting work though? How do I choose if I want Windows XP or Ubuntu?
Although I have had a few problems with installing a second OS on a second partition before resulting in me deleting my entire harddrive content. Now I do have an external HDD on which I am capable of saving my most important files, but I'd rather not have to reinstall Windows... again.

Thanks for the tips though!

It's really easy to setup a straightforward dual boot. Just boot to the Live CD, and choose the install icon on your desktop. Follow the prompts and accept the defaults. It should detect your XP partition and offer to import stuff from your My Documents folder. Decide how much disk you want each partition to own and make that change if needed. The installer will then resize the partitions and setup your boot menu. When you reboot, you'll see the grub menu. You can edit this menu later to make one OS or the other the default at boot. Let me know if you want help with that.

---

### Post by Kiliankoe on 2009-05-12
I'll just go ahead and deinstall Wubi and burn my LiveCD then. 

I've just had it before that the installation of Ubuntu was able to overwrite my Windows partition and left me sitting there like "What? That wasn't s'pposed to happen, right?" Unfortunately I depend on Windows and I need it (god this sounds awkward.. I was actually hoping never having to say that). It might have been my fault though, I wasn't very comfortable with installing an Operating System at that point.

In case I need help I'm definitely coming back to that offer, thanks!

---

### Post by vgrisham on 2009-05-12
[Here's]("https://help.ubuntu.com/community/WindowsDualBoot") a really straightforward guide to setting up a dual boot environment. Good luck.

---

### Post by Kiliankoe on 2009-05-12
Thanks for the link, it deifnitely is helpful!

I just have one questions regarding it. It's not clear enough if I have to create a second partition before booting Ubuntu from the LiveCD or if that's done during the Resizing Partitions Step.

---

### Post by vgrisham on 2009-05-12
It's part of the partitioning process on via the live cd. The only time you'd want to resize in advance would be with Vista (it has it's own resizing process). If you're using XP, Ubuntu will resize it for you (you'll have to choose how far to shrink it down and how big you want Ubuntu's partition to be).

---

### Post by Kiliankoe on 2009-05-12
So let's say my internal HDD is 111GB according to Windows. I've got about 46GB free. I was planning on using 30GB for Ubuntu.

I shouldn't lose any Windows files...


I understand that this sounds a lot like a complete beginner, but I just got over-sensitive due to the enormous amount of work I had to go through (two weeks of fun looking at Windows failing over and over again) installing Windows the last time. I don't want to mess this up again ;)

---

### Post by vgrisham on 2009-05-12
[Here's]("http://mywebsite.bigpond.net.au/dfelderh/p23.html") a more graphical how-to site. This really demonstrates what needs to happen and it is very thorough (and as I don't have a live CD with me, it's probably more accurate). 30 gb is fine. Be sure and back up your important files first.

---

### Post by Kiliankoe on 2009-05-13
Thanks for that link as well! I've got three more questions now though :D

1. I uninstalled Wubi, but the boot selection menu is still there. Would this make any differences and if so, how do I get rid of it?

2. I quickly booted Ubuntu from the LiveCD to access the Partition Editor (out of pure curiosity), but it was lagging just the same. Do I even have hope of fixing this with a full installation?

3. At step 36 in the graphical instructions, do I really need to make a swap area? I see the point, but I've got 4GBs of RAM in my PC and never thought about hibernating. I'm just wondering if I have to go through that extra step to make two new partitions from that space.

I guess that sums it up for now :D

Thanks for the great help already!

---

### Post by vgrisham on 2009-05-13
> **Kiliankoe said:**
> Thanks for that link as well! I've got three more questions now though :D

1. I uninstalled Wubi, but the boot selection menu is still there. Would this make any differences and if so, how do I get rid of it?

**I think Grub will overwrite the other bootloader when you install.**

2. I quickly booted Ubuntu from the LiveCD to access the Partition Editor (out of pure curiosity), but it was lagging just the same. Do I even have hope of fixing this with a full installation?

**The LiveCD runs from memory only, so it's not going to be very zippy.**

3. At step 36 in the graphical instructions, do I really need to make a swap area? I see the point, but I've got 4GBs of RAM in my PC and never thought about hibernating. I'm just wondering if I have to go through that extra step to make two new partitions from that space.

**You're going to want at least a 1GB swap; my swap is 4GB and I know it is overkill. You might also consider separate home and root partitions. This is handy for installing new releases. My system has a 4GB swap, a 14 gb root and a 280gb home partition.**

I guess that sums it up for now :D

Thanks for the great help already! **You're welcome. Good luck. **

---

### Post by Kiliankoe on 2009-05-13
Thanks for the quick answers! How can you possibly be able to answer this fast when living in Texas ;) Isn't it like 8 or 7 am for you guys right now?

I'm not going to install new releases in separate partitions. I either take a virtual PC for the quick tryout or use a throw-away laptop here :D
Ubuntu is just my big favorite so far, so I thought it would be time to install it on my main PC as well.

---

### Post by Kiliankoe on 2009-05-13
Okay, I finished installing Ubuntu and it all worked out. No problems during the installation process itself.

But now I have to problems:

1. The boot selection menu did not get replaced or disappear ;) After I select Windows in Grub it still shows up and asks me if I want to boot a non-existent Ubuntu or Windows XP... I uninstalled Wubi two days ago though. I thought that menu would disappear together with Wubi...

and 2. The original problem has not yet vanished either. Everything is still very laggy and just not fun to use.

What about that solution briansrapier posted earlier. I've never really done a lot of stuff with the console in Linux, how would I accomplish that?

---

### Post by vgrisham on 2009-05-13
> **Kiliankoe said:**
> Okay, I finished installing Ubuntu and it all worked out. No problems during the installation process itself.

But now I have to problems:

1. The boot selection menu did not get replaced or disappear ;) After I select Windows in Grub it still shows up and asks me if I want to boot a non-existent Ubuntu or Windows XP... I uninstalled Wubi two days ago though. I thought that menu would disappear together with Wubi...

and 2. The original problem has not yet vanished either. Everything is still very laggy and just not fun to use.

What about that solution briansrapier posted earlier. I've never really done a lot of stuff with the console in Linux, how would I accomplish that?

To get rid of the wubi boot manager, go to [this site]("http://www.psychocats.net/ubuntu/wubi"). Scroll about halfway down and you'll see an entry titled, "Double-click **System** and select **Advanced** and then **Settings** under *Startup and Recovery*. " In XP, change the entry on that menu to use the Windows boot manager again.

As far as the speed issues go, dang. I really thought that would have fixed it and that you would have seen an improvement. One question: what video card do you have?

---

### Post by Kiliankoe on 2009-05-13
I'll check out that site tomorrow, thanks.

I have a Nvidia Geforce 7600 GT. Ubuntu is using the newest possible, recommended drivers.

---

### Post by vgrisham on 2009-05-13
> **Kiliankoe said:**
> I'll check out that site tomorrow, thanks.

I have a Nvidia Geforce 7600 GT. Ubuntu is using the newest possible, recommended drivers.

I'd check this next...

Go to the System menu and choose System Monitor. Go to the Resources tab and report back what you see there. Then, go to the Processes tab and sort the list by the Memory column (two clicks).

---

### Post by danwood76 on 2009-05-14
Could you answer the question I asked earlier?
What are your system specs?

Also I said Wubi was full speed and this was caused by something else :)

---

### Post by Kiliankoe on 2009-05-14
I attached two screenshots showing the System Monitor. The three higher parts in the CPU History were caused by rapid mouse movement...

@danwood76:
Sorry, forgot that :D My system specs: 3GHz, 4GB Ram, my 25GB Ubuntu partition and my 256MB Graphics Card.
Is there something else you would like to know?

I prefer Ubuntu on it's own partition nevertheless :D Now it definitely is a solid part of my system.

---

### Post by danwood76 on 2009-05-14
Well your system is more than capable of running ubuntu! ;)
Sorry if I sounded a little short, its exam week at my uni, but now I'm finished :)

It seems that the slowness is probably graphics related, the other option is corrupt RAM but this is normally an extreme case (Linux is more sensitive to dead RAM as it actually uses the RAM it consumes).

The 7600 should be fine to run Ubuntu, with lots of silly effects also!
Have you installed graphics drivers on the new system (OS install)?
If so how did you do it?
The hardware drivers manager is the best way. (should give you the most compatible drivers)

---

### Post by Kiliankoe on 2009-05-14
Yes, I did install the newest graphics drivers on Ubuntu. I did so through the Hardware Drivers Manager and just downloaded/activated the recommended one, it was also the newest.

I really hope I'm not experiencing anything about corrupt RAM here. I just bought the 4 gigs a few weeks ago (upgrade from 2).

You didn't sound short in any way, hopefully you were successful with your exams :D

---

### Post by danwood76 on 2009-05-14
Exams were good thanks!
Curerntly relaxing with a celebratory beer ;)

Very strange then.
First thing is to disable all apperance effects to see if it gets better.
Go System -> Preferences -> Apperance

On the last tab (visual effects) select none and click OK. The screen might flicker but just click ok and see if its better.
If not then something odd is going on, what keyboard/mouse do you have?

---

### Post by Kiliankoe on 2009-05-14
I didn't even activate the extra effects (yet, not sure if I will)

Hmm... How do I find out detailed information about keyboard and mouse? I know both of them have worked fine with Ubuntu before (8.10) and are working fine with Windows.

Also it's not just the mouse that lags in Ubuntu, it's the general appearance, music and video. If you want, I can demonstrate it with a quick sound recording.

---

### Post by danwood76 on 2009-05-14
Compiz is enabled by default if your card can support it (which it should), so its worth checking and turning off.
General slowness should be caused by something, video drivers could be one thing. (and most probable)

If it was fine in 8.10 it _should_ be fine now really. Jaunty is quicker and should be lighter in general.
Keyboard and mouse should be fine if theyve working in linux before.

It is possible of course that the portion that the ubuntu devs disabled in X could be cause for your Issues (even I though I _may_ have told you it was unrelated in that other thread). [http://ubuntuforums.org/showpost.php?p=7261916&postcount=13](http://ubuntuforums.org/showpost.php?p=7261916&postcount=13)
Personally I dont know what it was they disabled (something to do with backfilling) or wether it will help but its worth a go considering the straws we are clutching at ;)

---

### Post by Kiliankoe on 2009-05-14
What do you mean with compiz? And where can I find an option for that?

I just followed the instructions in that link, they didn't help. It hasn't changed...

---

### Post by danwood76 on 2009-05-14
What I meant was my post no. 27.
Disabling effects!
Did you do that already?

---

### Post by Kiliankoe on 2009-05-14
Oh, as I said: They haven't even been enabled :D

---

### Post by Kiliankoe on 2009-05-17
All of the sudden it works... I didn't change anything, just started it for the 50th time and the lagging is gone, at least partially. 

Now the problem has changed a little. When I run Firefox and play any music title in the background, all it takes is some scrolling and the music gets jaggy. A quick look into the System Monitor explains it, I'm constantly scraping the 100%, but why?

Shouldn't 4 gigs of RAM be enough the let the PC run like it should?

---

### Post by ben2talk on 2009-05-17
> **Kiliankoe said:**
> All of the sudden it works... I didn't change anything, just started it for the 50th time and the lagging is gone, at least partially. 

Now the problem has changed a little. When I run Firefox and play any music title in the background, all it takes is some scrolling and the music gets jaggy. A quick look into the System Monitor explains it, I'm constantly scraping the 100%, but why?

Shouldn't 4 gigs of RAM be enough the let the PC run like it should?

Generally 4GB is slightly over the top - unless your PC architecture is entirely 64-bit you can't install more than 4GB, and if you do the BIOS won't allow any operating system (32 or 64 bit) to get at more than 3.5GB from that. It's enough for Ubuntu and a couple of virtual machines (I once ran Ubuntu with Vista and XP running fullscreen also around the cube mostly for fun)

Okay, just a wild stab in the dark after a few upgrades and a few problems. I find troubleshooting this kind of thing can be rather problematic, and sometimes things seem to come and go.

What I usually do now if an install doesn't go too smoothly is to go to my home folder, using Nautilus, and then press CTRL and H to bring up all of the .hidden stuff.

I make a new folder called - strangely enough - AA.hidden (goes to the top of the list) and then cut everything hidden and paste it in there.

Reboot (be prepared for a completely reset system) and see if it runs super fast. If that works, put everything back, and you can simply try to isolate the problem from there...

---

### Post by Kiliankoe on 2009-05-17
I know about my PC not being able to utilize the full 4GB, but it's not like I care that much if it's 4 or 3.5GB ;)

I'll see if I can work something out like that. Thanks for the tip.

---

### Post by bonkadventure2 on 2009-05-17
The way I installed Jaunty through Wubi was by Installing Inteprid(I think that's how to spell it) and upgraded from the internet in 8.10 to 9.04. Yes, mine lags, too, and I have 3 gigs of RAM, which is enormous for Ubuntu. Sorry I couldn't help, but I hope somebody will ;) .

---

### Post by Kiliankoe on 2009-05-17
Oh what wonders... I was just about to try denying Ubuntu the hidden files in the home folder, but before I could I got back to the laggy Ubuntu that created this thread.

Great...

Oh, and hey Bonkadventure2. Nice to see that I'm not the only one ;)

---

