---
title: "how to auto-run an app under unity"
date: 2017-07-12
forum: Desktop Environments
---

### Post by Skaperen on 2017-07-12
in unity under 16.04.2 LTX i would like to have an app auto-run or auto-started when that user logs in on unity (not from an ssh login).  in one case i want to start a background script (no window open).  in another case i want to start a terminal window with a specific environment variable set so that my .bashrc script will know this is that initial terminal screen.  in yet another case i want to start firefox (being able to specify the URL to visit in this case is a plus).  **anyone know how to set this up per user?**

---

### Post by DuckHook on 2017-07-12
You may find "Startup Applications" useful.

[https://help.ubuntu.com/stable/ubuntu-help/startup-applications.html](https://help.ubuntu.com/stable/ubuntu-help/startup-applications.html)

---

### Post by Frogs Hair on 2017-07-12
You can open Firefox to a url from startup applications using the following command , but I can't test this per user on single user system. Tested example:```
firefox %u https://ubuntuforums.org/
```

---

### Post by DuckHook on 2017-07-12
> **Frogs Hair said:**
> You can open Firefox to a url from startup applications using the following command , but I can't test this per user on single user system. Tested example:```
firefox %u https://ubuntuforums.org/
```
I believe that anything invoked with "Startup Applications" will affect only the one user who owns the desktop. Moreover, I also suspect that such apps will only run within a Unity session, though I am less sure about this latter conjecture.

---

### Post by deadflowr on 2017-07-12
Startup Applications that are setup and created can run on any Gnome session.
I cannot say about how they work for non-Gnome sessions.
But they do work with gnome-shell unity gnome-flashback.
They might work with mate. 
Not sure about kde lxde or xfce. I think those 3 have their own autostart settings that differ from gnome-based autostarts.

But they would only run for the user who sets them if you use the Startup Applications to set them up.
However...

If you wanted to set it so that all users would have an app start at login, for all users, create and place a startup desktop file in /etc/xdg/autostart.
I think the easiest way to do that is simply create the startup applications for the first user, then copy the startup application file that was created and moved it (or copy it) into the /etc/xdg/autostart folder.
The autostart desktop files a user creates are in ~/.config/autostart.

Bonus:
A nifty additional feature you can add to a startup applications desktop file is a delay.
Which can be very useful when dealing with unity since sometimes the startup app and unity fight each ( or so it seems ) and the winner is a funky desktop or odd window placement of the startup app.
To add the delay option just add
```
X-GNOME-Autostart-Delay=##
```
to your startup application .desktop file. 
Change the ## to the number you want for the delay (in seconds).

(These are desktop files so you would need to open a text editor first to edit them; either drag and rop it into the text editor or use the text editor open dialog to find the file to open.
desktop files are application launchers and do not have open with options, if that make sense) 

for what it's worth, but not much else.

---

### Post by Skaperen on 2017-07-13
> **DuckHook said:**
> You may find "Startup Applications" useful.

[https://help.ubuntu.com/stable/ubuntu-help/startup-applications.html](https://help.ubuntu.com/stable/ubuntu-help/startup-applications.html)

based on this link, i found that i can do "ln -s $(which gnome-session-properties) add-startup" then "./add-startup" when i want to add or remove startups.

---

### Post by Skaperen on 2017-07-13
> **deadflowr said:**
> If you wanted to set it so that all users would have an app start at login, for all users, create and place a startup desktop file in /etc/xdg/autostart.
I think the easiest way to do that is simply create the startup applications for the first user, then copy the startup application file that was created and moved it (or copy it) into the /etc/xdg/autostart folder.
The autostart desktop files a user creates are in ~/.config/autostart.

How could I just start a script/command/program, instead of a desktop file, for all users?

---

