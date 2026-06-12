---
title: "Adding drop down to Applications, Places, System"
date: 2009-02-13
forum: General Help
---

### Post by Barriehie on 2009-02-13
Is there a way to add another drop down to the main menu without using a drawer on the panel???  I don't mean add a folder to the existing drop downs but a new drop down composed entirely of editors.  I'm having issues getting the icon for the drawer to look right so I'm thinking perhaps I can do this another way?

Thanks to all,
Barrie

---

### Post by dj722000 on 2009-02-14
I think what your looking for is this.

   Right click over the menu area. 
     Click on EDIT MENUS

When MAIN MENU opens, look down towards the bottom for help. Click it.
When it opens look down towards the bottom and you will see "System Administration Guide". Click it.

Then look for MENU DEFINITION FILE

I believe this is how you make new menus in the panel.

If there is an easier way, I couldn't tell you. But this is how I found this from doing what I just told you.

By the way, I'M using 8.10, not 8.04, so it may be different.

---

### Post by Barriehie on 2009-02-14
> **dj722000 said:**
> I think what your looking for is this.

   Right click over the menu area. 
     Click on EDIT MENUS

When MAIN MENU opens, look down towards the bottom for help. Click it.
When it opens look down towards the bottom and you will see "System Administration Guide". Click it.

Then look for MENU DEFINITION FILE

I believe this is how you make new menus in the panel.

If there is an easier way, I couldn't tell you. But this is how I found this from doing what I just told you.


By the way, I'M using 8.10, not 8.04, so it may be different.

That's it!  Thank you dj722000!  It appears in 8.04 just as you described.

---

### Post by Barriehie on 2009-02-15
**Follow up**

After examining the files used in generating the menus I've found a few things out:

1)  You can't add another item to go across the panel

2)  The architecture retains entries, even those that aren't used.  Not sure what good this is.  The files tend to grow when changes are made, i.e. removing an application,      rather than remove the entries they are tagged to be ignored.

3)  To many files involved, the data spread across the directories/files involved could be     managed in 1 file with a bit more design.

4) With better programming skills I could fix this. :)

Barrie

---

### Post by PaulWhipp on 2009-03-19
In 8.10 I find I often need extra menus for different work areas to open frequently used documents etc. While its a bit irritating I can't use the drawer (because I'd have to remember and edit too many icons and I haven't found a way to display an item in the drawer with a label as well as an icon), here is a handy workaround:

Add your particular menu to the Applications menu at the bottom by right clicking on the menu and selecting "New menu". Add your items to it there. For example to open a spreadsheet doc you can add an item that invokes oocalc on your document. This helps keep the desktop free of shortcuts etc.

Now you can put your menu onto a panel directly to save having to drill down to it in the applications menu by right clicking on one of your items and selecting to add the "Entire menu" to the panel.

Remarkably, alacarte wont let you delete these menus but they disappear if you remove all the contents. To really remove them or change the icon for the whole menu you have to dig into the menu specification as indicated earlier in this thread but in practice I've never needed to do that - I find one 'reference' and one 'work' menu suffices to keep my desktop and panel pleasantly free of excessive clutter.

---

