---
title: "Trash Icon, Automount and several other problems"
date: 2010-12-13
forum: Desktop Environments
---

### Post by Zlikavac32 on 2010-12-13
Hi, 

first of all, I'd like to thank this forum (since this is my first post here) for helping me to find my way through Ubuntu OS (for about a year and a half).

I have a problem that's driving me crazy and I don't know what's causing it so don't know where to look (since all my guesses where not right - later in post). But I do know one thing. I think it started when I tried to install Pango dev files manually and to through apt-get.

First little intro.

It all stared 10 days ago. When I installed Pango and restarted computer, I've got some squares and strange symbols (in whole system, even terminal). My guess was it was pango so I removed it from safe mode and it was back in normal. Then I installed gtk-dev from apt-get and some system updates as well.

This is when my problems started to show. Automount was disabled and could not be enabled, trash icon missing and unable to restore and when logedout/logedin icons on Desktop are reseted.

What did I try to solve this?

First for trash icon. 

[LIST=1]
[*]Add to panel
[*]Delete panel then add it
[*]Reinstall applets and then repeat 1. and 2.
[*]Few other tutorials and solutions I found on net and here
[/LIST]
This all was a fail without success.

Automount.

[LIST=1]
[*]Check if /apps/nautilus/preferences/media_automount is unchecked but it was checked
[/LIST]
Desktop icon position reseting

[LIST=1]
[*]I have no idea what I tried, think nothing
[/LIST]


So, these are my problems. An other reason why I guess it's Pango problem is that when I installed gtk-dev through apt-get on my laptop there where no problems but on my computer (first pango from src then from apt-get) there are problems.

I don't know how to get rid of these problems (since I tried to reinstall everything that was updated in past 30 days.

---

### Post by Zlikavac32 on 2010-12-14
Upgrading to 10.10 also didn't help.

About trash icon, 

Using panel-test-applets it starts trash applet windows but it's 1px in width and when resized there is no icon inside that window. Also when clicked inside window I get error 

[B]Error while spawning nautilus:
Operation not supported[/B]

I double checked and all images are there (those I found out that are used in sourcecode of trash applet).

This happens also if new user is created. That used has same problems as my account.


If someone could help me I'd be veeery thankful since I don't wanna reinstall whole system :(

---

### Post by Krytarik on 2010-12-15
So, I got that you installed Pango from source? How did you remove it, is it possible that some files from the Pango installation remained and probably have replaced some important system files?

---

### Post by Zlikavac32 on 2010-12-18
> **Krytarik said:**
> So, I got that you installed Pango from source? How did you remove it, is it possible that some files from the Pango installation remained and probably have replaced some important system files?

Don't have to worry about it anymore. 

I reinstalled system and now it works. I also installed pango from source and this time it worked just fine. Don't know what happened but doesn't mater anymore. I've lost few days  trying to solve this and it took me just 5hrs to reinstall system and restore it back how it was :).

---

### Post by Krytarik on 2010-12-18
Sometimes it would have been really faster just to re-install, but I also want to avoid it as much as I can. I just recently spent a couple of days to manually restore a system image of Windows, which I made with its included backup tool a year ago, on a new hard drive, which the Windows tool obviously ins't able to do. And after that was successful I had of course to update most of the installed applications. Now I use CloneDVD as backup tool for all OSes.

Then please mark the thread as solved, via "Thread Tools"

---

