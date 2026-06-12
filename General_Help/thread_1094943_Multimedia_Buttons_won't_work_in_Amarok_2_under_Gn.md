---
title: "Multimedia Buttons won't work in Amarok 2 under Gnome"
date: 2009-03-13
forum: General Help
---

### Post by jtreach on 2009-03-13
In Amarok 1.4 you could install a userscript to make multimedia buttons work in Gnome. Is there any way to do this for Amarok 2 in Gnome?

Thanks in advance.

---

### Post by andrewkk on 2009-03-15
It's strange that the Configure Shortcuts dialog does recognize the Media Play, etc. buttons but that they seem to have no effect when set as global shortcuts. Other keys like Meta+C do work as global shortcuts.

I even tried using CompizConfig to assign the command "amarok --play-pause" to the XF86AudioPlay button, but still nothing happened.

This makes me think that the problem may not be specific to Amarok or KDE applications, but rather probably has something to do with the way Gnome handles multimedia buttons.

Can you find the old Amarok 1.4 script to see how it worked?

---

### Post by jtreach on 2009-03-15
The original script is [here]("http://www.kde-apps.org/content/show.php/Gnome+Multimedia+Keys?content=60910").

There was also a comment from the writer of that script, doesn't sound good:

> Sorry for not keeping up to date with the comments here... as for Amarok 2 support I don't think it it's going to happen anytime soon - not from me anyway.

The scripting interface has changed completely and scripts are now required to be written in javascript so it would mean starting over a fresh in a language I've never used before.

Currently I don't even have Amarok 2 installed and my time is limited however I will try and investigate this sometime soon.

Cheers,

Chris

---

### Post by andrewkk on 2009-03-15
Well, it looks like all someone needs to do is throw together an [Amarok 2 script]("http://amarok.kde.org/wiki/Development/Scripting_HowTo_2.0") that:
[LIST]
[*]Connects [via DBUS]("http://doc.trolltech.com/4.4/qtdbus.html") to the [FONT="Courier New"]MediaPlayerKeyPressed[/FONT] signal in [FONT="Courier New"]org.gnome.SettingsDaemon.MediaKeys[/FONT], and
[*]Controls playback [via the Amarok script API]("http://amarok.kde.org/wiki/Development/Script_API#Amarok.Engine")
[/LIST]
For anyone familiar with JavaScript, API use, and DBUS this shouldn't take more than an hour.

I have far too limited experience with all of those to have the time to work this out right now. But this could be a great starter project for someone interested in add-on scripting for Amarok, Firefox, Songbird, or anything else with a JavaScript interface. It looks very doable.

---

### Post by jtreach on 2009-03-15
Shame anything like that scares the beejebus out of me.

Thanks for looking into it though. Nice to know it might happen in the near future!

---

### Post by BrowneR on 2009-04-25
Hi, I'm the creator of the Gnome Multimedia Keys script for Amarok 1.4.

I have created a new Amarok 2 version of my script.

It's in a pretty basic state at the moment but should hopefully do the trick for you guys.

[http://www.kde-apps.org/content/show.php?content=103448]("http://www.kde-apps.org/content/show.php?content=103448")

---

### Post by gocek on 2009-04-25
woho, wonderful! It actually works for me ;)

Thanks a lot, I'm damn sure many people have been waiting for this script!

---

### Post by jtreach on 2009-04-26
Thanks for fixing this problem. That's wicked!

I haven't tried it out yet but I have faith.

---

### Post by eladamri on 2010-05-05
I got mine working easily enough.

First I disabled the media keys in System > Preferences > Keyboard Shortcuts (click on each shortcut and press backspace to clear)

Second I configured each of the shortcuts in System > Preferences > CompizConfig Settings Manager > Commands (available in Ubuntu Software Center). I attached them to "Amarok --previous", "Amarok --next", "Amarok --play-pause" and "Amarok --stop".

It didn't work immediately, I had to restart my X server (log out and log back in).

---

### Post by Elfy on 2010-05-05
I just installed the Gnome Multimedia Keys 2 script.

Thread closed necromancy.

---

