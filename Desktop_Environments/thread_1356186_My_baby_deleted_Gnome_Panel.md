---
title: "My baby deleted Gnome Panel"
date: 2009-12-15
forum: Desktop Environments
---

### Post by n4pgw on 2009-12-15
I walked in the room and my 22 month old baby girl had Gnome panel up.  I took the mouse away and she grabbed another and somehow deleted the gnome panel.  

Ironically, I just created a shortcut to the terminal so it is the only thing I have access to.  

Please help 

Thank you
Buck

---

### Post by pixel :-) on 2009-12-15
(i'm in KDE!!!!)

I think, if you simply restart your session, it will come back. No?

other wise try in a terminal the command.

gnome-panel

normally, if you kill the terminal session, the panel will go away too, i don't remember well, but i think the command 

gnome-panel &

permits to kill the terminal without killing the panel.

---

### Post by n4pgw on 2009-12-15
> **pixel :-) said:**
> (i'm in KDE!!!!)

I think, if you simply restart your session, it will come back. No?

other wise try in a terminal the command.

gnome-panel

normally, if you kill the terminal session, the panel will go away too, i don't remember well, but i think the command 

gnome-panel &

permits to kill the terminal without killing the panel.

I restarted the computer and logged back in.  It is gone.
I tried running "gnome-panel" in the terminal and it just says "Cannot register the panel shell: there is already one running."

I tried uninstalling it with apt-get and reinstalling, but the same thing.

I'll reboot.

Someone suggested I delete gconf in home directory.  I don't know how to get there in terminal.

Thanks
Buck

---

### Post by aveightor on 2009-12-15
Are both panels gone? Do you have a panel at the bottom of the screen? If you do right click on it and click on New Panel. Then right click on the new one and add everything back.

---

### Post by coskierken on 2009-12-15
ok, here you go: in a terminal "gconf-editor".  Once it is active you go to "desktop/gnome/session/required components"  In the section called "panel" look to the right and it might be empty.  If so, just type in "gnome-panel" and hit ok.  If you double click "panel" it will bring up a second window to enter the same info.  Then just reboot and it will show up.

---

### Post by n4pgw on 2009-12-15
Now you tell me!!!  

lol did not think of it as part of the panel.  

I recovered it by following an instruction on the net... 

```
$ rm -rf .gnome .gnome2 .gconf .gconfd
```

It wiped out all my settings, but that is better than completely reinstalling Ubuntu :D

Sorry your advice was 2 minutes late, but thanks for the help. 

Buck

---

### Post by doas777 on 2009-12-15
> **n4pgw said:**
> Now you tell me!!!  

lol did not think of it as part of the panel.  

I recovered it by following an instruction on the net... 

```
$ rm -rf .gnome .gnome2 .gconf .gconfd
```It wiped out all my settings, but that is better than completely reinstalling Ubuntu :D

Sorry your advice was 2 minutes late, but thanks for the help. 

Buck

those are some questionable instructions, unless taking extreme action. where did you findd them?

---

### Post by n4pgw on 2009-12-16
I did a google search and found it, but do not remember where, I think it was on a red hat forum.

It may have been extreme, but it worked.  The only thing I seemed to lose was the bar at the top right which shows the name of the one logged in that when clicked gives logout and shutdown options.  I also lost the background image setting.  I just had to choose the background picture again.

That was a pretty minor loss, in my opinion.

---

