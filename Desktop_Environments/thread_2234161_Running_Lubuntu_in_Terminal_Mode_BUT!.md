---
title: "Running Lubuntu in Terminal Mode BUT!"
date: 2014-07-12
forum: Desktop Environments
---

### Post by Sha'ir on 2014-07-12
Well I have got Lubuntu to run in terminal mode but I am unable to use software such as Chromium or anything graphically based which is of course a bit obvious. 
The issue is that it is actually more of a text mode than a terminal mode and I am left with a fairly useless computer. 

I want to find a way to boot Lubuntu into a terminal mode but keep things like Chromium and all my other stuff usable. I essentially just want to have as little hardware strain on my desktop as it is very old. It is just a computer I use to test stupid stuff on, a "lab bot" essentially. Is there a way to enable a terminal mode that can still have graphical capabilities? Or should I just install a different version of Linux altogether? I was thinking of Slackware

---

### Post by Bashing-om on 2014-07-12
Sha'ir;Hello,

I run a minimal install, booting to terminal. Now If it is my desire to activate a GUI application I can do so.
I have installed 'xorg', and for the DE (GUI) I have installed and run xfce4 . When I want a GUI ap I start the GUI manually.
IN my usecase the terminal command 'startx' will start the desktop for these GUI applications.
This arrangement is ideal for me and the manner I use my system. Your use case may be different. 

[INDENT][INDENT]my little bit
[INDENT][INDENT][INDENT]to try and help
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Sha'ir on 2014-07-13
This is exactly what I was desiring. essentially I do not want a desktop to be enabled just the terminal. If possible I would want to have it so that any graphical applications can run with minimum need of a GUI desktop.

---

### Post by Sha'ir on 2014-07-13
I should also add that I want a way in which I can always return back to the terminal without rebooting of course.

---

### Post by sudodus on 2014-07-13
I think what Bashing-om was describing can do what you need, but there are many different ways to implement it.

I agree that very old computers run well in text mode while there are problems with graphics. Please read these links
[URL="http://ubuntuforums.org/showthread.php?t=2130640"]
Old hardware brought back to life[/URL]
[https://wiki.ubuntu.com/Lubuntu/AdvancedMethods](https://wiki.ubuntu.com/Lubuntu/AdvancedMethods)

A lightweight windows manager is ***Fluxbox***, which can be installed from the OBI-9w installer. See this link

[https://help.ubuntu.com/community/9w#A9w_iso_files](https://help.ubuntu.com/community/9w#A9w_iso_files)
[RAM_&_disk_usage]("https://help.ubuntu.com/community/9w/RAM_%26_disk_usage") 

This iso file contains what you need for that purpose

[http://phillw.net/isos/linux-tools/9w/obi_Trusty-nonpae-txt5-9w.iso](http://phillw.net/isos/linux-tools/9w/obi_Trusty-nonpae-txt5-9w.iso)

If you install Fluxbox via the install menu, you still log in to the text screen. The command ```
sudo startx
``` will start Fluxbox. When you ***right-click on the background and select Exit***, you will leave Fluxbox and return to the text screen. And of course, you can install your favourite application programs, text programs as well as graphical programs, for example the light-weight web browser Midori.

By the way, do you know of the text screen web browser Lynx?

This software installs a system built on Ubuntu 14.04 LTS mini.iso. If you have problems to get the graphics to work, I suggest that you try starting from ***Ubuntu 12.04 LTS mini.iso*** or from ***Debian Wheezy***.

You may also try some ultra-light linux distros, that might do well in your old computer, for example

***DSL, Wary Puppy, Tiny Core***

---

