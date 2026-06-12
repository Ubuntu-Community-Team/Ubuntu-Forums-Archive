---
title: "Start a program at login in workspace #2"
date: 2012-04-25
forum: Desktop Environments
---

### Post by Ehknaton on 2012-04-25
Hi, I've set TeamViewer 7 to load at startup (on Ubuntu 10.04) , but I want it to appear on workspace #2. I think this can be accomplished using compiz, as described in this thread [http://ubuntuforums.org/showthread.php?p=11870915](http://ubuntuforums.org/showthread.php?p=11870915)

I've done these settings, but it doesn't work. How can I do it?

[[IMG]http://img6.imageshack.us/img6/8001/teamviewerstartup.png[/IMG]]("http://imageshack.us/photo/my-images/6/teamviewerstartup.png/")

---

### Post by stinkeye on 2012-04-25
Use the windows with fixed position section.
My resolution is 1680x1050.

I use 4 horizontal and 1 vertical desktop in compiz.
Compiz now sees my screen as 6720x1050
ie **4 times 1680** horizontal and **1 times 1050** vertical.

So if I use 1750x100 as a fixed placement for gpodder it will open
in the second desktop 70 in from the left edge and 100 from the top.

Untick the **keep in work area**.


You can use wmctrl to give you the top left coordinates of each desktop.
Install wmctrl...
```
sudo apt-get install wmctrl
```
This command will give the coordinates of each desktop.
```
wmctrl -d | awk '{print $6}'
```

eg I ran the command in each desktop
```
glen@Precise:~$ wmctrl -d | awk '{print $6}'
[COLOR="Red"]0,0[/COLOR]
glen@Precise:~$ wmctrl -d | awk '{print $6}'
[COLOR="red"]1680,0[/COLOR]
glen@Precise:~$ wmctrl -d | awk '{print $6}'
[COLOR="red"]3360,0[/COLOR]
glen@Precise:~$ wmctrl -d | awk '{print $6}'
[COLOR="red"]5040,0[/COLOR]
```

---

### Post by Ehknaton on 2012-04-25
Thanks for your tips, I tried some values but,
I don't know what should I write in "class=", I tried "Grab" and then clicked on the window, but it didn't work.
Can you provide a step by step guide please ?

---

### Post by stinkeye on 2012-04-25
Use what you had before.
```
title=TeamViewer
```
Various grab options in the dropdown.

Actually I was just playing around and the fixed viewport you first tried works for me using gedit as the placed window.

Try again the way you first attempted but try grabbing as **window title** or **window name**

---

### Post by Ehknaton on 2012-04-25
Yes, I tried it like this, because TeamViewer7 has two windows, one using *title* and the other using *name*, but neither one works. When I start the program it still appears in the current workspace #1.

---

### Post by stinkeye on 2012-04-26
Works here in 12.04 using
```
name=TeamViewer.exe
```

Are you sure your using compiz as the window manager?
```
echo $DESKTOP_SESSION
wmctrl -m
```

eg my output
```
glen@Precise:~$ echo $DESKTOP_SESSION
**ubuntu**

glen@Precise:~$ wmctrl -m
Name: **Compiz**
Class: N/A
PID: N/A
Window manager's "showing the desktop" mode: OFF
```

---

### Post by Ehknaton on 2012-04-27
These are my results:

```
echo $DESKTOP_SESSION
gnome

```

and
```

wmctrl -m
Name: Metacity
Class: N/A
PID: N/A
Window manager's "showing the desktop" mode: N/A

```

How can I make compiz my window manager ?

---

### Post by stinkeye on 2012-04-27
What session choices do you have at the login screen?
See [**_[COLOR="DarkRed"]HERE[/COLOR]_**]("https://help.ubuntu.com/community/CompositeManager")

Instead of installing compiz you could use gdevilspie with metacity.
```
sudo apt-get install gdevilspie
```

Then set it up as in pics.

---

### Post by Ehknaton on 2012-04-27
Good suggestion with devilspie, looks good and it seems easy to use.

I installed devilspie using Ubuntu Software Center, and the gui for it, downloaded it from a website(apt-get could not find the package) and it works. As soon as I hit the start button my windows move to the second workspace. 

I can add it to Startup Applications, but it won't start the deamon with the application. I'll still have to manually click "Start" each time to start the deamon.
Problem is my program looks like this:

---

### Post by stinkeye on 2012-04-27
> **Ehknaton said:**
> Good suggestion with devilspie, looks good and it seems easy to use.

I installed devilspie using Ubuntu Software Center, and the gui for it, downloaded it from a website(apt-get could not find the package) and it works. As soon as I hit the start button my windows move to the second workspace. 

I can add it to Startup Applications, but it won't start the deamon with the application. I'll still have to manually click "Start" each time to start the deamon.
Problem is my program looks like this:
Just add
```
devilspie
```
to startup applications.No need to autostart gdevilspie.
Pretty sure gdevilspie just creates a config for devilspie to use in ~/.devilspie

---

### Post by Ehknaton on 2012-04-27
Indeed, your advice worked just fine. Now it does what I wanted. Perfect, my issue is resolved.

---

