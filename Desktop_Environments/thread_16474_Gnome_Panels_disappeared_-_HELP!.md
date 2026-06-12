---
title: "Gnome Panels disappeared - HELP!"
date: 2005-02-21
forum: Desktop Environments
---

### Post by andbert on 2005-02-21
Ive been playing around with Crossover Office.
I finally managed to get all my MS apps to work in Ubuntu.

I decided to reboot the system, and then, after logging into GDM, my top panel was gone. And my bottom panel does not look like it use to.

I have no options when I right-click the remaining panel, and I wonder what happened.
And of course how I could solve it?

I have access to all programs on the desktop.

---

### Post by kassetra on 2005-02-21
Ok, let's see if we can't fix the problem here...

1. start a terminal (right click on desktop, "open terminal") and type
 ```
gnome-panel
```  

2. When they come up, go to Computer->Desktop Preferences->Sessions, Current Session tab

3. Scroll down through the list and make sure that you see a restart icon in the style column next to "gnome-panel"  in the list (look at metacity's icon to compare if you're not sure) 

4. Stop the panels running from the terminal by pressing CTRL+c in the terminal window

5. Restart your gnome session (CTRL+ALT+Backspace)

That should fix the problem.  *Should*

---

### Post by KLineD on 2005-02-21
That exactly happened to me and couldn't fix it. My solution? I upgraded to hoary and that fixed the problem. I know maybe is not the best solution.

With fear that the same thing would happen, I reinstalled crossover office, and now everything runs smooth.

---

### Post by andbert on 2005-02-21
Yeah... 
I have been trying everything for the last couple of hours, so I guess ill try upgrading to Hoary.

So you think that this IS Crossover-related?

---

### Post by KLineD on 2005-02-21
My guess is yes, maybe something to do with crossover trying to write it's own menu entry but that's just a big guess I really don't know.

In hoary crossover didn't get any menu entries also but it didn't rendered my gnome useless

---

### Post by kassetra on 2005-02-21
andbert:
you could also try moving your /home/username/.gnome2/panel2.d folder to /home/username/.gnome2/backup_panel2.d and restarting gnome...

---

### Post by andbert on 2005-02-22
hmmfh...
none of the suggested solutions worked for me, so i guess ill try the Hoary-upgrade.

If that fixes the problem, will i then be able to upgrade back to warty and have full functionality?

---

### Post by kamstrup on 2005-02-22
I have two ideas...

1) Look in the gconf-editor for weirdnesses... Programs->System->Conf.edit (or just 'gconf-editor' in a terminal). Then browse to apps->panel and look for weird settings.

2) Try running 'sudo update-desktop-database /usr/share/applications'. Some install scripts  bork up the .desktop file database, which can cause weird behavior all over the place.

---

### Post by andbert on 2005-02-22
Thanks man.
I will try it after work later today.

---

### Post by andbert on 2005-02-22
[QUOTE=kamstrup]
2) Try running 'sudo update-desktop-database /usr/share/applications'. Some install scripts  bork up the .desktop file database, which can cause weird behavior all over the place.[/QUOTE]

That gave med the following output:

```
** (process:4276): CRITICAL **: file eggdesktopentries.c: line 2223 (egg_desktop_entries_add_group): assertion `egg_desktop_entries_lookup_group (entries, group_name) == NULL' failed

** (process:4276): CRITICAL **: file eggdesktopentries.c: line 2223 (egg_desktop_entries_add_group): assertion `egg_desktop_entries_lookup_group (entries, group_name) == NULL' failed

** (process:4276): CRITICAL **: file eggdesktopentries.c: line 2223 (egg_desktop_entries_add_group): assertion `egg_desktop_entries_lookup_group (entries, group_name) == NULL' failed
andreas@ubuntu:~ $
```

---

