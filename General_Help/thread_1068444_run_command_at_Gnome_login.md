---
title: "run command at Gnome login"
date: 2009-02-12
forum: General Help
---

### Post by pytheas22 on 2009-02-12
I'd like to run a command every time a user logs into Gnome.  I know that this can be done easily by going to System>Preferences>Sessions, but I need to do this from the command line, without using the graphical interface.

I thought this would be simple, but I'm quite surprised at how difficult it's proving to be.  This is what I've tried so far:

1. I added .desktop entries to ~/.config/autostart for the program I wanted to run.  However, the new entries don't appear in the Gnome Sessions window, and the commands that they're supposed to run never get run.  It seems that Gnome Sessions ignores .desktop files that are added manually.  It only recognizes them if I add them through the graphical Sessions utility.

2. I added .desktop entries to /etc/xdg/autostart (which is where Ubuntu stores Gnome startup utilities that should be run for every user), with the same results as above.

Does anyone know how to make Gnome recognize new entries?

Alternatively, if there's some other way that I can tell the system to run a custom command when a user logs into Gnome please tell me.  Most of the traditional approaches (~/.Xession for example) seem to no longer exist in Ubuntu 8.10.

At this point I don't care whether the command gets run for every user on the system, or just the ones I specify.  I don't care how dirty the solution is; I just want to find something that works!

---

### Post by lswb on 2009-02-12
When gdm starts the gnome desktop one of its startup scripts sources your .profile so you can place the command there. Note that you cannot count on your X server having started at that time, so if your command is for an X program it may fail to run.

---

### Post by pytheas22 on 2009-02-13
Thanks for that.  It more or less works, although it seems to start the X application before gnome-settings-daemon and other things have started, which might be a problem but I suppose I can work around it.  It also hangs on the X application and stops loading the rest of the desktop, but I suppose that adding a & to the end of the command will make it not do that.  This at least gets me further along; thanks for the tip.

If anyone has alternative ideas, I'm still open to them.

---

### Post by adult swim on 2009-02-13
you can delay the command with sleep, replacing xx for how many seconds youd like to delay the command
```
sleep xx && command
```

---

### Post by Neural oD on 2009-02-13
> **adult swim said:**
> you can delay the command with sleep, replacing xx for how many seconds youd like to delay the command
```
sleep xx && command
```
+1 for that - sleep is really good for one ;)

---

### Post by lswb on 2009-02-13
You may want to look at 
[http://library.gnome.org/admin/gdm/stable/configuration.html.en#scripting](http://library.gnome.org/admin/gdm/stable/configuration.html.en#scripting)

It states that /etc/gdm/Xsession is run as the user logging in. I've looked at this script and it was not obvious (to me) where custom commands should be added.

---

### Post by pytheas22 on 2009-02-13
Thanks for the additional suggestions.  The sleep command is a good idea.

I also tried adding the command to /etc/gdm/Xsession and it didn't work.  But I didn't try very hard and the script there is indeed not clear about where custom commands should be added.

---

