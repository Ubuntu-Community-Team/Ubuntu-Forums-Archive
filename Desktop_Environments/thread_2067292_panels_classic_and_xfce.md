---
title: "panels classic and xfce"
date: 2012-10-06
forum: Desktop Environments
---

### Post by cmcanulty on 2012-10-06
I have been trying to get only gnome-panel to start in gnome classic, and only xfce4-panel to start in xubuntu and xfce4, but it seems if I autostart gnome-panel in classic it starts also in xubuntu and xfce4 even though I have set the autostarts different for them. Is there a way to avoid this, I have been messing with it all day to no success.In xubuntu or xfce4 the gnome panel is behind the xfce4 panel. I can drag them and see the other panel below.

---

### Post by Frogs Hair on 2012-10-06
I am seeing the proper panels for each environment and do not have the panels set to auto start. Though I use Nautilus as default in XFCE The option to start Gnome services is not enabled. 

Does the Gnome or XFCE panel fail to start if they are not set to auto start ? I am running 12.10 with XFCE 4.10.

---

### Post by cmcanulty on 2012-10-06
OK I disabled gnome services in session and startup but the gnome panels are still behind the xfce panels I tried logout and a reboot no change.

---

### Post by cmcanulty on 2012-10-06
OK I disabled gnome services in session and startup but the gnome panels are still behing the xfce4 panels even after trying logout and reboot. 


More info, I can get rid of gnome panels by disabling it in session and startup but then it won't start in gnome classic. There should be a way to separate the startup apps for each desktop.

---

### Post by Frogs Hair on 2012-10-06
The panels in Classic should start without having to add them to the the start up applications.I do remember having the same occasional problem in 11.10.(no panel) This makes me think the problem was related to the 11.10 fallback session. 


I never followed up because fallback was installed as a result of installing the Gnome Shell and was almost never used.

I just started using XFCE in 12.04 and now have the newest version in 12.10. Are you running XFCE 4.8 or 4.10 ?

---

### Post by cmcanulty on 2012-10-06
I am running 4.10 and if I delete gnome-panel from startup I get an empty desktop in classic. I was hoping there was a conditional command so if gnome-classic no effects then startup gnome-panel, if xfce4 or xubuntu startup xfce4-panel. But I have no idea how to do that if it is even possible.

---

### Post by Frogs Hair on 2012-10-06
If you are using 11.10 as your information states see this post. I don't find a PPA package for 11.10 and am guessing 4.10 now in the 11.10 repository.   

[http://ubuntuforums.org/showthread.php?t=1968553](http://ubuntuforums.org/showthread.php?t=1968553)

---

### Post by cmcanulty on 2012-10-06
I am using 12.04

---

### Post by LewisTM on 2012-10-06
There is a hidden way to control in which DE your autostart entries are enabled.
Navigate to ~/.config/autostart and find you gnome-panel entry, it should be a .desktop file modified recently.
Open it inside a text editor and add this line:
> OnlyShowIn=GNOME;

Cheers!

---

### Post by Frogs Hair on 2012-10-06
> **LewisTM said:**
> There is a hidden way to control in which DE your autostart entries are enabled.
Navigate to ~/.config/autostart and find you gnome-panel entry, it should be a .desktop file modified recently.
Open it inside a text editor and add this line:


Cheers!

Looks like a nice solution ! I'm wondering why the panels would need to be set to auto to begin with.

---

### Post by cmcanulty on 2012-10-07
Ok there are a bunch of panel files in there probably because I tried so many fixes lately. I am attaching a screenshot of the folder items and the error I get when I try to open one to modify. Which file should I modify and how do I open it. Thank you

---

### Post by LewisTM on 2012-10-07
I didn't tell you to launch it, I told you to open it inside a text editor, like gedit.

---

### Post by cmcanulty on 2012-10-07
That's what I tried to do and why I posted the error screenshot I get when I try to open it.

---

### Post by cmcanulty on 2012-10-07
OK I used thunar to pick gedit to open it-that option is gone from nautilus and added it as you said, no change I still get the gnome panels. If this helps, when I restart the xfce panels flash up for a second then they are replaced by the gnome panels.I can kill the gnome-panel in system monitor but it instantly reappears.

---

### Post by LewisTM on 2012-10-08
I don't have GNOME Classic or gnome-panel installed so I cannot fully test this. However, I created a dummy startup application in Xfce. It appended 
[FONT="Courier New"]OnlyShowIn=XFCE;[/FONT]
to the desktop file contents which makes sense, and it does launch. If I change =XFCE to =GNOME, it no longer launches at login. So the trick does work.

Did you keep only one gnome-panel autostart .desktop file?
In any case, you can disable it temporarily if you just want to test out Xfce. In GNOME, just execute gnome-panel to get it back. Once you have made up your mind, clean up everything.
:guitar:

---

### Post by cmcanulty on 2012-10-08
OK I added that to the .config/autostart/gnome-panel.desktop. How do I create a dummy startup application in xfce? Thank you.No change I still get gnome panels in front of xfce panels but I haven't done the dummy startup app until I find out how to do it.And still as xfce opoens I see the xfce panels then they are immediately covered by the gnome panels.

---

### Post by LewisTM on 2012-10-08
The dummy entry was for me, for testing the OnlyShowIn method. If you want to test drive Xfce either disable all gnome-panel entries or find how it gets autostarted and edit the .desktop file accordingly. This should be straightforward, I can provide no more help.

---

