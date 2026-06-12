---
title: "control the number instances of a program in Unity"
date: 2014-02-22
forum: Desktop Environments
---

### Post by grashdur on 2014-02-22
I can open multiple instances of some programs, but not of others. I use the little Stopwatch program, and in Gnome I could open as many stopwatches as I wanted. But Unity only allows me to have one of them open at a time. 

For a year or so I've gotten around this by installing another timer called Zeegaree Lite, so then I can have two different timers open at once. But Zeegaree has become unreliable lately (it often stops itself before reaching zero), so I want to start having more than one Stopwatch again.

How do I change this setting?

---

### Post by kostkon on 2014-02-23
Have you already tried middle-clicking on its icon in the launcher? That is the way you typically start new instances/windows in unity, especially for those apps that don't provide such an option in their launcher menu (that appears when you right-click on their icon in the launcher.)

---

### Post by grashdur on 2014-02-23
Okay, just now tried middle-clicking on the icon in the launcher. And then tried it for other program icons. Nothing happened -- it seems the middle-click just gets ignored. I see that Chromium does offer the option of opening another window when I right-click it.

I've also tried pressing CTRL-N when the Stopwatch window is selected, and nothing happens.

---

### Post by mc4man on 2014-02-23
There is a bit of a limitation here as far as opening multiple instances from the unity launcher as it doesn't appear stopwatch has a separate command to open a new instance. (if it did then no problem at all.

So you could add a desktop action to stopwatch.desktop to open  new instances from a right click on the launcher & it would work fine however you'll get cursor spin for about 10 sec's or so (harmless but annoying

Another option would be to just go alt+F2 > stopwatch
after doing the above the command once it  will be in alt+F2's history so you'll just need to alt+F2 &  click on

A 3rd option would be to browse to /usr/share/applications, find Stopwatch, right click > copy, then back on your Desktop right click > paste

The last 2 ways will not produce cursor spin

If the cursor spin isn't an issue, to add an action add the blue to stopwatch.desktop - 

```
[Desktop Entry]
Version=1.0
Type=Application
Encoding=UTF-8
Name=Stopwatch
Comment=A virtual stopwatch
TryExec=/usr/bin/stopwatch
Exec=/usr/bin/stopwatch
Categories=Application;Utility
Icon=/usr/share/pixmaps/stopwatch.xpm
[COLOR="#0000CD"]Actions=Addwatch

[Desktop Action Addwatch]
Name=Open new
Exec=/usr/bin/stopwatch
TargetEnvironment=Unity[/COLOR]

```

If I find a way around cursor spin in the Desktop action will let you know
You can either edit stopwatch.desktop in /usr/share/applications with a root text editor (gksudo gedit or sudo nano) or copy to ~/.local/share/applications & edit as user (gedit

---

### Post by grashdur on 2014-02-23
> **mc4man said:**
> Another option would be to just go alt+F2 > stopwatch
after doing the above the command once it  will be in alt+F2's history so you'll just need to alt+F2 &  click on
...
You can either edit stopwatch.desktop in /usr/share/applications with a root text editor (gksudo gedit or sudo nano) or copy to ~/.local/share/applications & edit as user (gedit

Thank you, mc4man! The Alt-F2 option works great!

And thanks also for telling me where those desktop files are located -- that fact will be very useful to me in the future.

---

