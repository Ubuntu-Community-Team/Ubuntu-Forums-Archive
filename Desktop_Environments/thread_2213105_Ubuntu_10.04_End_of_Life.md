---
title: "Ubuntu 10.04: End of Life?"
date: 2014-03-24
forum: Desktop Environments
---

### Post by Kurt_Alan on 2014-03-24
****

I have been an Ubuntu user since 6.X, Dapper Drake.  My pre-Unity "sweet spot" is 10.04 Lucid Lynx LTS.

I have no Plan B.  Is there such a thing as end-of-life? How many years can I keep going? Ramifications?

---

### Post by Iowan on 2014-03-24
[http://www.ubuntu.com/info/release-end-of-life](http://www.ubuntu.com/info/release-end-of-life)
Here's a place to start.

---

### Post by deadflowr on 2014-03-24
Ramifications of using an end of life distro?

Well, end of life means that NO package will get any update ever again.
Now, 10.04 is an odd one because the server version is still up and running, so I would guess you might still get some system wide non-desktop packages to be updated.
But think about those packages for the desktop that won't.
Chief among them is X. the xserver which will never be updated for lucid, and if any exploit is found, which is a strong possibility, could cause your system to be harmed or damaged.
So that's something to think about.

---

### Post by buzzingrobot on 2014-03-25
10.04 desktop reached EOL in May 2013.  10.04 server reaches EOL in April 2015.

Lack of security patches is the big issue. A system that was completely updated the day before EOL is now vulnerable to any exploit disseminated since then.

if it's the Gnome 2 interface that keeps you on 10.04, take a look at using the Mate Desktop on Ubuntu, or from Linux Mint. Mate is the Gnome 2 codebase forked, patched, and migrated into 2014.

---

### Post by grahammechanical on 2014-03-25
You can keep going until the hardware brakes down. Then you may find that 10.04 does not have driver modules for newer hardware. Then you will have to install a newer Linux kernel and that may need supporting libraries that are not in the 10.04 repositories. which, by the way are now closed and have been relocated. So, right now updates will fail. And so will attempts to install software from the 10.04 repositories.

---

### Post by Kurt_Alan on 2014-03-28
Thank you.    Probably I'll stay with what I have.  For me, there is no substitute for menus and panels.  I see I'm still getting some updates on 10.04.

---

### Post by Kurt_Alan on 2014-03-28
Thank you.  I looked at MATE.  For me, the killer Gnome 2 combo is menus plus panels.  MATE has menus but no panels. Sticking with 10.04 if and until a deal-breaker appears.

---

### Post by slooksterpsv on 2014-03-28
Look into elementaryOS - it's amazing. Not really like Gnome 2 (I miss Gnome 2 and MATE can never replace it =( ), but it satisfied my need. Also Xubuntu can be changed to look a lot like Gnome 2.

---

### Post by buzzingrobot on 2014-03-28
> **Kurt_Alan said:**
> Thank you.  I looked at MATE.  For me, the killer Gnome 2 combo is menus plus panels.  MATE has menus but no panels. Sticking with 10.04 if and until a deal-breaker appears.

I'm not sure what you mean about panels. 

Mate, for all practical purposes, is Gnome 2, so I don't understand why some folks think it is so entirely different.  Are they thinking about appearance -- the old Ubuntu themes -- that Canonical used?

In Mate, the menus drop down from panels. They are the same panels, the same menus, using the same code, as in Gnome 2.

Mint's Mate defaults to one panel and its own menu design.  The traditional menus and more panels are added in a couple of clicks.

---

### Post by silex89 on 2014-03-28
Hi there! :)

What I would personally suggest you is to give a sincere try to the latest releases (like 12.04 LTS or 13.10) and install the gnome-panel package with a simple sudo apt-get order. You'll get two extra sessions, one that is "very" similar to what Gnome used to be, with some Compiz plugins enabled, and the other one with stock metacity if you're not into compositing your desktop.

Best of Luck!

---

### Post by monkeybrain20122 on 2014-03-28
Wow, it never ceases to amaze me that some people so hate changes that they would rather stick to a completely dead  OS for the sake of familiarity instead of venture out  a little bit for something fresh and new. "the menu and panel are killer features"? you gotta be kidding, but that is just my opinion. 

However, it is not just opinion that are plenty of 'classic' des available in more up to date incarnations:gnome-flashback, lxde, mate, xfce.. to name a few.

Ubuntu and Linux in general have improved so much since 2010 that 10.04 feels like from last the last century. To be still running 10.04 is not only a security nightmare, but also a massive scale back of functionality. I would find it very crippling to run such an OS now, regardless of DE (I remember even evince was so slow in 10.04 that it was almost unusable, I had to grab the version from Maverick development instead, which was a lot faster) And all that because of the menu and panel? I don't get it especially since you can get those in up to date releases.

 I predict many people will stick with XP through hell and high water whether MS supports it or not. :)

---

### Post by slooksterpsv on 2014-03-28
There was a lot you could do with the panels. Anymore, things don't work, aren't compatible, etc. so I can see why he wanted a gnome2-like interface. It was the BEST in my opinion.

elementary OS and Xubuntu are still my favorite.

---

### Post by KBD47 on 2014-03-28
Really old hardware can be a problem for some people with the newer Ubuntu releases. I have a 10 year old desktop beast that nothing but Debian would run on without video issues until I tried Linux Lite. Lite is Ubuntu 12.04 based but they must have some additional drivers or something in it. Linux Lite also works well on a 9 year old desktop that Ubuntu quit working well on after the 11.10 version.

---

### Post by buzzingrobot on 2014-03-29
> **monkeybrain20122 said:**
>  "the menu and panel are killer features"? you gotta be kidding, but that is just my opinion. 

To each, their own, I guess.  But, a lot of people really don't like *any* change.  I still see people complaining that something can't be done or isn't available in Unity/Gnome Shell when, in fact, it can be done and it is available. 

My requirements are simple: One app per workspace, one click to move between apps.  I can configure all the major DE's to do that.

> To be still running 10.04 is not only a security nightmare, but also a massive scale back of functionality. 

2010 all over again. (And I still don't know what "no panels in Mate" means. ;)) 

 > I predict many people will stick with XP through hell and high water whether MS supports it or not. :)

Oh, yeah. People are already out there marketing "Keep Your XP" snake oil.

---

### Post by Kurt_Alan on 2014-03-29
I re-visited Xubuntu.  Thanks for the suggestion.  I see that it can be configured to be gnome-like and that it has menus.  However, I tried this a couple of years ago.  It has one deal-breaker for me: I am low vision and xcfe doesn't cut it.  On Gnome 2 and 10.04 my objects and text are HUGE.  I also looked at elemantary os.  Interesting.
I have an emotional investment with Ubuntu since Dapper Drake--as much as I hate Unity.  However, I see that in 14.04 some limited menu items can be turned on in Appearances . . .

---

### Post by Kurt_Alan on 2014-03-29
Panels.  I remember spending hours reading through the Gnome desktop tutorial.  I can set up one to four panels on the perimeter of my display.  I can add arrows to collapse them.  I can make them translucent and adjust their width. I can drag and drop apps to different panels.  One panel, for example, contains all music apps.  I can add applets to each panel.  I can get real-time displays on my cpu, RAM, etc. In Unity panels are history.  For me, they are critical for my workflow and there is no substitute.

---

### Post by Kurt_Alan on 2014-03-29
I understand your sentiment.  I should have stated that I have tried xfce, Cinnamon, MATE and different flavors of Unity. Xfce is a deal-breaker for low-vision accessibility. Unity is clean and elegant.  But inductive menus? Are you kidding me?  Like going into a restaurant and asking for a menu and being handed a keyboard.

Sure, I am suffering big negatives staying with 10.04, for example, the kernel is obsolete for TRIM . . .

---

### Post by Kurt_Alan on 2014-03-29
Good idea.  I think I will try this with Trusty Tahr and see how close I can get to Gnome 2.  Thanks.

---

### Post by Kurt_Alan on 2014-05-15
**[SIZE=5][/SIZE]**

I have jettisoned the "love of my life," Gnome 2 (and 10.04 LTS), and am making peace with Unity (and 14.04 LTS).

I have done this via a thorough reading of the pre-packaged "Help" and by searching for tweaks that enable me to do work the way I want it done.

"Workspaces" are critical to my workflow.  This is one program that Gnome 2 implements better than Unity.  For example, in a Gnome 2 panel, my workspaces are labeled and evident; in Unity they are hidden.  And instead of a single mouse click in Gnome 2, I must use Super + S before clicking or using arrow keys--and since I can't see my workspaces from my Desktop, it's "out of sight, out of mind" -- I forget what is located where.

However, long story short, from a Unity hater, I'm becoming a Unity lover . . .

---

### Post by buzzingrobot on 2014-05-15
> **Kurt_Alan said:**
> 

...in a Gnome 2 panel, my workspaces are labeled and evident; in Unity they are hidden.  And instead of a single mouse click in Gnome 2, I must use Super + S before clicking or using arrow keys...

You can attach Unity's version of a pager to the Launcher via the Appearance panel in System Settings. (The Behavior tab, I think.) Can't go to a specific workspace in one click, it just exposes all workspaces.  But, at least it avoids the need for the keyboard. 

Instead, I usually just click on the icon of a running app in the Launcher.  That moves the display to whatever workspace it's in.

---

### Post by Kurt_Alan on 2014-05-15
**[SIZE=5][COLOR="#000000"][/COLOR][/SIZE]**

Yes, I have done that but it didn't work because the switcher went to the bottom of the Launcher, squeezed out by other apps.  Hey! Just found out that the Switcher is movable, so now it is at the top of my Launcher where I can see it.

This is an improvement.

---

