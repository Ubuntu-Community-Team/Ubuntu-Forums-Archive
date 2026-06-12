---
title: "Gnome Applications menu isnt working properly"
date: 2007-03-24
forum: Desktop Environments
---

### Post by profXavier on 2007-03-24
Symptoms:

When I click on my Applications menu listed on my top panel, the menu does NOT drop down.  What actaully happens is (an outline caused by selection of an item) this box appears around the last icon (the "quick launch menu") I selected.

Pre-issue:

So I am currently trying to do many things on my system, and one thing I wanted to understand was how to add items to the list manually.  I have a remote desktop I connect to daily, so I thought, ill be handy.  I added the following:

[Desktop Entry]
Name=Xvnc-Parents
Comment=Connecting to Mom and Dads
Exec=xvncviewer *.*.*.* (hidden IP)
Icon=
Terminal=false
Type=Application
Categories=Application;Network;

*NOTE: I did save this as Xvnc-parents.desktop -- so it did work
Once I added this, I found it worked successful.  Now, something has happened so I cannot use my Applications (see issue above) menu. 

The Places and System menu next to it work just fine.  So I am not sure what to try.  Any ideas?

One thing I did do, was remove this new item (from /usr/share/applications) and the menu still doesnt work.

---

### Post by josephus on 2007-03-24
Not entirely clear about the problem. 

If you edit the menu layout (either right click on the menu bar or go into System->Preferences->Menu Layout) what do you see.  Are there any items that are checked off to be displayed?

---

### Post by profXavier on 2007-03-24
I cannot open the Menu Layout.  My output is at [pastbin]("http://pastebin.ca/408388") from the output from alacarte.

---

### Post by ardchoille42 on 2007-03-24
> **profXavier said:**
> Symptoms:

When I click on my Applications menu listed on my top panel, the menu does NOT drop down.  What actaully happens is (an outline caused by selection of an item) this box appears around the last icon (the "quick launch menu") I selected.

Pre-issue:

So I am currently trying to do many things on my system, and one thing I wanted to understand was how to add items to the list manually.  I have a remote desktop I connect to daily, so I thought, ill be handy.  I added the following:

[Desktop Entry]
Name=Xvnc-Parents
Comment=Connecting to Mom and Dads
Exec=xvncviewer *.*.*.* (hidden IP)
Icon=
Terminal=false
Type=Application
Categories=Application;Network;

*NOTE: I did save this as Xvnc-parents.desktop -- so it did work
Once I added this, I found it worked successful.  Now, something has happened so I cannot use my Applications (see issue above) menu. 

The Places and System menu next to it work just fine.  So I am not sure what to try.  Any ideas?

One thing I did do, was remove this new item (from /usr/share/applications) and the menu still doesnt work.

Not sure if yu're aware of this, but you can put new menus items in ~/.local/share/applications and they will appear in the menus the same way the items in /usr/share/applications do. This might save some sudo'ing.

Your menu items are also listed in ~/.config/menus/*  there are two files there and they have to be in sync with the items in /usr/share/applications and ~/.local/share/applications or yur menus can act weird. Have you tried looking at those two files?

---

### Post by josephus on 2007-03-24
I'm figuring this out as I go along, but it looks like it has some error parsing a file.  Tracing through the program on my system I think that it might be opening '~/.config/menus/applications.menu'
and '~/.config/menus/settings.menu'

it's possible that these files might be corrupted in some way that is causing problems for the parser.  Try:

```

mv ~/.config/menus/applications.menu ~/.config/menus/applications.menu.old
mv ~/.config/menus/settings.menu ~/.config/menus/settings.menu.old

```

and see if that clears up the problem.  If it doesn't help then just rename them back to the original names.  Hope this helps.

edit:  I just read what ardchoille42 just wrote and I think that we are referring to the same thing

---

### Post by ardchoille42 on 2007-03-24
> **josephus said:**
> 

edit:  I just read what ardchoille42 just wrote and I think that we are referring to the same thing

Yes, we are on the same page :)
I have also noticed that when you move those two files, any menu items that you have added will disappear.. since those two files and the .desktop files are no longer in sync.

---

### Post by profXavier on 2007-03-24
Ok, well that mv actually worked, I am still not 100% clear on what the issue was, and it is definitly a quick fix. So it basically allow the menu to rewrite a new applications.menu and new settings.menu because those were both moved?

Just want to make sure I understand correctly.

---

### Post by josephus on 2007-03-24
That sounds about right.  If you really want to know what exactly went wrong, you can look inside the  applications.menu file (i'm guessing the settings.menu was fine all along)  and try to figure out which entry was causing the problem.  Most likely it's the entry related to xvnc.desktop file.

---

