---
title: "Showing Power Manager Icon in Icon tray on Desktop CPU using 13.04"
date: 2013-08-04
forum: Desktop Environments
---

### Post by jdallara on 2013-08-04
On my lap top computer, the power manager icon is in the icon tray and shows me the status of the lap top's battery.  It also shows me the charge state of my Iphone when it is attached via USB.  On my desktop, the icon doesn't show (desktop doesn't have a battery, I know), but when I go to system settings -> power, my Iphone shows up when it is connected.  Is there a way that I can have the power manager icon show in the icon tray either all the time or at least when the Iphone is attached?  My Iphone is my network interface and I can't see if it is charging when I'm on the computer because it is up on a shelf out of view.

Thanks in advance,

Jon.

---

### Post by jdallara on 2013-08-04
Sorry, Gnome classic DE.

---

### Post by jdallara on 2013-08-07
On my lap top computer, the power manager icon is in the icon tray and  shows me the status of the lap top's battery.  It also shows me the  charge state of my Iphone when it is attached via USB.  On my desktop,  the icon doesn't show (desktop doesn't have a battery, I know), but when  I go to system settings -> power, my Iphone shows up when it is  connected.  Is there a way that I can have the power manager icon show  in the icon tray either all the time or at least when the Iphone is  attached?  My Iphone is my network interface and I can't see if it is  charging when I'm on the computer because it is up on a shelf out of  view.

Ubuntu 13.04
Gnome Classic DE

Thanks in advance,

Jon.

---

### Post by bapoumba on 2013-08-07
Threads merged.
Please check you have the indicator-power package installed.
In System Settings > Power > show the battery status when battery is charging / in use

---

### Post by jdallara on 2013-08-08
Right.  Indicator-power package is installed.  I can see it using system settings - > power.  I want the icon to show in my system tray on my desktop system as it does on my laptop.  See the attached screen shot from my laptop.

Thanks, Jon.[ATTACH=CONFIG]245177[/ATTACH]

---

### Post by bapoumba on 2013-08-08
Yes, I did understand that. I have laptops, need to go see on my kids desktop if it can be done, but not just right now, sorry :)

---

### Post by jdallara on 2013-08-08
No problem.  Thanks for wanting to give it a try.  I'm in no hurry, it is not a major problem, I'd just like it to show on the desktop if it is possible, which it should be.  Most likely there is a command line switch or something similar, but I don't know where to look for the documentation.

Thanks again,

Jon.

---

### Post by bapoumba on 2013-08-09
I'm currently looking around dconf-editor, but not sure how it is different from my current laptop configs. This laptop battery died a few weeks back :)

---

### Post by jdallara on 2013-08-10
I also poked around in dconf and found the setting for showing the icon.  The setting is com->canonical->indicator->power->icon-policy.  The options are present, charging, never.  Tried different settings with no effect.  Both my laptop and desktop are set to present.  Must be something else that triggers it.  I'll keep looking.

---

### Post by bapoumba on 2013-08-10
Yeah, I have been looking around too.

This bug is not directly related to your symptoms and your wishes, but it reminded me of an old old thing I had to do : add a "vendor" line somewhere in order for my (now dead) palm gets recognized. maybe something along these lines ? I know it is vague, sorry, i'll try to think a little further. May be someone else will have a bright idea ?
[https://bugs.launchpad.net/ubuntu/+source/indicator-power/+bug/1103064](https://bugs.launchpad.net/ubuntu/+source/indicator-power/+bug/1103064)

---

### Post by jdallara on 2013-08-11
I looked at the bug report and I tried playing around with upower --dump and upower --monitor-detail and got the following:


On the laptop, upower sees the power supply attached to the laptop (the power supply info disappears if I disconnect it).  On the desktop, upower doesn't see the power supply.  Maybe it has something to do with the ACAD function ignoring the power supply on the desktop because it is not detachable or the supply sends a code that causes ACAD to ignore it?  Sort of looks like that might be the determining factor.  I'll see if I can find out anything about the ACAD function.

Merci et prendre soin,

Jon.

---

### Post by bapoumba on 2013-08-11
Well, I looked around before reading your txt files and came up with the same path for the battery details from here: [https://mail.gnome.org/archives/gnome-power-manager-list/2010-March/msg00002.html](https://mail.gnome.org/archives/gnome-power-manager-list/2010-March/msg00002.html), That was after reading a lot of bug reports and things. Looks to me, as my own battery details are in these files, it gets populated during the install process. On a desktop, the installer (or some other component) may be detects there is no battery and the whole thing gets a different config. Is it possible to force it to behave on a desktop the same way it behaves on a laptop ? I do not know.

---

### Post by jdallara on 2013-08-11
Interesting twist.  If it occurs during the install, then there has to be a configuration file somewhere that contains this information and can either be edited or modified in some way to fool upower into thinking that it is funning on a laptop instead of a desktop.  Just force battery level to 100% and state to charging, and it should work fine.  Should I post something on the installation&upgrades forum to see if anyone knows about this?

---

### Post by bapoumba on 2013-08-11
Well, Installation and Upgrade is mainly followed by people who help with packages installs (and problems).

I'd say Hardware. Please keep in mind the installation thing is all speculation from me :)

---

### Post by jdallara on 2013-08-11
Ok, I'll try there.  Yes it is all speculation, but it would make a lot of sense to gather that information at install time since it is static and not subject to change like the Iphone, or a battery powered keyboard.  I'll let you know what I find.

Thanks,

Jon.

---

### Post by bapoumba on 2013-08-11
Sure, please. I'll subscribe to your new thread and you can link back here.

---

### Post by jdallara on 2013-08-11
new thread in Hardware #2166928

---

### Post by bapoumba on 2013-08-11
OK thanks, I've subscribed to it :)

---

### Post by jdallara on 2013-08-27
Well it looks like this thread has died due to lack of interest.  I did look at the upower documentation and delved into finding the ACAD information storage, but other than finding some of the most horrendous circular and relative referenced links that I have ever seen, I couldn't find any location where the configuration information for the system is stored.  If anyone knows anything about the system internals that could shed some light on this configuration information so that I can trick upower to thinking its running on a laptop instead of a desktop I'd love to hear it.  Otherwise, I'll have to look into it when I have some free time.  Much thanks to bapoumba for your help.

Thanks,

Jon.

---

### Post by bapoumba on 2013-08-28
May be not lack of interest, but may be that is something people just do not know about. Searched around and did not find anything relevant..

---

### Post by jdallara on 2013-08-29
All I have been able to locate thus far points to kernel level or low level system operation.  Which forum would those people be watching?  My post in hardware didn't get any nibbles.  The Upower daemon is the application that displays the information and ACAD is a system level application that gathers the information.  It would seem that I need to catch and modify the information that ACAD is returning or providing, but the documentation is not there.  I've looked at the Upower website and I've found the ACAD directory tree, but it becomes a series of symbolic links that use multiple levels of redirection, often times to non-existant directories.  I'm writing this based on memory as I haven't looked at it for a week or so and I don't have it on screen.  Anyhow, if you or anyone else knows where to redirect this thread please let me know.  This is almost starting to be come a mission and I'd hate to have to end up writing my own application.

Thanks,
Jon.

---

### Post by bapoumba on 2013-08-29
OK, a quick search (no tim, not lack of interest). Been looking around LFS docs, as there could be some information there.
[http://www.linuxfromscratch.org/blfs/view/svn/general/upower.html](http://www.linuxfromscratch.org/blfs/view/svn/general/upower.html)
[http://upower.freedesktop.org/docs/](http://upower.freedesktop.org/docs/)

If you have not already read these :)

---

### Post by jdallara on 2013-08-30
Did look at upower.freedesktop.org and that is where I picked up the ACAD trail.  Haven't heard of the other one but it sounds like it would be interesting to look at, if nothing else than to see what all they have there.  I've always been interested in OS internals.  Like you, I haven't had any free time recently.  I'll keep you posted if I find anything interesting.

Thanks,
Jon.

---

### Post by bapoumba on 2013-08-31
> **jdallara said:**
> Did look at upower.freedesktop.org and that is where I picked up the ACAD trail.  Haven't heard of the other one but it sounds like it would be interesting to look at, if nothing else than to see what all they have there.  I've always been interested in OS internals.  Like you, I haven't had any free time recently.  I'll keep you posted if I find anything interesting.

Thanks,
Jon.

OK, I thought about LFS because as it says, you have to do it from scratch. Maybe there will be something in their doc.

---

### Post by jdallara on 2013-08-31
LFS may have something.  Its more about how to put together a custom system from package sources, however there are some links to docs.  One thing that I'm finding is that most of the documentation that I'm coming across is woefully out of date.  I was on the 'Linux Documentation Project' site last night and most docs are 10+ years old.  The most recent kernel documentation I found there was for 2.6.  I know that the documentation is the last thing that gets completed in a software project (ex-programmer, IT engineer, HP-UX admin here), but...

---

### Post by bapoumba on 2013-08-31
Hmm, yes, I see.. I have some time for the forums today. When I'm done with what I wanted to do, I'll browse around :)

---

### Post by bapoumba on 2013-08-31
Although not all on ubuntu, and most of it well over my head, some comments here sound interesting (the BAT1, when most of them talk about BAT0 and timings) : [https://bugzilla.redhat.com/show_bug.cgi?id=521874](https://bugzilla.redhat.com/show_bug.cgi?id=521874)
Somewhere else, there was a mention of acpitool : [http://linux.die.net/man/1/acpitool](http://linux.die.net/man/1/acpitool) (please read down there also are some issues with this application)

Is the power supply info in the bios ?

---

### Post by jdallara on 2013-09-02
I downloaded the Linux kernel documentation package last night and it is going to take a little while to sift through it.  I have found some info on acpi and another doc on power supply information system calls.  I'll take a look at the links that you found, but right now I was looking at /usr/share/doc/linux-doc/power that describes system calls to determine battery status and other information.  Most of the files in the directory seem to be geared to laptops and software suspending of the system.  However, acpi is mentioned and the power_supply_class is detailed.  I'm not sure the information is in the bios but it is at a low system level where in you're talking directly to the hardware, although this information might be cached some where.

---

### Post by bapoumba on 2013-09-02
All I can say is best of luck, and learn something in the process. Please share if you find anything interesting :)

---

### Post by jdallara on 2013-09-02
Thank you for all the help that you have given me.  You are a credit to this forum.  I will post what I find.  Spent a couple of hours today reading through some of the documentation and found a lot of interesting information that has nothing to do with this thread. Currently, I've got to try to find out why Wine has started to give me OpenGL errors on my laptop.  Started a few updates ago, not sure exactly when but I think it was after upgrading to 13.04.  I need it to run my CAD software when I'm out in the field.  It's working fine on my desktop, which is my drafting platform due to its power, which is why I didn't notice the problem until a short while ago when I got ready to do a presentation for a client.  May have to regress the laptop back to 12.10.  Anyhow, thanks again for your help.

Best wishes,
Jon.

---

### Post by bapoumba on 2013-09-05
You are most welcome, I do not feel I have been of much use to you, thanks for your kind words :)

---

