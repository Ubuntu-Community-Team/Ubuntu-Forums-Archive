---
title: "[SOLVED] Gnome handling desktop, not xfce"
date: 2008-12-23
forum: Desktop Environments
---

### Post by djbushido on 2008-12-23
Whenever I log in to my Xubuntu computer, I am presented with the Xfce desktop I want. Then, Gnome loads up, and gives me theirs. I still have the Xfce menus and everything, just a Gnome desktop.
This is a problem.
When I go to Applications-Settings-Desktop, the checkbox to let XFCE handle the desktop is unchecked. Re-checking it brings up my Xfce desktop, which is good.
Now how do i automate getting my xfce desktop?

---

### Post by Bucky Ball on 2008-12-23
Login screen->Sessions->Xfce

Login.

You will be asked if you want to use this setup just this once or as default. Choose default. Gnome is not included with Xubuntu so you have either downloaded it or are mistaking the desktop. Check in the 'Sessions' menu at login. :)

---

### Post by djbushido on 2008-12-23
I am not mistaking it, I guarantee that. There is a visible difference between desktops, and when I go to settings, the "allow xfce to manage desktop" checkbox is undone.
I did install GNOME as a backup desktop. XFCE is my default.
The Sessions menu at login is set to XFCE session. I can check in GNOME to make sure it isn't auto-loading anything, but I doubt this is the case.
Any other ideas?

---

### Post by the yawner on 2008-12-23
Have you by any chance used Nautilus as a file browser on your Xfce desktop? In my experience running nautilus without the --no-desktop option on other DEs/windows managers would load the GNOME desktop on top of your current setup. Check the processes if nautilus is running.

---

### Post by djbushido on 2008-12-23
Okay, yeah, it is nautilus. I removed it, and xfce loaded and stayed there.
Now, how do i get nautilus to stop doing this? I would like to keep Gnome, but don't want it commandeering my desktop every time I log in. Any ideas?

---

### Post by Hangwire on 2008-12-23
I had the same problem today. 
How about putting xfdesktop in Autostart?

---

### Post by s3gfault on 2008-12-23
> **djbushido said:**
> Okay, yeah, it is nautilus. I removed it, and xfce loaded and stayed there.
Now, how do i get nautilus to stop doing this? I would like to keep Gnome, but don't want it commandeering my desktop every time I log in. Any ideas?

i guess replace your link to nautilus with one that launches it with the --no-desktop switch, like the yawner suggested.

---

### Post by snowpine on 2008-12-23
Or try using the Thunar file manager, which is Xfce-friendly.

---

### Post by djbushido on 2008-12-23
Okay, first off, what link? I don't have it in auto-started apps...
Also, autostarting "xfdesktop" didn't work...
Sorry, I know this is weird...

EDIT: doing ```
killall nautilus
xfdesktop
```

from either terminal or Alt-F2 brings me back to what i want. I guess I could do a script to automate this at startup, but I would really rather get to the root of the problem.

---

### Post by mali2297 on 2008-12-23
Check this tip:
[QUOTE=http://spuriousinterrupt.org/projects/xfce4#faq]
A more permanent solution is to set the gconf key /apps/nautilus/preferences/show_desktop to "false" (the --no-desktop will no longer be required).  This can be done using the graphical gconf-editor, or the command-line gconftool utility.
[/QUOTE]

---

### Post by djbushido on 2008-12-23
Looks like this will work, where is my apps folder?

---

### Post by mali2297 on 2008-12-23
> **djbushido said:**
> Looks like this will work, where is my apps folder?

It's not a folder per se, but a location within the gconf tree. Either install gconf-editor or use the terminal. If you choose the latter, I think this command will work:
```

gconftool-2 --type bool --set /apps/nautilus/preferences/show_desktop false

```

---

### Post by djbushido on 2008-12-24
I already had gconf-editor installed, followed this and it works fine! Thank you!

---

### Post by Bucky Ball on 2008-12-24
Nice to see this all worked out. :)

Could you mark the post as solved from the 'Thread Tools' menu so others might solve similar probs, please? 

Incidentally, I use xfce on my desktop multimedia workstation with the Ubuntu Studio packages installed minus the desktop. Works great! Gnome/Openbox on the laptop.

Have fun.

---

### Post by djbushido on 2008-12-24
Not to get too far into it, but I really like xfce because of uncluttered menus, and running on a _really_ old computer. Sorry, I meant to mark this solved (thought I did...), so will do that, and hope this helps other people. Good luck!

---

