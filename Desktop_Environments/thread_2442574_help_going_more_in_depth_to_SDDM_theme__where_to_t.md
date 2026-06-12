---
title: "help going more in depth to SDDM theme : where to turn?"
date: 2020-05-05
forum: Desktop Environments
---

### Post by anotherChris on 2020-05-05
I think the new Lubuntu SDDM theme that comes with Lubuntu 20.04 is really bad.  In fact, almost all the SDDM themes are bad.  So, I wanted to make my own SDDM theme, but it is proving more challenging than I thought.

At first, I thought I would simply copy, modify, and replace the Lubuntu theme's **Main.qml** file, but I can't.  

I have been able to make *some* modifications.  The following is a screen capture after running 
```
sddm-greeter --test-mode --theme /home/myaccount/Documents/mysddmthemes/mythemename
```
[https://ubuntuforums.org/attachment.php?attachmentid=285749&d=1588650953](https://ubuntuforums.org/attachment.php?attachmentid=285749&d=1588650953)

As you can see, I've got three accounts on my computer, and I've been able to remove a lot of things like the username and user icon.  However, what I did to achieve this is very ugly code, and I think it is also likely to prove non-functional if actually installed.  Also, I would like to add functionality like changing focus to different user account login boxes by scrolling through them with the Tab key rather than just hovering with mouse.  But to fix all that, I need to do more than just modify the **Main.qml** file.  And that is where I am having problems because I can't figure out things like *Where is "SDDMComponents2.0" being imported from?*  and  *Where is PictureBox.qml located?*  (I used "locate" from command line, but can't find) and  *How can I make sure my code is not jeopardizing the security of SDDM log in?*

I tried going to the [QML sub-forum on the Qt website]("https://forum.qt.io/category/12/qml-and-qt-quick"), but I think they are mostly operating at a level to far above me to be interested in my questions.

What is a good place to turn for more in-depth help with QML for a beginner?

---

### Post by wildmanne39 on 2020-05-05
Please use the attachment facility by clicking on the paperclip or  use url's for images because apart from bandwidth issues for some, it makes it difficult for those using mobile devices to browse the forum.

---

### Post by GhX6GZMB on 2020-05-05
It's an exceptionally bad idea to modify the QML files. SDDM has lots of (text) configuration possibilities. What exactly do you want to change? SDDM normally only takes care of the startup/login screen.

---

### Post by anotherChris on 2020-05-05
> **ml9104 said:**
> SDDM has lots of (text) configuration possibilities. 

Really?  Can you explain more, because it doesn't seem very configurable to me.  According to the [Lubuntu manual]("https://manual.lubuntu.me/stable/3/3.1/3.1.9/sddm_configuration.html"), you can change the auto-log-in feature, the background, or choose one of the themes from Muon, but all those themes look the same.

I might use something else, like  [Simplicity theme]("https://github.com/gabretana/simplicity-sddm-theme") or [Aerial theme]("https://awesomeopensource.com/project/3ximus/aerial-sddm-theme"), but I don't know enough to know whether those will be compatible with Lubuntu or whether they are safe.  I feel it is safer to do my own by modifying Lubuntu theme.  

> **ml9104 said:**
> What exactly do you want to change? SDDM normally only takes care of the startup/login screen.

Yes, I want to change the startup/login screen.  I hate the one that comes with 20.04, and the other themes in Muon basically look the same.  As I mentioned above, I have succeeded in removing the icon and rectangular white box from the startup/login screen, as shown in the following screen capture:
[https://ubuntuforums.org/attachment.php?attachmentid=285749&d=1588650953](https://ubuntuforums.org/attachment.php?attachmentid=285749&d=1588650953)

However, I don't know if that will be functional, and I would like to go farther in modification.  I guess my next step, this morning, is replacing "PictureBox" object with the code in PictureBox.qml from Github, but I'm not sure if that file in Github is the thing on my computer because I can't find the SDDMcomponents2.0 that the Lubuntu theme's Main.qml is importing...

---

### Post by CatKiller on 2020-05-05
> **anotherChris said:**
> Yes, I want to change the startup/login screen.  I hate the one that comes with 20.04, and the other themes in Muon basically look the same. 

[It's not like there's a shortage.](https://store.kde.org/browse/cat/101/order/latest/) Even if you don't find **the ultimate SDDM theme** there you can see what other people have done, and how, to guide your tinkering.

---

### Post by anotherChris on 2020-05-05
> **CatKiller said:**
> [It's not like there's a shortage.]("https://store.kde.org/browse/cat/101/order/latest/") Even if you don't find **the ultimate SDDM theme** there you can see what other people have done, and how, to guide your tinkering.

Okay, but KDE is for Plasma, and I'm using LXQt.  I assume that those KDE store themes won't work in Lubuntu, right?

I have looked at what other people have posted on GitHub for SDDM themes.  Using the Main.qml from "Lubuntu SDDM theme" as a template, I have modified it and been successful as described in previous posts upthread.  But I don't know what resources to turn to for advice.

---

### Post by deadflowr on 2020-05-06
> Okay, but KDE is for Plasma, and I'm using LXQt. I assume that those KDE store themes won't work in Lubuntu, right?
No.
sddm, as with most (if not all) display managers, is rather desktop session agnostic.
The login screen runs before the desktop loads.

---

### Post by GhX6GZMB on 2020-05-06
> [COLOR=#000000]Really? Can you explain more, because it doesn't seem very configurable to me. According to the [/COLOR][Lubuntu manual]("https://manual.lubuntu.me/stable/3/3.1/3.1.9/sddm_configuration.html")[COLOR=#000000], you can change the auto-log-in feature, the background, or choose one of the themes from Muon, but all those themes look the same.[/COLOR]

Sure. Let's take the background first. This is defined in /usr/share/sddm/themes/wall.png ... except it's not! wall.png just contains a symbolic link. The real background picture is stored in /usr/share/lubuntu/wallpapers/lubuntu-default-wallpaper.png ... except it's not! This .png file is also a symbolic link that per default points to 2004-lubuntu-wire-humming.png in the same directory. You'll need to copy your favorite wallpaper graphic into this directory and change the lubuntu-default-wallpaper.png symbolic link to point to your graphic. This means deleting the symbolic link and creating a new one with the same name. Be careful with ownership and permissions, use the same as the previous files.
Fixed.

For the rest of the SDDM screen, starting top left:
The drop-down menu for choosing environment is modified by editing:
/usr/share/xsessions/LXQt Desktop and /usr/share/xsessions/Openbox to contain the line NoDisplay=true
The drop-down menu for keyboard: I've no solution at this point (it's a known bug in SDDM)
The icons for Suspend, Reboot and Shutdown can be changed in /usr/share/sddm/themes/lubuntu by substituting equivalent .png files.
The login avatars can also be changed. For the Main User (as defined during installation) the avatar is a 256x256 .png stored in /usr/share/sddm/faces and has the name .face.icon 
For all other users it's stored in $HOME, also with file name .face.icon

Hope this helps. Again, changing the .qml files is NOT a good idea, the side effects can be devastating.

Cheers.

---

### Post by anotherChris on 2020-05-06
> **deadflowr said:**
> No.
sddm, as with most (if not all) display managers, is rather desktop session agnostic.
The login screen runs before the desktop loads.

That makes sense, but then why does the Muon Package Manager (which is [how the Lubuntu manual recommends getting new themes]("https://manual.lubuntu.me/stable/3/3.1/3.1.9/sddm_configuration.html")) show only a handful of alternate themes?  (I guess I should really ask that question at the Lubuntu.me forum!)

---

### Post by anotherChris on 2020-05-06
> **ml9104 said:**
> Sure. Let's take the background first. This is defined in /usr/share/sddm/themes/wall.png ... except it's not! wall.png just contains a symbolic link. The real background picture is stored in /usr/share/lubuntu/wallpapers/lubuntu-default-wallpaper.png ... except it's not! This .png file is also a symbolic link that per default points to 2004-lubuntu-wire-humming.png in the same directory. You'll need to copy your favorite wallpaper graphic into this directory and change the lubuntu-default-wallpaper.png symbolic link to point to your graphic. This means deleting the symbolic link and creating a new one with the same name. Be careful with ownership and permissions, use the same as the previous files.


I understand this method, but this is not how the Lubuntu manual suggests changing the background.  It suggests modifying the theme.conf file.

> **ml9104 said:**
> For the rest of the SDDM screen, starting top left:
The drop-down menu for choosing environment is modified by editing:
/usr/share/xsessions/LXQt Desktop and /usr/share/xsessions/Openbox to contain the line NoDisplay=true
The drop-down menu for keyboard: I've no solution at this point (it's a known bug in SDDM)
The icons for Suspend, Reboot and Shutdown can be changed in /usr/share/sddm/themes/lubuntu by substituting equivalent .png files.
The login avatars can also be changed. For the Main User (as defined during installation) the avatar is a 256x256 .png stored in /usr/share/sddm/faces and has the name .face.icon 
For all other users it's stored in $HOME, also with file name .face.icon

I didn't know about xsessions, but if you look at the image I posted to Ubuntu forums of screen capture of my in-progress SDDM theme (linked above), you can see I already removed all these things.  Not very difficult.

> **ml9104 said:**
> Hope this helps. Again, changing the .qml files is NOT a good idea, the side effects can be devastating.

But installing new SDDM themes from Muon or from the KDE store (see comment above from deadflower) is the same as changing the .qml files.  If Main.qml contains the elements necessary for logging in, there should be no problem.  That's why I asked the original question--because I want someone to look at the code before I try it.

---

### Post by CatKiller on 2020-05-06
> **anotherChris said:**
> That makes sense, but then why does the Muon Package Manager (which is [how the Lubuntu manual recommends getting new themes]("https://manual.lubuntu.me/stable/3/3.1/3.1.9/sddm_configuration.html")) show only a handful of alternate themes?  (I guess I should really ask that question at the Lubuntu.me forum!)
With no disrespect intended towards the Lubuntu project, Kubuntu would likely have more pull for getting SDDM themes into the standard repositories than Lubuntu - since they're bigger and have been using SDDM for longer - and pulling new bling from the KDE store is built into KDE's standard settings so they have less incentive to bother than they would otherwise. Not having that infrastructure so that you have to fiddle with things by hand is the "bloat-avoidance" that people are choosing by going with something like Lubuntu. 

I can't speak for ml9104, but *some* caution is warranted when fiddling with a display manager, since it's possible to render yourself unable to log in with careless fiddling. So things like working with a different theme rather than potentially breaking the *only* theme (and knowing how to change theme from the command line), trying to avoid breaking Qt, testing in a VM, making backups of files you change so you can easily restore them from the command line if your changes break things, and so on, are entirely sensible precautions. Where I might differ, though, is that it's your computer: should you break things beyond your ability to fix them, a reinstall takes about 20 minutes, and you'll have learned not to do whatever it was that you did. It's entirely possible that ml9104 learned a lesson about those files by exactly that method, hence their note of caution: there are definitely things *I* tried in the beginning (although I've never tried playing with SDDM themes) where the salient lesson was exactly "yeah, don't do that."

I would definitely start with examining how other themes work, though, so you can get a feel for the structure without having to give your own machine such a hard poke.

---

### Post by GhX6GZMB on 2020-05-07
> [COLOR=#000000]should you break things beyond your ability to fix them, a reinstall takes about 20 minutes, and you'll have learned not to do whatever it was that you did. It's entirely possible that ml9104 learned a lesson about those files by exactly that method, hence their note of caution: there are definitely things [/COLOR][I]I tried in the beginning (although I've never tried playing with SDDM themes) where the salient lesson was exactly "yeah, don't do that."
[/I]

Spoken from my heart :)
Yes, that's exactly where I was...

Nowadays I look for the configuration files (not an easy job) instead of fiddling with the .qmls
To me, .qmls are program files just like binary executables. A wrong period or comma will get you back to the install DVD quickly.

---

### Post by anotherChris on 2020-05-11
> **CatKiller said:**
> *some* caution is warranted when fiddling with a display manager, since it's possible to render yourself unable to log in with careless fiddling. So things like working with a different theme rather than potentially breaking the *only* theme (and knowing how to change theme from the command line), trying to avoid breaking Qt, testing in a VM, making backups of files you change so you can easily restore them from the command line if your changes break things, and so on, are entirely sensible precautions.

Yes, I understand what you're saying, and I have been doing that--looking at how other themes work, etc, and I'll try it in a VM machine first, although I'll have to "learn" VMs in order to that (never used one before).  I'm trying to do something crazy like a theme with video or animations.  Actually, what I am trying for is something even more pared down than the pre-installed Lubuntu theme.  The only problem I'm having is that some visual elements in the Lubuntu theme QML objects seem not to be configurable except by modifying the QML objects imported from the .qml files.

Anyway, my original question was about where to go to get help with QML besides the Qt forums, but maybe there isn't a good place...

---

### Post by CatKiller on 2020-05-11
> **anotherChris said:**
> Anyway, my original question was about where to go to get help with QML besides the Qt forums, but maybe there isn't a good place...

There may well not be. There's not just one place that you'd be able to teach yourself JavaScript or C++ on the fly, either. Qt has some [reference material](https://doc.qt.io/qt-5/qmlapplications.html) to get you started.

---

### Post by anotherChris on 2020-05-12
This question was answered on the Lubuntu.me Discourse: there is an SDDM developer community centered around Github.
[https://discourse.lubuntu.me/t/creating-sddm-themes-for-lubuntu-20-04-feasibility-and-assistance/1126/6](https://discourse.lubuntu.me/t/creating-sddm-themes-for-lubuntu-20-04-feasibility-and-assistance/1126/6)

Marking as solved...

---

### Post by CatKiller on 2020-05-12
Awesome! Glad to hear that you found some resources. Have fun!

---

