---
title: "Customizing Gnome Menus"
date: 2006-03-02
forum: Desktop Environments
---

### Post by folki on 2006-03-02
Dear all, 

to what extent can one configure the Places and Desktop menus? Is it possible e.g. to remove/change the 'About Ubuntu ' menu entry or to remove the 'Places' menu completely?

I was not able to spot any configuration file for that. I had a bash on using the special locations in the file manager as pointed out in the docu but got an 'invalid location' error, i.e. it doesn't work as described. 

Any suggestions? 
Folki

---

### Post by shof2k on 2006-03-02
I think if you right click on the menu you can remove it from the panel completely.  

If you install 'alarcarte', it will allow you to edit menu entries in the 'applications' menu.

---

### Post by folki on 2006-03-02
Ok, 'remove from panel' removes all the menus, 'add to panel -> Menu Bar  adds all those menus again. 
As they belong together, where would such a menu launcher be configured?

---

### Post by shof2k on 2006-03-02
Add 'Main menu' instead of menu bar. You should be able to use alarcarte to then edit it.

---

### Post by domino1241 on 2007-03-02
I tried everything suggested but still can't seem to be able to modify the "Places" menu.  I want to add some of my own folders to the list, but because the word "places" is so common a Google search turns up nothing.  Does anyone have any idea how to do it?

Note: I made a folder called "Documents" in my Home Folder, and that was automatically added to the Places menu.  I'm trying to recreate this.  Help!

---

### Post by eXisor on 2007-03-02
Use the bookmark feature. That's what it is for.

EDIT: In other words, use Nautilus to navigate to where you want to go, then create a bookmark. It'll show up in the Places menu.

---

### Post by tbodine on 2007-03-02
If you want folders to show up in the places menu, you need to first go into Nautilus(the file manager), and navigate to the folder that contains the folder you want in the places menu.
For example, if I wanted /home/tbodine/this/folder to be in the places menu, I would go to /home/tbodine/this
Now click and drag the folder that you want in the places menu, over to the left side (where it should say Home, Desktop, Filesystem, etc.
Then your folders should appear in the places menu automagically.

---

### Post by Ux64 on 2007-11-07
**Thanks perfect guide!** It just solved both of the problems I were looking solution for!

"Use nautilus" was mentioned in several guides. But they didn't explain that it's nautilus bookmark menu which also changes places list.

**- Thanks!**

---

