---
title: "Nautilus &quot;shortcuts&quot; in 12.04"
date: 2012-05-03
forum: Desktop Environments
---

### Post by Warthaug on 2012-05-03
Back in the "old days" (i.e. 11.10) I could drag a folder onto the left-bar in the nautilus window and add it to the "shortcut list".  This was convenient, since the pre-installed shortcuts are not of much use for me, but there are fodlers I access near-hourly that were nice to have listed there.

I cannot figure out for the life of me how to do this in 12-04.  I can neither remove [SIZE="1"](the option in the left-click menu is greyed out)[/SIZE], nor add [SIZE="1"](dragging/dropping just copies the contents of the folder into whichever shortcut was closest to the drop-point)[/SIZE] folders to nautilus's side-pane.  Even using the terminal to launch nautilus with sudo didn't give me the access I desire.

Anyone know a work-around?

Thanx

Bryan

---

### Post by billyseth on 2012-05-03
While I don't know how to remove the default ones, you can add shortcuts...

Browse to the folder you want to shortcut to, then choose bookmarks from the menu, then add bookmark. That should add that folder to your bookmarks section on the left

---

### Post by mc4man on 2012-05-03
You can DnD to the 'Bookmarks' section in the sidebar to add , though it won't show till you've added at least one folder to your bookmarks by some other means
(the computer section only allows DnD into the selected folder

Seems odd the Bookmarks dropdown in nautilus is greyed out

What happens if you open some folder & go Ctrl+D on the keyboard, does it get added to the sidebar?

You could also try manually adding - from terminal
```
gedit .gtk-bookmaks
```

Add some folder using the same format as you see there - ex. 
file:///usr/share/applications

---

### Post by Warthaug on 2012-05-04
billyseth's method worked - folders added.  Now if only I could rid nautilus of the music and pictures folders...

Thanx

Bryan

---

### Post by Menthu_Rae on 2012-05-19
> **Warthaug said:**
> billyseth's method worked - folders added.  Now if only I could rid nautilus of the music and pictures folders...

Thanx

Bryan

I love how we are consigned to no longer having a choice in simple things like this... it drives me mad :mad:

---

### Post by chrisbracken on 2012-10-11
> **Warthaug said:**
> Now if only I could rid nautilus of the music and pictures folders...

Months late, but edit ~/.config/user-dirs.dirs

---

