---
title: "Getting rid of gnome for KDE"
date: 2007-10-30
forum: Desktop Environments
---

### Post by NoSmokingBandit on 2007-10-30
I want to switch over to KDE sometime so i can use kde 4 when its released which looks just plain awesome, but im sure ill be sticking with it so i want to get rid of gnome completely as to not bog down my system. I know theres a thread on that somewhere but it is from 2005 so i dont want to kill my gusty install by running something that was meant to Dapper or something.
So how does one get rid of gnome (i can handle installing KDE myself) ?

Also, would this affect any of my programs? Like, will exaile still work or will i have no choice but to use amarok?

---

### Post by taurus on 2007-10-30
[http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde)

---

### Post by aysiu on 2007-10-30
I updated it for Gutsy, but it doesn't account for KDE 4.

---

### Post by Happy_Man on 2007-10-30
Exaile will still work, but it would have to load GNOME libs and as such would defeat your purpose of running pure KDE. Besides, Amarok is WAY better.

---

### Post by aysiu on 2007-10-30
Even if Exaile gets accidentally removed, you can always reinstall it. All your settings should be intact.

---

### Post by NoSmokingBandit on 2007-10-30
I'll be switching pre-KDE4 so i can upgrade and it should handle it fine.
I only use exaile because i didnt want a bunch of random kde packages just to play music.
I'll probably make the switch tomorrow. Hopefully it will go smooth.

---

### Post by Happy_Man on 2007-10-30
Actually, the packages that let Amarok play music are included in the kubuntu-desktop package.

---

### Post by NoSmokingBandit on 2007-10-30
once im in kde i wont care about having random kde packages around anymore though, i just didnt want any kde in my gnome and later ill try to get rid of all gnome packages so it will be strictly kde

---

### Post by NoSmokingBandit on 2007-10-31
Alright, i made the switch. Couple of things i need to get squared away before im happy.
1 How do you get the mounted volumes to appear on the desktop like gnome does. In gnome you just run gconf-editor and tweak nautilus, but i dont know how to tweak dolphin to do that. Its nice having usb drives right on the desktop.
2 Is there a way to change it so files/folders dont open on a single click? I looked in system settings but i couldnt find anything.
3 What is the Home icon name? I put a desktop entry on for my home folder but i dont know what the icons name is so right now its a blank document that links home.
Thanks!

Edit:
Another thing to add to the list:
Amarok refuses to work. It never worked in gnome so i installed exaile. The problem is that exaile freezes on me in kde and i cant get rid of it until i reboot. I installed Amarok, Amarok-xine, and Amarok-engines packages in synaptic but got no sound at all. My soundcard is a SB Live! card.

---

### Post by GeneralZod on 2007-11-01
> **NoSmokingBandit said:**
> Alright, i made the switch. Couple of things i need to get squared away before im happy.
1 How do you get the mounted volumes to appear on the desktop like gnome does. In gnome you just run gconf-editor and tweak nautilus, but i dont know how to tweak dolphin to do that. Its nice having usb drives right on the desktop.


KDE does not use a file manager to render the desktop (they do share a lot of  code, though).  Right-click on desktop -> Configure Desktop -> Behaviour -> Device Icons -> Knock yourself out ;)


> 2 Is there a way to change it so files/folders dont open on a single click? I looked in system settings but i couldnt find anything.


Open SystemSettings, Keyboard and Mouse -> Mouse -> General -> Double-click to open etc.

> 
3 What is the Home icon name? I put a desktop entry on for my home folder but i dont know what the icons name is so right now its a blank document that links home.
Thanks!


Right-click on desktop -> Create New -> Link to Location URL -> Enter 

```

home:/

```

as the URL.  The name isn't important, IIRC.  The icon will be filled in automatically.

---

### Post by NoSmokingBandit on 2007-11-01
thanks for the help, but im going to be going back to gnome. I turned my computer on this morning and the resolution is stuck at 640x480. I disabled/enabled the restricted driver and its still stuck. I really dont like kde but i figured it was worth a shot.

---

