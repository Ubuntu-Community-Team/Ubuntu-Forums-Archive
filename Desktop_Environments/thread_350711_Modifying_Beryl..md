---
title: "Modifying Beryl."
date: 2007-01-31
forum: Desktop Environments
---

### Post by Roasted on 2007-01-31
Just a question, and maybe a simple one so I figured I'd post it here. I just got Beryl installed without any issues. It's great, I love it. But I wonder, can I alter the settings at all? Can I change the theme colors or change the speed at which these windows wobble? And flipping to a different side of the cube, how can I slow that down? It's almost instant for me and I want to take a screenshot for a friend.

---

### Post by ButteBlues on 2007-01-31
> **Roasted said:**
> Just a question, and maybe a simple one so I figured I'd post it here. I just got Beryl installed without any issues. It's great, I love it. But I wonder, can I alter the settings at all? Can I change the theme colors or change the speed at which these windows wobble? And flipping to a different side of the cube, how can I slow that down? It's almost instant for me and I want to take a screenshot for a friend.
You see that red icon in your panel that looks like a diamond? Right click it.

---

### Post by NewOldTimer on 2007-01-31
try beryl-manager also see [http://www.ubuntuforums.org/showthread.php?t=349732](http://www.ubuntuforums.org/showthread.php?t=349732)

---

### Post by Roasted on 2007-02-01
Is there anyway I can set an icon to launch beryl? Like put it under applications or in the bar at the top for a quick launch?

---

### Post by Roasted on 2007-02-01
Also, when I move the windows around they blur pretty badly for a few seconds. Is there anyway to turn that off or slow it down? I find it gives me a headache cause by nature I try to focus my eyes whenever I move a window. I'm looking in the menu but there's so much that I'm tinkering with, I'm not seeing anything that helps, so if someone can directly guide me to the setting I'd appreciate it. Thanks.

---

### Post by xpod on 2007-02-01
Like the guy`s said the best thing you can do is get stuck into the beryl settings.

The cube can be slowed down by clicking on "rotate cube>misc options" then adjusting the speed  and the zoom is in the behaviour  tab.

Visual effects to turn off the blur if it need be and the animations tab will give you access to many of the fancy visuals.

It`s just a case of trial & error till you have things the way you like them.
Good luck

---

### Post by mahiyar on 2007-02-01
It seems that you do not have access to the red ruby thing at start up. To do that go to >systems>sessions>start up tab. There add the lines 1)beryl-manager and you will get the beryl in the task bar at start up.

---

### Post by Waappu on 2007-02-01
> **Roasted said:**
> Is there anyway I can set an icon to launch beryl? Like put it under applications or in the bar at the top for a quick launch?

Hi

This is one way:

Type in terminal
```
gksudo gedit /usr/share/applications/Start-Beryl.desktop
```
and paste these lines to file and save it
```
[Desktop Entry]
Name=Start Beryl
Comment=Starts Beryl manager
Exec=beryl-manager
Icon=beryl-manager
Terminal=false
Type=Application
Categories=GNOME;Application;Utility;
```

Now you can found "Start Beryl" from menu applications->accessories.
If you right click that you can select "add this launcher to panel" and you have also same icon in upper panel.

I hope this is something you looking and helps you

---

### Post by Brunellus on 2007-02-01
thread moved out of Absolute Beginners.  [Beryl is off-topic in the Beginners forum](http://www.ubuntuforums.org/showthread.php?t=349732)

---

