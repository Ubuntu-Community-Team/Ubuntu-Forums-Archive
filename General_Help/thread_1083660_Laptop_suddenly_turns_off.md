---
title: "Laptop suddenly turns off"
date: 2009-03-01
forum: General Help
---

### Post by jackn on 2009-03-01
My laptop, an Asus A8J, has been turning off (without shutting down).
It will do it within a quarter of an hour to an hour or more of starting up.
I cannot then get it to restart right away. I've found that if I go through some voodoo ritual of unplugging, removing and reinserting the battery and then restarting - it will start right away. If I do nothing, it will start up after a while.

This may be due to overheating, but it doesn'P

---

### Post by Pulsewave on 2009-03-01
I had the same problem when using the ATI drivers, i switched to VESA drivers and my system is running cooler.

---

### Post by jackn on 2009-03-02
Thank you kindly, Pulsewave.

I use Nvidia drivers, if I understood your answer.

The laptop has only recently started acting up this way, after about two years of behaving itself impeccably.

---

### Post by blackened on 2009-03-02
Monitor the system temperatures (there should be a panel applet for it). Chances are it has a critical temp limit in the bios and the fan isn't running properly (if at all) causing it to overheat and shutdown before hardware damage is done.

---

### Post by jackn on 2009-03-02
Thank you very much, Blackened.

Indeed, I've been feeling the heat.

I installed "computer temperature monitor", a Gnome applet, and it's at 91C...

Yet, it doesn't happen in XP, so it's not a fan or some other faulty hardware...

In short, it's now a question of what is going on to let it or make it heat up so much? And only under Linux...

---

### Post by Cybie257 on 2009-03-02
I had that problem once on my laptop. Ended up that I had bad RAM.

How much RAM do you have and what distro are you using. 

Also, I had some weird issues on my Toshiba laptop with ACPI. Turning that off helped, but at the time (7.10), when I did that, I lost my sound. :\

BTW, is this when plugged in or Battery, or both?

-Cybie

---

### Post by Gramps on 2009-03-02
Do you hear the fan running when your laptop is running Ubuntu? I know mine don't on my Dell when I run Ubuntu unless I run gkrellm to control the fans along with some applets for the Dell.

---

### Post by jackn on 2009-03-04
> **Gramps said:**
> Do you hear the fan running when your laptop is running Ubuntu? I know mine don't on my Dell when I run Ubuntu unless I run gkrellm to control the fans along with some applets for the Dell.

Thank you, Gramps.
Yes, I do hear the fan. I've always heard it, even when it wasn't turning off. And I also hear it on XP.

> **Cybie257 said:**
> I had that problem once on my laptop. Ended up that I had bad RAM.

How much RAM do you have and what distro are you using. 

Also, I had some weird issues on my Toshiba laptop with ACPI. Turning that off helped, but at the time (7.10), when I did that, I lost my sound. :\

BTW, is this when plugged in or Battery, or both?

-Cybie

Thank you Cybie.
I'm using 8.04 Hardy. I have 2Gb of RAM.
I am both plugged in to the mains and have the battery inserted.

How do I turn off ACPI? What do I lose then?

Sorry about the late response. I answered right away, and apparently the answer didn't register.

Jackn

---

### Post by SamNSane on 2009-03-04
I just have another comment without any real suggestion, other than to just try to monitor the temperatures.

I use Ubuntu 8.04 on two notebooks. One of them is passively cooled, and it definitely runs hotter than it did under either WinXP or Vista, but it never overheats.

The other notebook, a "desktop replacement" type -- Dell Precision M70 -- exhibits some pretty quirky behaviors under Ubuntu and runs MUCH hotter than it did under WinXP and Vista. Sometimes it shuts down due to high temperatures, but it doesn't just quit. The GUI quits, and I'm facing white text on black stating that the system is shutting down because of high temperature.

The system will go months without doing this, and then just do it once or twice in a week. It does seem to be provoked generally by the JRE (and Flash?) running in Firefox at commercial Web sites.

I also run 8.04 on about 8 desktop systems at work, and have never seen the behavior on any of them. They don't even seem to run particularly hot.

---

### Post by jackn on 2009-03-05
Thank you, SamNsane.

I do monitor tempertures.
It's around 90-100 on Ubuntu within minutes.
It's around 65C on XP all along.

Your observations, and the forums, suggest that this is quite widespread.

Right now, it is so disturbing, that I can't use Ubuntu, and I'm on XP most of the time. I hate this, and my productivity has taken a serious dive. While I can get entertainment on XP, my work files are on Ubuntu.

It didn't use to be this way. Although the laptop would overheat, I now realize, it wouldn't turn off.

What can be done?
Jackn

---

### Post by SamNSane on 2009-03-05
> **jackn said:**
> Thank you, SamNsane.

I do monitor tempertures.
It's around 90-100 on Ubuntu within minutes.
It's around 65C on XP all along.

Your observations, and the forums, suggest that this is quite widespread.

Right now, it is so disturbing, that I can't use Ubuntu, and I'm on XP most of the time. I hate this, and my productivity has taken a serious dive. While I can get entertainment on XP, my work files are on Ubuntu.

It didn't use to be this way. Although the laptop would overheat, I now realize, it wouldn't turn off.

What can be done?
Jackn

The doggoned forum logged me out while I was composing a rather long response.

Don't have time to redo the whole thing, so I'll try to tell you what I think in a nutshell.

I think your system uses an nVidia display subsystem. Are you using restricted drivers? If so:
a. How were they installed -- through the standard restricted drivers applet provided by the distro, or through some other means?
b. If using restricted drivers, you might try removing them from the equation temporarily to see what happens to temperatures.

If I see the temps climbing rapidly on my system, I can usually open HTOP or System Monitor and kill the (almost always) javascript/JRE or flash player process that's causing the problem. This can happen AFTER the browser has been closed!

If your situation were not so extreme I'd suggest using an active or passive cooling pad for the notebook. But 90 C is entering serious territory. Running at that temp will reduce component life expectancies in the system. It's just not worth it. You need a more basic fix.

Problems like this can be caused by drivers or issues with kernel / hardware abstraction layer. I know better how to research such things on the Windows platform. I'm pretty new to Linux (since Sept, 2008).

---

### Post by jackn on 2009-03-05
Thank you very much, SamNsane.

Yes, I *am* using Nvidia restricted drivers. 
I don't remember how they were installed for sure, but I'm pretty sure it was through the built-in option.

One piece of advice on the forums mentioned going to VESA drivers, which alleviated the heat.

I don't know how to go about this, and I was thinking there was a more fundamental issue here.
Given your input, it looks like this might be the root issue, so I mean to study this, and try the VESA drivers.
This will, by the way, mean giving up Compiz. I can live with that. Yet, I wonder: is there no way I can get my laptop to run on Linux properly? In other words, do I have to rein in my laptop to run Linux? I have a hard time believing that.

Yes, I'm pretty sure my laptop has been suffering for a while, before it started turning off and forcing me to pay attention, and, in my ignorance, I just let it go, thinking that that kind of heat just came with the territory. Then, it started turning off on me. As to identifying a particular process, I don't know, as this happens regularly know. Unless it's one of my default tabs... But I've always used these self same tabs (mail, online docs...).

I'm grateful for this advice, will look into changing drives, and will report back.

---

### Post by SamNSane on 2009-03-05
> Yes, I am using Nvidia restricted drivers.
I don't remember how they were installed for sure, but I'm pretty sure it was through the built-in option.

If you installed them that way, then reversing the process is easy. Just go to System / Administration / Hardware Drivers. You'll be prompted for your password. When the restricted drivers applet pops up, just uncheck the Enabled box for the nVidia driver. You'll have to reboot the system to complete the changes.

>  This will, by the way, mean giving up Compiz. I can live with that. Yet, I wonder: is there no way I can get my laptop to run on Linux properly? In other words, do I have to rein in my laptop to run Linux? I have a hard time believing that.

I know how you feel. The video subsystem on my computer was a several hundred dollar option, IIRC. There's no doubt that Ubuntu looks better when you're running Compiz -- assuming that it's working properly. But killing the hardware isn't going to do anyone any good.

All I know is that the OpenSource developers working on the hardware abstraction layer and the kernel are at a disadvantage when they have to try to make that stuff work with proprietary drivers for which they have no source code. We nVidia users are caught in the middle. No matter who we complain to, they can point to the other side as the culprit. But, if nVidia wants to provide only closed source drivers to the Open Source development community, then I'm going to place the blame for the problem squarely on nVidia's shoulders. I think the onus is on them to solve problems like this.

Frankly, they won't be seeing any more of my money unless they go Open Source.

Anyway, if taking the restricted drivers out of the equation alleviates your problem with overheating, you have two basic choices:

1. Keep using the standard Open Source drivers and do without all of the nice special effects. (This isn't just a matter of decoration. Many of the features are truly useful.)

2. Download some of the more recent drivers directly from nVidia and try to install them on your system.

That second choice is not for the faint of heart. It's not rocket science, but it can definitely result in a borked OS (or at least a borked GUI). So, before you do it, you need to be sure you have all data backed up to external devices and / or media.

Another thing to remember about downloading and installing the drivers that don't come through the Ubuntu repositories is that, any time there's a kernel upgrade, you have to revert to the VESA drivers, do the kernel upgrade, then recompile the drivers for the new kernel version. Again, not rocket science, but hardly a point-and-click operation.

My opinion is that nVidia could definitely be providing better service to its customers.

---

### Post by jackn on 2009-03-05
OK, that was very helpful.

I went ahead and unchecked the nVidia driver.
This I did before launching Firefox, thinking that I would that way tell apart Firefox's demands on the system from nVidia's.
As soon as I launched Firefox, with the proprietary driver off, the temperature rise started, exactly what sent me to this forum to begin with.
It was only then that I started suspecting that my having more than twenty or so tabs open might have anything to do with it.
Yes, I hate to admit, but I've been hogging the net and, it appears, my own resources, by leaving tabs sitting around till I get around to consulting them.
I then went on a drastic Firefox tab reducing diet. 
The temperature was going down!
I went on killing tabs and taking notes about those I wanted to keep. I ended up with six tabs, which is all I'm going to allow myself from now on.
The temperature was around 65C, which is what it is on XP.
I then turned on the nVidia driver anew, and, what do you know, the temp is still around 65 all the time...

I am not familiar with the cooling devices you mention. I wonder about their cost and portability.
I can handle some fall in life expectancy, as I expect with constant innovation, the laptop might not be up to snuff anymore before it is physically worn out.

Come to think of it, I could also live without Compiz. It was just annoying to think that my OS can't handle my computer. Fortunately, this turns out not to be the case.

I guess one final trial would be to go back and open lots of tabs, but I don't feel like it. I'm convinced.

Thak you kindly, SamNsane.
It's been a worrisome few days there.

---

### Post by SamNSane on 2009-03-05
Hi, jackn.

Well, that's interesting. I guess that you have, at least, found a way in which you can work with your system. I know that opening that many tabs -- especially if there's much Javascript / Flash going on on the pages -- would cause my system with the nVidia card to flake out, too.

The sad thing is that it doesn't cause any problems to put the same system through such extreme usage in Windows. I just did some serious testing of the little Panasonic notebook under Ubuntu. It, too, runs Compiz and desktop effects, but with Open Source drivers. It gets warm, but it throttles properly and never overheats. That's as it should be. No matter how hard you run a system, it shouldn't overheat. It should eventually bog down and become slow, get warm, even throttle down -- but never overheat to the point of forcing thermal shutdown protection from the BIOS. At least not without severe environmental problems like using it in a 100 degree room.

You could still do some testing by switching out add-ons / extensions / plugins that are installed in Firefox. I don't know what you would learn, but you might find a combination that lets you run more tabs. I haven't found any magical combination, though.

At least you have Compiz and desktop effects and have a workable configuration. I hope it stays that way. Remember that even closing some tabs, or even all Firefox instances, may not always kill the related processes. I have seen Gstreamer, for instance, still laboring away burning cycles long after the page that was using it (and the browser) was closed. You may have to manually kill a runaway child thread from the browser on occasion in order to keep from overheating.

Here's a link you might want to check out.

[http://news.cnet.com/8301-17938_105-9700201-1.html](http://news.cnet.com/8301-17938_105-9700201-1.html)

It's a test of several notebook coolers. I've never actually used one, but I've certainly noticed the difference just the surface type on which the computer sits can make a substantial difference in the GPU and CPU temps.

Please post back if you learn anything more!

---

### Post by jackn on 2009-03-06
Yes, true enough, it's too bad it all means that Ubuntu, or Linux really, underperforms Windows, on this count at least, and for the source availability reasons you mentioned. Not that I'd look back.

To you, SamNsane, what accounts for the Panasonic mini's ability to handle the same tasks without overheating?

I've looked at the link, and I now understand these coolers better. 
I realize now that laptops getting hot is a widespread problem, as I took the case to be without too much thought (which is, however, an issue distinct from temperature differences between Linux and Windows).
When the laptop came in and my son couldn't hold it in his lap while sitting cross-legged, I improvised by providing a cardboard binder as an insulator, which I've since kept as the permanent base for the laptop.

I'm grateful for the accompaniment and advice you've provided. It was very necessary and helpful, not to mention enlightening.

BTW, am I right in thinking that there's currently no way, other than manual, to mark a thread as solved?!

---

### Post by SamNSane on 2009-03-06
> 
Yes, true enough, it's too bad it all means that Ubuntu, or Linux really, underperforms Windows, on this count at least, and for the source availability reasons you mentioned. Not that I'd look back.


Despite being handicapped with all of the legacy stuff they must support, Microsoft actually does a superb job of producing a first rate operating system -- for some purposes, particularly traditional office roles. Their driver support in Vista is almost stupefyingly good. If you can't get a device driver for a device in Vista it's because the company that produced the device put absolutely no energy into supporting it. The memory management and GUI responsiveness are superior, too. Vista really pops on the Precision M70. Ubuntu is responsive, but operates with nowhere near the same panache on this computer. I use Linux because it's the right tool for me -- oddly enough in doing systems management on a huge variety of systems -- mostly Windows but also mainframes / minis / Unix / MacIntosh / CP/M (yes, honestly) / Apple //e (yes, really).

I also use Ubuntu because I really like being able to customize my environment to this extent. For instance, you'd have to break Windows to change the logon screen (from their allowed choices) in any substantive way. It's also terribly easy to outfit Linux with the tools you need for managing remote systems. In Windows it's easy enough to get tools for managing other Windows systems, but you often have to go "third party" with at least some attendant cross-platform annoyances in order to achieve the same level of flexibility in management capabilities.

I also love being able to do research to find real answers to problems. In the closed source community there are lots of "proprietary issues" that interfere materially with a systems administrator's ability to get all the information s/he needs to troubleshoot a problem. With Linux, even though there are certain signal-to-noise issues at times, you can always get the real dope on just about anything if you look hard enough.

> 
...what accounts for the Panasonic mini's ability to handle the same tasks without overheating?


It's chipset / video combination is simply better supported by the drivers available and the Gnome desktop environment in Ubuntu 8.04. They behave themselves because nothing untoward is being demanded of them. With the Dell Precision M70 there's something missing in the support that causes what may be a race condition in the CPU. I know it's not a problem with fan control because, when the overheating issue occurs, the fans on this thing start screaming before the temperature has risen more than a few degrees. It's just that they aren't enough to cope with what's being demanded of the processor. And it is the CPU that is being maxed out, not the GPU. But the reason I think the problem is in the nVidia drivers / hardware design is that reverting to the non-restricted drivers eliminates the problem. Of course it causes other problems, like the system locking up if the "wrong" OpenGL screensaver is chosen, and not having some useful desktop effects like the desktop zoom and window transparency.

I should tell you that the Panasonic worked LESS well than the Dell in Ubuntu 8.10. It didn't overheat, but it had terrible power management problems that made it completely useless under that OS. I don't know whether that was a driver problem or an issue with a change in the desktop environment.

Incidentally, there are few "laptops" made these days which should be used on the lap. I think that's why the vendors started calling them notebooks years ago. The majority have cooling fans which exhaust through the base of the system. Placing them on a lap / clothing is a sure way to get them to overheat if you're blocking a fan opening. But laps also insulate the case so that it is less well able find a "heat sink". A cool desktop works a lot better than a lap for the purposes of transmitting heat away from the computer. Most manuals for these things tell users not to use them in the lap or on cloth (like bedclothes or tablecloth) -- that they should be used on a desk or table, or on a laptop tray, perhaps.

My little Panasonic is somewhat of an exception, since it is passively cooled. On the other hand, it runs too warm to hold comfortably in one's lap for more than a few minutes anyway.

> 
am I right in thinking that there's currently no way, other than manual, to mark a thread as solved?! 


I believe all of those special features for marking posts and threads disappeared during / following a maintenance issue the forums had a couple of months ago.

It has been fun working with you. I'm sorry we weren't able to find anything more substantive than a workaround, but I hope you'll at least be able to use the OS now -- and without watching your computer go up in smoke.

;)

---

### Post by josvanr on 2011-03-06
for anyone looking for an answer to the laptop suddenly turnign off:

unscrew the bottom and clean the fan and outlet as good as possible first ! !

worked for me (at least ... .uptime 35 min so far as opposed to 1 minute

previously)...


josvanr


ps a day later I'm still fine!

---

