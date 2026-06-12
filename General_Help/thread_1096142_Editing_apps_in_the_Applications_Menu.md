---
title: "Editing apps in the Applications Menu"
date: 2009-03-14
forum: General Help
---

### Post by dullard on 2009-03-14
I was wondering whether there's a way to edit the way a program launches from the Applications menu...

Not for the first time I've installed something today that doesn't launch when the menu item is clicked. Instead, I've had to create a launcher on the desktop/panel with a command pointing to the executable in order to get it to run.

Forgive me for not stating what software I'm having trouble with. I'd rather a general solution if there *is* one, instead of a specific one (which I'll ask for if all else fails).

---

### Post by Zill on 2009-03-14
dullard: The menu editor is called Alacarte...
Applications, Accessories, Alacarte Menu Editor.

Right-click and select application "Properties" then change as required.

---

### Post by Peasantoid on 2009-03-14
Right-click on one of the menus and select "Edit Menus".

---

### Post by ugm6hr on 2009-03-14
> **Zill said:**
> dullard: The menu editor is called Alacarte...
Applications, Accessories, Alacarte Menu Editor.

Right-click and select application "Properties" then change as required.

Default location is:
System -> Preferences -> Main Menu

---

### Post by dullard on 2009-03-14
Thanks, but no luck there :(

Okay... I'm using Hardy (8.04) and Gnome 2.22.3 if that might make a difference.

**Applications> Accessories> Alacarte Menu Editor** does not exist here.

**System -> Preferences -> Main Menu** doesn't exist here either.

Right-clicking the specific icon in the application's menu item doesn't give me any option to edit how it launches (it just gives the option to add a launcher to the panel or desktop etc.)

Right clicking **Applications** *does* give me the Edit Menus option but then I *only* have the choice of checking/unchecking each menu item.


To explain, I installed Gnome-Art NG earlier today but it won't run when I try to launch it from **Applications> System Tools> Gnome-Art Next Gen**. Instead I had to create a launcher with the appropriate command to get it running but I don't want an infrequently used launcher cluttering up the panel or desktop like that.

---

### Post by Zill on 2009-03-14
> **dullard said:**
> ...Applications> Accessories> Alacarte Menu Editor does not exist here.

Apologies for that - I based this on Dapper - it must have moved for Hardy. :oops:

I suggest you hit Alt-F2 to bring up the Run Application dialog box.  Copy the following command into this box to start up the editor.
```
alacarte
```

You will probably find that the "visible" checkbox against Alacarte is unchecked.  Check this and you should then be able to open the menu editor from the menu in future.  Edit items as suggested previously.

---

### Post by ugm6hr on 2009-03-14
> **dullard said:**
> Right clicking **Applications** *does* give me the Edit Menus option but then I *only* have the choice of checking/unchecking each menu item.

Where you have the option of checking / unchecking, try right-clicking over the text to the right of the check boxes.

This gives another option: Properties

Self-explanatory from there.

The default for Alacarte is System->Prefs->Main Menu in Gnome Hardy; not sure why you don't have it.

---

### Post by dullard on 2009-03-14
Excellent! All sorted :-)

I tried running alacarte in a terminal (thanks **Zill**) and it wasn't installed. After doing a "sudo apt-get install" it seems that it had been 'previously deselected' so it's obviously my own fault I couldn't find it! 

Heaven knows why I would've uninstalled it but I did do a lot of messing around when I first discovered Ubuntu (breaking lots of other stuff in the process... ho hum) :oops:

Thanks everybody for your help!

---

