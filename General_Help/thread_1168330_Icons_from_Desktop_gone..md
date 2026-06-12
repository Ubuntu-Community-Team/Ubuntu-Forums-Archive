---
title: "Icons from Desktop gone."
date: 2009-05-23
forum: General Help
---

### Post by BslBryan on 2009-05-23
Hello, everyone. :-)

I'd just finished up the theme that I've been working on, and started restoring all of my icons, what have you, back to normal.  

Everything's back to normal now, but my "Computer" and "Trash" icons are gone.  Not in the way you'd expect, though.  I'm not a n00b. ;)

Take a look at the screenshot.  Anyone's natural reaction would be "well, you must have replaced the icons with new ones, and so when you moved or deleted them, there was no icon left."  

That would be sound logic, except that I was lazy and hadn't gotten around to changing those icons yet, so for screenshot purposes, I right-clicked --> properties, and changed the icons that way.  

Now, I can't find the original computer icon, and have no idea as to how to have a functional trash again.

Any ideas?

---

### Post by asmoore82 on 2009-05-24
You could try moving the file "~/.nautilus/metafiles/x-nautilus-desktop:%2F%2F%2F.xml"
to a backup location and then `xkill` the desktop to refresh.

---

### Post by BslBryan on 2009-05-24
Hmm...  Didn't work.  :-k

Thanks for your speedy reply, by the by.

Any other ideas?

---

### Post by QIII on 2009-05-24
I rethought my original idea ...

Are you wedded to having it on your desktop, or would the Gnome panel do just as well?

---

### Post by QIII on 2009-05-24
For your Computer icon, just go to Places, the right-click-and-hold on the Computer icon there and drag it on to your desktop.

---

### Post by BslBryan on 2009-05-24
All right, so the Computer icon works now.  :-)

I tried this on a hopeful, brave whim, and it gave me a new, completely default desktop:

```
rm -rf .gnome2 .gconf .gconfd .metacity

```

I thought that removing these would make everything default and great...  Well, everything was set back to its default with the exception of the two icons. :roll:

I am really not up for putting my trash on the panel...

Any other suggestions?

---

### Post by DeMus on 2009-05-24
> **BslBryan said:**
> All right, so the Computer icon works now.  :-)

I tried this on a hopeful, brave whim, and it gave me a new, completely default desktop:

```
rm -rf .gnome2 .gconf .gconfd .metacity

```

I thought that removing these would make everything default and great...  Well, everything was set back to its default with the exception of the two icons. :roll:

I am really not up for putting my trash on the panel...

Any other suggestions?

I installed a program called Ubuntu Tweak. In there you find a tab called Desktop. When clicking it it will open further and you see an item called Icons.
On the right side you can now switch on several icons, including Trash.
Maybe this works for you.

---

### Post by BslBryan on 2009-05-24
Thanks, DeMus, but it didn't work.  It was basically a more GUI based configuration editor, and it runs the exact same commands.

Thanks, everyone, for your help. :-)

Any other ideas?

EDIT: I think I'm off to bed.  I've temporarily added the empty-trash icon to my desktop as a placeholder that, at least, looks normal now.  

I'll check back here in the morning.  Good night!

---

### Post by Legace on 2009-05-24
Press ALT+F2, type in gconf-editor, and browse to:
/apps/nautilus/desktop

Then make sure both computer_icon_visible and trash_icon_visible are checked :)

---

### Post by BslBryan on 2009-05-24
Thanks, but I don't need to verify that.  Even those icons wouldn't be on my desktop if those options weren't checked. :-)

Anybody have any other suggestions?

---

### Post by BslBryan on 2009-05-30
Bump.  ;)

I have temporarily solved this, but now my trash icon is broken.  I can delete files, whatever, but the icons do not change.

---

### Post by BslBryan on 2009-06-02
Bump

---

### Post by BslBryan on 2009-06-03
Bump.

---

### Post by BslBryan on 2009-06-06
This is actually a pretty annoying problem.  I can't seem to find any way around it.  Bump.

---

### Post by BslBryan on 2009-06-07
... Bump?

---

### Post by BslBryan on 2009-08-05
It was pretty simple to fix.  

1.  Right-click on the broken icon.  Select Properties.
2.  Click on the icon in properties to change it.
3.  At the bottom of the file browser, next to Cancel and OK is a third option: Revert.
4.  Select this option and all should be well! :)

---

