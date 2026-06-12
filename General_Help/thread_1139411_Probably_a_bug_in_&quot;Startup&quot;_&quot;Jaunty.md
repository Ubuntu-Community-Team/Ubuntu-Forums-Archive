---
title: "Probably a bug in &quot;Startup&quot; &quot;Jaunty&quot;"
date: 2009-04-27
forum: General Help
---

### Post by redserpent7 on 2009-04-27
I'm not sure if this is a bug or if i'm not doing things right. I've been trying to add a new startup application via the startup manager and I'm setting it up as I did with the old sessions manager. everything seems to go well and the application I want (AWN) to be precise is added to the list of startup applications. however when I click the close button and reopen the startup manager it disappears. I even tried dragging and dropping the AWN icon from the applications menu onto the startup manager and it was added successfully to the list but still when i restart SM it doesn't show and of course when i restart my computer AWN doesnot run automatically.

to tell ya the truth, i haven't tried adding any other applications as I only need to customize AWN to run on startup.

---

### Post by ninjapirate89 on 2009-04-27
Are you sure you put all of the necessary info? 
For AWN your Startup should look like this:

Edit -> Then click Add

---

### Post by redserpent7 on 2009-04-27
yes I'm sure. as I said this worked for me on early dists

---

### Post by ninjapirate89 on 2009-04-27
What about the check-box in the preferences in AWN that says something like "Start AWN at login"? Have you checked that? (Sorry I haven't used AWN a whole lot)

---

### Post by redserpent7 on 2009-04-27
Ok so I've tried running Startup Manager under commmand line and added AWN, I got this error message in terminal.

** (gnome-session-properties:4396): WARNING **: Could not save /home/zaid/.config/autostart/avant-window-navigator.desktop file

Any ideas, not sure what to do here. :confused::confused:](*,):-k:-k

---

### Post by CatKiller on 2009-04-27
Have you changed the permissions on ~/.config or anything like that?

You could also manually create the .desktop file in that location. That's what the sessions tool does. It should contain something like this.

```

[Desktop Entry]
Type=Application
Encoding=UTF-8
Version=1.0
Name=AWN 
Comment=Task manager/launcher dock tool
Exec=avant-window-navigator
X-GNOME-Autostart-enabled=true

```

---

### Post by redserpent7 on 2009-04-28
> **CatKiller said:**
> Have you changed the permissions on ~/.config or anything like that?

You could also manually create the .desktop file in that location. That's what the sessions tool does. It should contain something like this.

```

[Desktop Entry]
Type=Application
Encoding=UTF-8
Version=1.0
Name=AWN 
Comment=Task manager/launcher dock tool
Exec=avant-window-navigator
X-GNOME-Autostart-enabled=true

```

I would do that except the autostart directory doesnot exist, instead there is a file of that name in that location. With the compiz script. I tried adding the script you mentioned as an entry in that file, but this only displayed an error message when I restarted the computer.

---

### Post by CatKiller on 2009-04-28
> **redserpent7 said:**
> I would do that except the autostart directory doesnot exist, instead there is a file of that name in that location. 

Really? Weird. No wonder it couldn't automatically make the file. You could rename that file to something like autostart.old and try again to see if everything works after that. If it doesn't, you can always rename that file back.

---

### Post by trotos on 2009-05-01
got the same thing.

I cannot add, or edit anything on the startup applet. Also I do not know where it is located so to do it manualy

---

### Post by CatKiller on 2009-05-01
> **trotos said:**
> Also I do not know where it is located so to do it manualy

Make a directory in ~/.config called autostart. Case is important. Create a text file in there called avant-window-navigator.desktop that contains the text that I gave you earlier. Log out and log back in.

Hopefully AWN will have automatically started.

---

### Post by redserpent7 on 2009-05-10
yeah well thanx Catkiller that worked for me, I don't like messing with system files but anyways i did it and am not really happy about it :(

---

