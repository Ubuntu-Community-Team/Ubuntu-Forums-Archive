---
title: "Using KDE Apps in LXDE"
date: 2012-12-04
forum: Desktop Environments
---

### Post by Iggy64 on 2012-12-04
My question will probably demonstrate what a newcomer I am.  I have been slowly learning about Linux for several months, hoping to get completely away from Windows.  Currently, I am running Ubuntu 12.10 with LXDE.  Other than my frustration with the limitations of the alacarte menu manager, I am quite pleased with this setup.

I have an extremely limited grasp of the whole GNOME versus KDE business.  Nevertheless, I have a few times ventured to install an app from the KDE side of the tracks.  In some cases, this seemed to result in a staggering barrage of new packages, most of which I have no idea what they are or what they do.  Apparently, these are the KDE "dependencies" I have been hearing about.

So I have these newbie questions:

1) Is it considered smart (or best practice) to stick with GNOME apps in an LXDE (or Peppermint) environment?  

2) Is there a surefire way to see how much extra baggage a KDE app will bring along BEFORE deciding to try it out?

3) If and when I do install a KDE app, along with all its baggage, does the extra baggage simply use up disk space?  Or can it somehow affect the performance of my LXDE system?

Thanks!

---

### Post by TenPlus1 on 2012-12-04
Personally I use Synaptic Package Manager to install software which gives me a good idea which packages are going to be installed alongside a specific package or program and what size it will take up on the hard-drive...  I tend to stick with gtk or qt4 applications and avoid kde apps that bring in the runtimes which can be rather large...  If you shop around you tend to find alternatives to any program running on different gui's (gnome, kde, qt4, gtk, e17 and X)...

---

### Post by black veils on 2012-12-05
> limitations of the alacarte menu manageryou can manually edit the menu files located at **/usr/share/applications**
dont delete any. you can change the menu category for that entry, name, or hide it. the categories arent always the same as shown in the menu, eg. you may have **accessories**, but in the file it will say **utility**. to edit these files, first you need to open the file manager with extra privileges, open the terminal and copy-paste ```
gksudo pcmanfm
``` unless you use an alternative file manager. warning though, i have found that while having pcmanfm open with privileges, it randomly closes at times.

> I have an extremely limited grasp of the whole GNOME versus KDE business.
there are different desktops, apps are created with different software which is specifically for a certain desktop. if you load a kde app in the gnome environment, it has to also load other background stuff, which would be running by default in the kde environment.

> 1) Is it considered smart (or best practice) to stick with GNOME apps in an LXDE (or Peppermint) environment?  it is considered best for performance and saving on disk space, to use gtk apps (or some lighter tollkit), but it depends on your hardware, and what compromises you are willing to make.

> 3) If and when I do install a KDE app, along with all its baggage, does the extra baggage simply use up disk space?  Or can it somehow affect the performance of my LXDE system?both, but it depends on what hardware you have, as to how much of an impact you will notice.
also, if you see different themes due to those applications, there is an application called **qt4-qtconfig**, install it, then on the appearance tab, under GUI style, select GTK+. restart your kde app and it should be the same as you system. you will also notice different icon theme, there is a tweak for that too, but it can confuse your font settings which can be awkward to sort, and i am not sure how you would deal with that in lxde. - install **systemsettings**, then go to application appearance.

---

### Post by Iggy64 on 2012-12-05
Many thanks to TenPlus1 for the new perspective.  Now I see that KDE is an entire environment that sits on top of Qt; so if an app is part of KDE, it brings along the extra run-time files.  I wasn't appreciating the difference between the programming language, the widget toolkit, and the desktop environment.  You've helped me know what to read about.  Much appreciated.

Also grateful to black veils for taking time to clarify several items for me.  I'll definitely try the manual editing of the menu.  I hadn't found any instructions on how to do that, so this is very helpful.  Your comments on apps from different toolkits and environments are also very welcome.

I obviously have a ton to learn; but this support from the forum gets me going and helps me find the right things to read about next.

---

### Post by mike555 on 2012-12-05
For editing the lxde menu you might install " menulibre " it works good for me (on Lubuntu)

---

### Post by SeijiSensei on 2012-12-06
I suggest you burn a Kubuntu CD and run it in the "Try Ubuntu" mode to see what it looks like and how well it performs with your hardware.  I'd start with the stable [12.04.1 release]("http://cdimage.ubuntu.com/kubuntu/releases/12.04.1/release/").

Remember that the fact that the OS will need to load everything off the CD will make it seem a bit slow, though once an application is running it should be fine.  You can also install the CD image to a [USB pen drive]("https://help.ubuntu.com/community/Installation/FromUSBStick") and boot from that.  Performance will be slightly better.

---

### Post by Iggy64 on 2012-12-07
Thanks, mike555.  I will check out menulibre.  It would sure be great to be able to make a clean, organized menu.  Otherwise, I will have to plaster launchers all over the desktop.

Also appreciate the thoughts from SeijiSensei.  I don't think I want to seriously consider running the KDE desktop at this time (due to running on an old laptop).  However, it might be worth some giggles just to see what it's all about, using a LiveCD.  It can't hurt, and maybe I'll learn something.  Thanks.

---

### Post by Iggy64 on 2012-12-07
So, I tried MenuLibre in LXDE and it works great.

Too bad it doesn't allow for creating new menu categories or renaming of categories.  I'm going to have to totally redo my menus.  But -- at least I'll have much more useful menus.

Alacarte was driving me crazy.  Some bits work, some don't (in my LXDE).

I took a brief look at manual editing of the menu files, but I'm a little intimidated by that right now.

---

### Post by Peripheral Visionary on 2012-12-08
[This]("http://forums.linuxmint.com/viewtopic.php?f=90&t=54945&start=0#p314893") is absolutely the best novice-friendly description of Linux desktops I've ever read, even though it's a little out of date.  It explains why KDE applications drag in all that KDE baggage, and same with Gnome/GTK.  Other than taking up space on your hard drive, simply *having those apps installed* will not slow down performance. It's *applications*, not so much the desktop environment, that chew up resources.

---

### Post by Iggy64 on 2012-12-08
Thanks a lot, PV.  That's just the kind of stuff this novice needs.  

Nice of you to take time to help!

---

### Post by Buntu Bunny on 2012-12-08
> **Peripheral Visionary said:**
> [This]("http://forums.linuxmint.com/viewtopic.php?f=90&t=54945&start=0#p314893") is absolutely the best novice-friendly description of Linux desktops I've ever read, even though it's a little out of date. 

I appreciate the link too. Thanks.

---

