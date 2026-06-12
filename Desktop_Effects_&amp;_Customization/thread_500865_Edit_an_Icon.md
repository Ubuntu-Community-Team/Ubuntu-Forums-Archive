---
title: "Edit an Icon"
date: 2007-07-14
forum: Desktop Effects &amp; Customization
---

### Post by Astrikor on 2007-07-14
Anyone have any ideas on how to edit the icons in a desktop sidebar?
I want to add a new icon (png extension) but it won't save to the default icons folder.
I also want to edit the text displayed when hovering on the icon.

Any ideas?

Thanks
Astrikor

---

### Post by Astrikor on 2007-07-15
> **Astrikor said:**
> Anyone have any ideas on how to edit the icons in a desktop sidebar?
I want to add a new icon (png extension) but it won't save to the default icons folder.
I also want to edit the text displayed when hovering on the icon.

Any ideas?

Thanks
Astrikor

Hi Guys,

Can no-one help here?

Any ideas gratefully received!

Astrikor

---

### Post by lluisanunez on 2007-07-15
You can simply save your icons in a .icons folder under your home directory, and then calling them from the properties window (right-click >> properties>> click on the icon >> use "Browse") of the icon you want to change
Or else you can sudo cp your icons to /usr/share/icons
Also, you can edit the text in "Comment" field in the properties window

---

### Post by Astrikor on 2007-07-15
> **lluisanunez said:**
> You can simply save your icons in a .icons folder under your home directory, and then calling them from the properties window (right-click >> properties>> click on the icon >> use "Browse") of the icon you want to change
Or else you can sudo cp your icons to /usr/share/icons
Also, you can edit the text in "Comment" field in the properties window

Sorry, doesn't work for me!

"Browse" lets me go to any folder via the directory structure, but doesn't show any files in any folder.
I have unchecked the "show only folders" box, but still no files shown.  I notice that the other default icons are listed as links to .png files - I am not sure where the actual icon files are located so I can't save a .png to the default location, however,  I have also tried dragging a link from my new icon into the default folder - with no result.  
I presume by an .icons folder you mean the .ico file extension.  Saving my .png file as a .ico file using "Image Viewer" doen't work - I just get a blank result.

Regarding text editing, that doesn't work either.  For example, I have an icon on the sidebar for openoffice spreadsheet.  When I hover over it it gives a supplementary setence after the title.  I can edit the sentence out as you suggest in the "Comment" field, but the change is not retained after I exit (there is no "save changes" button).

(As a nooby I have yet to get to grips with sudo)

Any further ideas?

Thanks

Astrikor

---

### Post by lluisanunez on 2007-07-15
> **Astrikor said:**
> Sorry, doesn't work for me!

"Browse" lets me go to any folder via the directory structure, but doesn't show any files in any folder.


That's because you don't have to select an icon, but a whole folder. 
Click on your .icons folder, and click "open" and then you'll see your icons there in the window

---

### Post by Astrikor on 2007-07-15
> **lluisanunez said:**
> That's because you don't have to select an icon, but a whole folder. 
Click on your .icons folder, and click "open" and then you'll see your icons there in the window

Thanks - it works!

That explains editing the icon,  how about it's text?

How can I get the icon text edit accepted?

Astrikor

---

### Post by lluisanunez on 2007-07-15
Is the icon in the menu, or on the panel?

---

### Post by Astrikor on 2007-07-15
> **lluisanunez said:**
> Is the icon in the menu, or on the panel?

On the desktop sidepanel

---

### Post by lluisanunez on 2007-07-15
Side panel? Is this KDE? (I'm sorry, I'm on Gnome)

---

### Post by Astrikor on 2007-07-15
I'm on gnome too, but I've added a side panel.
Exactly the same problem occurs on the top panel - I can't edit the icon text.

---

