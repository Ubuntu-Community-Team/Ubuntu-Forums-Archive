---
title: "Common problem- no solution for me"
date: 2011-04-21
forum: Desktop Environments
---

### Post by c0dege3k on 2011-04-21
Ok, before everyone says google it I want to say that I HAVE. Been through the bunches of threads for this problem and I've yet to find a solution.

Now, I'm using compiz/emerald and about a minute after logging in, the emerald theme stays up, but everything else changes to that ugly gray theme that nobody likes. I can get most of the theme to go back just by opening up System/Prefs/Appearance, but nautilus doesnt. I cant find an answer to this, and its really starting to annoy me.

Can ANYONE help me?

---

### Post by Copper Bezel on 2011-04-21
This is becoming an absurdly common problem, so you're not alone.

Run this:

```
killall gnome-settings-daemon; gnome-settings-daemon && killall nautilus
```

The settings daemon is either dying or getting hung on something, depending on the specific case, and needs to be restarted. Then Nautilus has to be restarted, because it seems to be the one application that won't take theming changes while running.

If it happens predictably at startup, set the above command as a startup application, possibly with a

```
sleep 10s;
```

at the beginning; adjust the delay if necessary.

---

### Post by c0dege3k on 2011-04-22
Ok, that works while I'm logged in. But if I set it on start up, the theme auto-sets to the gray theme- I've tried with & without a delay.

EDIT: oh, and when it is set to go on boot, running the command to try to make it my theme doesn't work

---

### Post by Copper Bezel on 2011-04-22
Huh. Odd. Well, we have at least identified that it's the same problem, then. 

I'd try this as my next step: set it in your startup, then check your System Monitor's Processes tab to see if gnome-settings-daemon appears in the list. (You can make the list sort alphabetically.) System Monitor can be launched from the System -> Administration menu.

If it is running, check its status - Running, Sleeping, or Zombie. Then try running the command again and see if anything changes in System Monitor.

---

### Post by c0dege3k on 2011-04-22
It says it's running both before and after I run the script

EDIT: and like every other time I log in without the script set at boot, when I do run it, it kills the title bar on my programs- those already running and any I open afterwards

---

### Post by Copper Bezel on 2011-04-22
Oh,* that's* new. Do the title bars come back if you run (the usual) emerald --replace ?

---

### Post by c0dege3k on 2011-04-22
Ok, the title bar thing hasn't happened for a few times now *knock on wood*. But I am still curious as to why the script does weird stuff when run at start up. However, I've just made a little file that I run- makes things a little less annoying

EDIT: the title bar thing just happened again, and emerald --replace did fix it

---

### Post by c0dege3k on 2011-04-28
> **Copper Bezel said:**
> Huh. Odd. Well, we have at least identified that it's the same problem, then. 

I'd try this as my next step: set it in your startup, then check your System Monitor's Processes tab to see if gnome-settings-daemon appears in the list. (You can make the list sort alphabetically.) System Monitor can be launched from the System -> Administration menu.

If it is running, check its status - Running, Sleeping, or Zombie. Then try running the command again and see if anything changes in System Monitor.

I just set up another computer with compiz+emerald (still on 10.10) and the same problem happened. Only this time the gnome-settings-daemon doesn't appear at all in the system monitor. Next step?

---

### Post by Copper Bezel on 2011-04-28
Try running it from a terminal (just [font="Courier New"]gnome-settings-daemon[/font]) and post the resulting errors, if any.

---

### Post by c0dege3k on 2011-04-28
Ok, here's the errors:

```

(gnome-settings-daemon:4531): LIBDBUSMENU-GLIB-WARNING **: Error getting the properties from ID 1: The ID supplied 1 does not refer to a menu item we have

(gnome-settings-daemon:4531): LIBDBUSMENU-GLIB-WARNING **: Error getting the properties from ID 2: The ID supplied 2 does not refer to a menu item we have

(gnome-settings-daemon:4531): LIBDBUSMENU-GLIB-WARNING **: Error getting the properties from ID 3: The ID supplied 3 does not refer to a menu item we have

(gnome-settings-daemon:4531): LIBDBUSMENU-GLIB-WARNING **: Error getting the properties from ID 4: The ID supplied 4 does not refer to a menu item we have

(gnome-settings-daemon:4531): LIBDBUSMENU-GLIB-WARNING **: Error getting the properties from ID 5: The ID supplied 5 does not refer to a menu item we have

```

---

