---
title: "XFCE is broken after a right-click..."
date: 2005-09-24
forum: Desktop Environments
---

### Post by YourSurrogateGod on 2005-09-24
Ok, here's the problem. I was using XFCE yesterday and I right-clicked on an item in one of my folders (to either delete or change the name of a file.) Now, after I clicked the option that I wanted, the right-click menu continued to be displayed (which it shouldn't have been.) I tried to close the folder, but that didn't work too. I tried to restart my pc, but no go (I click on the little power button in my panel (I tried the power button on the right-click menu as well, but that didn't work either), but no log-off screen is shown.)

So I figured the heck with it and rebooted my machine by hitting the power button on my box. Well, that was a bad idea... The next time that I logged into my XFCE, the only thing that I saw was the top bar/panel and that's it. No wallpaper, no lower bar, nothing! The right-click on the screen didn't work. I mean honestly, it's effectively useless.

I tried to simply reinstall xfce (thinking that whatever problem there was, it would be overwritten), but this didn't work out either, same results :( . I don't want to get rid of and reinstall xfce since I don't want to lose my settings (although I admit this is looking more and more like the option that I ought to use.) Do you have any ideas on how I could possibly fix this problem?

---

### Post by Xian on 2005-09-24
The first thing I would do is a little troubleshooting, and in this regard the obvious place to start would seem to be discerning whether or not this is a user prefs issue. If this is the case then your options become much clearer.

Open your /home/~ directory and rename the .xfce4 folder.
Then start up an xfce session.

Is a functional desktop available?

---

### Post by YourSurrogateGod on 2005-09-24
[QUOTE=Xian]The first thing I would do is a little troubleshooting, and in this regard the obvious place to start would seem to be discerning whether or not this is a user prefs issue. If this is the case then your options become much clearer.

Open your /home/~ directory and rename the .xfce4 folder.
Then start up an xfce session.

Is a functional desktop available?[/QUOTE]
The /home/~ directory? I tried to get there, but I got an error message saying that that directory does not exist.

---

### Post by Xian on 2005-09-24
[QUOTE=YourSurrogateGod]The /home/~ directory? I tried to get there, but I got an error message saying that that directory does not exist.[/QUOTE]
That's just forum shorthand. You need to fill in your user name.
For example:

/home/xian

---

### Post by YourSurrogateGod on 2005-09-24
[QUOTE=Xian]That's just forum shorthand. You need to fill in your user name.
For example:

/home/xian[/QUOTE]
Umm... I don't have a /home/name/.xfce4 directory. I typed in "ls -la" and it wasn't there.

---

### Post by Xian on 2005-09-24
Okay, do me a favor. Please post the output of the following:

```
$ ls /home
$ ls -a /home/name
```

---

### Post by foxy123 on 2005-09-24
[QUOTE=Xian]Okay, do me a favor. Please post the output of the following:

```
$ ls /home
$ ls -a /home/name
```[/QUOTE]
xfce4 is now in ~/.cache. I think it changed after 4.2

---

### Post by Xian on 2005-09-24
Yep, you are correct. /home/~/.cache/xfce4

---

### Post by YourSurrogateGod on 2005-09-24
[QUOTE=Xian]Yep, you are correct. /home/~/.cache/xfce4[/QUOTE]
Cool. I changed the name of the directory, I'll now try to start up a new session. When I looked into .cache, here are the directories that I've found.
```
drwx------   2 name name 4096 2005-09-23 20:14 sessions
drwxr-xr-x   5 name name 4096 2005-09-08 19:08 xfce_temp
```

---

### Post by YourSurrogateGod on 2005-09-24
Ok, it seems that xfce is broken for sure, I renamed the xfce4 folder and no go. I'll try renaming the sessions folder and give it a try...

---

### Post by YourSurrogateGod on 2005-09-24
Ok. I renamed the sessions folder and logged into xfce, worked like a charm. I deleted my old sessions and xfce4 folders. Kewl, it works :) .

---

### Post by foxy123 on 2005-09-24
you can try to run xfdesktop and xfce4-panel from terminal to see if they would launch...

---

### Post by YourSurrogateGod on 2005-09-24
[QUOTE=foxy123]you can try to run xfdesktop and xfce4-panel from terminal to see if they would launch...[/QUOTE]
Thanks for the tip, I'll keep it in mind.

---

### Post by jecos on 2005-09-30
panel will launch from terminal.. but its a bug that needs to be fixed.

---

