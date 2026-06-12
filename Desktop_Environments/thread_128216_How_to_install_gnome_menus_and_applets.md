---
title: "How to install gnome menus and applets"
date: 2006-02-10
forum: Desktop Environments
---

### Post by mayankgarg1 on 2006-02-10
Dear all
I am a newbie in linux and installed breezy on my P4 2.6ghz pc
yesterday by mistake i have uinstallled gnome-menu,gnome-applets etc
so i could not launch any application as no menu is visible
Please help me to get back those menus

---

### Post by cdhotfire on 2006-02-10
Do you mean you deleted the panel?
Or the panel is there but when you hover over the menu no applications show up?

---

### Post by mayankgarg1 on 2006-02-10
I think I have deleted the panels
as they are not visible neither Application/System/Places etc

---

### Post by Piggah on 2006-02-10
If you just deleted your top panel with your menu, you just need to add a new panel.

Right click on any other panel you have, and select add new panel. Then just set it to the top and then just add to panel and select menu bar and whatever else you'd like.

---

### Post by cdhotfire on 2006-02-11
Press Crtl + Alt + Backspace.  Then choose to run under Gnome in "Sessions" this should bring your panels back, if not, let me know.

---

### Post by mayankgarg1 on 2006-02-11
this has not worked 
what command should i give on command prompt to get back the panels

---

### Post by cdhotfire on 2006-02-11
How are you able to open up the command line? do you have another panel?

If so right click in an empty space of it and press "New Panel". Then go to the new panel and right click it then press "Add to Panel" then select "Menu Bar" and anthing else you might need. Make sure to lock them after you have moved them around to your liking. :)

---

### Post by mayankgarg1 on 2006-02-11
I have no other panel on desktop
I have opened command line by Ctl+Alt+F1 keys

---

### Post by cdhotfire on 2006-02-11
Hmmm, put in gnome-panel, see if something shows up, if not then there is only one other way I know off. Type in
```

$ nautilus

```

This should bring you to your home folder, now press crtl+h to reveal hidden folders, find .gconf, go in it. Then go to apps, dl this
[http://s39.yousendit.com/d.aspx?id=0IZULHWBMH9D30FI7PPQC4LGJ0](http://s39.yousendit.com/d.aspx?id=0IZULHWBMH9D30FI7PPQC4LGJ0)
its mine, put the "panel" folder inside of the "apps" folder, it should bring a panel back up once you relogin, but it will be my panel so change it as you like.

Good luck.

---

### Post by alfonz on 2006-02-11
I don't know if I understood his post right, but I do believe he uninstalled the panel... errr I could be wrong.

---

### Post by mayankgarg1 on 2006-02-11
[QUOTE=alfonz]I don't know if I understood his post right, but I do believe he uninstalled the panel... errr I could be wrong.[/QUOTE]
You are right I have uninstalled the panels

Thanks Cdhotfire
Iwill try that tommorrow and comeback to you

please give me any other option also to try

---

### Post by alfonz on 2006-02-11
try using 

```
sudo apt-get install <package name goes here>
```

or load synaptic and do a search for gnome and look at all the options. if you see them check them off and apply

it might work.

---

### Post by mayankgarg1 on 2006-02-21
[QUOTE=mayankgarg1]You are right I have uninstalled the panels

Thanks Cdhotfire
Iwill try that tommorrow and comeback to you

please give me any other option also to try[/QUOTE]

Dear Friends
I have tried in aptitude and it gives me error that GNome-Panel could not be installed and it has been deleted becuase it has got no dependencies.
I have got KUbuntu install Cd and uButnu live cd , is these can help me in recovering Gnome-panel.

---

### Post by cdhotfire on 2006-02-23
Hmm, if you type in gnome-panel, does it say command does not exist, does it show nothing, or does it give out an error?

If it shows command doesnt exist then do
```

$ sudo apt-get install gnome-panel gnome-applets gnome-applets-data

```

If it shows nothing, then do use the file I sent you.

If it gives out an error, let me know what it is. :)

---

