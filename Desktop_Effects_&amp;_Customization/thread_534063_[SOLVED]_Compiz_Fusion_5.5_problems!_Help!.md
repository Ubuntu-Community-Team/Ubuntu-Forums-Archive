---
title: "[SOLVED] Compiz Fusion 5.5 problems! Help!"
date: 2007-08-24
forum: Desktop Effects &amp; Customization
---

### Post by runemaste644 on 2007-08-24
I recently updated Compiz Fusion from version 5.2 to 5.5 and i've been experiencing problems ever since. I even installed XGL and went to a Gnome with XGL session to run Compiz Fusion, and it still doesn't work but some of my problems happened less frequently, and when i set all beryl advanced options to XGL(when i was typing this!), i didnt experience anything but a partial lockup, though it gave me time to access the terminal window i was running CF in and hit Ctrl+C and type
> metacity --replace 
to run Metacity. And i cant access beryl manager's options very easily because my system tray disappeared! (but when i try to run beryl manager, it brings up the drop-down menu and lets me change 1 option) 

1. Frequently it cuts off part of my top panel and i have to move it to another side of the screen and back for it to reappear. Also, when this happens, it moves and resizes the active window. which annoys me a lot!!!](*,)

2. I kept beryl manager to switch window decorators (between Emerald, Compiz GTK decorator and Compiz KDE decorator) and whenever i switch over to Compiz GTK decorator it shifts my desktop over 1 inch to the right (revealing a wallpaper that Compiz Fusion tries to draw) and it really messes me up.](*,)

3. After all this, it locks up and i have to hold down the power button for 4 seconds to reboot and i cant even get to the tty1 terminal!](*,)](*,)](*,)](*,)](*,)](*,)

What is WRONG with Compiz???????????? Please help me! Thanks in advance.


*After all this, can i have you help me get my system tray back? I like having my system tray.*

---

### Post by runemaste644 on 2007-08-24
Umm... Anybody there? I really need help on this.
Sorry, this is my first thread I ever posted. But I would really appreciate help from the Ubuntu Forums Community.

---

### Post by josys36 on 2007-08-24
The system tray is an applet called Notification Area. You should be able to bring it back by just right clicking on your panel and then add that applet.

I have had quite a few compiz problems myself, so for now I am just sticking to Beryl. 

Jason

---

### Post by runemaste644 on 2007-08-24
well, i did that and it is back, but i only see beryl-manager. Oh well, after i reboot it will have the battery and network applets back. Thanks for the help! And beryl crashs every time i do that and i messed up my cube by editing the # of virtual desktops.

---

### Post by runemaste644 on 2007-08-25
Ok, there is an update today. Im gonna risk CF being rendered unusable, but the bugs might be gone. But, its still 5.5. but its the aug. 24 release of 5.5. Well, it won't break my system, so i wont have to worry about going to Winblows.
But there are 43 other updates anyway.

---

### Post by runemaste644 on 2007-08-25
ok, its done updating.
now lets see if the stuff is fixed.....
oops! when i do fusion-icon to launch, i get a white screen.
on
```

compiz --replace

```
my bottom panel disappears.
but i can easily put my window list, trashcan and show desktop button on the top panel.(for now)
and it also did a partial lockup so bye bye compiz (for now)

---

### Post by Diabolis on 2007-08-25
I had problems with compiz this week too. My only bug was that if I pressed alt+tab to go through my windows, compiz craashed. This morning I did the upgrade and everything is working fine again.

---

### Post by runemaste644 on 2007-08-25
> **Diabolis said:**
> I had problems with compiz this week too. My only bug was that if I pressed alt+tab to go through my windows, compiz craashed. This morning I did the upgrade and everything is working fine again.

Hmm... todays upgrade... Ill try that again. Which were you using, Gnome, KDE, Gnome+XGL or another WM? I use Gnome with XGL and all beryl settings set to XGL

Well, i had no luck now either. It stil freezes this browser window and hardly lets me get to the terminal to run Metacity.:( BTW, if this helps, I use Opera for the browser.

Sys specs are (you might be jealous of my hardware)
Lenovo 3000 N100 model
nVidia GeForce Go 7300 for my video card
1 GB of RAM
1680x1050 resolution
intel Core 2 duo processor (i686)

I'll try reinstalling Compiz Fusion completely and see if that does anything which it did not.

---

### Post by runemaste644 on 2007-08-25
Ok, this is weird. I tried to run Beryl and i got Compiz Fusion instead. My browser is working fine.(oh, wait duh. i had crash handler in beryl set to run Compiz Fusion:???:
But everything is running just fine now in Gnome with XGL. But we cant mark it as solved yet, because i have to investigate a bit more.:) But i did do a re install of all compiz packages, so that could be it.
The browser occasionally locks up, but its no big deal.:)

---

### Post by runemaste644 on 2007-08-25
Ok, so we have this partially solved. My panels don't disappear (except the bottom one does occasionally:P), Opera has a few less problems, but my desktop moves over about a foot now. Maybe altering Beryl's advanced options would fix some stuff but probably not the desktop. The desktop is the biggest problem, however. I will try stuff in different sessions like KDE, for example. Plus, I added a poll about the shifty desktop.

---

### Post by runemaste644 on 2007-08-25
I read a thread and somebody said if it is acting weird after an update, go to Preferences>Reset to defaults and it will work. IT DID WORK!!!:guitar:\\:D/=D>
Yaaaaaaaaaaaaaaaaaaaaaaaaaaaay!!!
That is the solution!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

---

