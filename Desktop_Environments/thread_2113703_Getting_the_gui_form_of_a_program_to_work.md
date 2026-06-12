---
title: "Getting the gui form of a program to work"
date: 2013-02-08
forum: Desktop Environments
---

### Post by ShowMeGrrl on 2013-02-08
I am running Ubuntu Lucid 10.04 desktop.

Today I used the Ubuntu Software Center on the Applications Menu to install a program called linkchecker-gui 

The Software Center showed an image of the gui of the program and also the program has -gui in its name, so I assumed that I was installing a gui form of the program.

I installed the program by clicking on the "install" button; no installation problems were reported.

However, after installing it, I was unable to find an icon for it on any of the applications menus.

So I went into the terminal and typed linkchecker followed by a URL. The program worked very well: it very speedily checked scores -- perhaps hundreds -- of links and clearly and accurately flagged the problems.

However, I would like to have the gui form of the program rather than the terminal form. I would also like to get an icon for the program onto my Applications menu. 

Does anybody know how I can summon the gui form of the program? And how I can get an icon for it to show up in my Applications menu?

---

### Post by furything on 2013-02-08
Works on unity running 12.04.
from cmd line```
linkchecker-gui
```
I also get a menu item but it uses the default icon so I guess the app has not got one.

---

### Post by ShowMeGrrl on 2013-02-08
> **furything said:**
> Works on unity running 12.04.
from cmd line```
linkchecker-gui
```
I also get a menu item but it uses the default icon so I guess the app has not got one.

Yes! That works to type "linkchecker-gui" into the terminal instead of just "linkchecker" That successfully brings up the gui form of the program.

And after much trial and error I finally figured out how to get an icon -- albeit, as you say, a default icon -- onto the menu:

1. Right click on the word "Applications" in the desktop's top panel.
2. Click on "Edit Menus"
3. In the left-hand panel, select the sub-menu you want. In my case, it was "Internet." 
4. In the right-hand panel, all of the programs on the Internet sub-menu will appear. Click on the "New item" button
5. Fill in the name you want to give the program in the "Name" slot.
6. In the "Command" slot, fill in (no quotes) "linkchecker-gui"
7. Click OK.

Thanks much for your response, furything.

---

### Post by furything on 2013-02-08
you're welcome:D

---

