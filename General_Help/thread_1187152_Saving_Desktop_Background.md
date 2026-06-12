---
title: "Saving Desktop Background"
date: 2009-06-14
forum: General Help
---

### Post by casmok on 2009-06-14
What silly thing am I forgetting here?

I just installed Jaunty. In setting things up Preferences > Appearance I copied and added my customised desktop background from a disk. However,  it wont save so when I reboot it reverts back to the default. So how do I save it permanently

Thanks!

---

### Post by Amilo1718 on 2009-06-14
hello
what happens if you right-click your desktop & select change background?

---

### Post by Holyjoely on 2009-06-14
The right-click method works for me...

Not sure what to suggest.

---

### Post by hansdown on 2009-06-14
Hi casmok.

This is how I like to do it.

Rightclick a spot on your desktop.Click change background.Click add.

Let's say you wish to add one of your backgrounds from pictures.

Click pictures. Double click a picture.Click open.

Click close. It will be saved in your background folder.

---

### Post by casmok on 2009-06-14
> **hansdown said:**
> Hi casmok.

This is how I like to do it.

Rightclick a spot on your desktop.Click change background.Click add.

Let's say you wish to add one of your backgrounds from pictures.

Click pictures. Double click a picture.Click open.

Click close. It will be saved in your background folder.

Yes that did it, Thanks! But... it didn't save in the /usr/share/bookmarks folder. It is in the System>Preferences>Appearence>Backgrounds menu so god knows where it IS saved?

I find I a unable to anything in the Backgorounds folder presumably due to permissions which I admit I dont fully understand yet! (my next project) For example there are a bunch of preloaded backgrounds that I dont want and would like to delete but cant. Likewise there are all sorts of "examples" that I dont need either. I'll eventually figure out how to accesss them and similar and delete them.

Mike

---

### Post by cariboo on 2009-06-14
You can run nautilus as root to delete the backgrounds you don't want. Press Alt-F2 and type:

```
gksu nautilus
```

Be very careful what you delete, as you can make your system unusable.

---

### Post by hansdown on 2009-06-14
> **casmok said:**
> Yes that did it, Thanks! But... it didn't save in the /usr/share/bookmarks folder. It is in the System>Preferences>Appearence>Backgrounds menu so god knows where it IS saved?

I find I a unable to anything in the Backgorounds folder presumably due to permissions which I admit I dont fully understand yet! (my next project) For example there are a bunch of preloaded backgrounds that I dont want and would like to delete but cant. Likewise there are all sorts of "examples" that I dont need either. I'll eventually figure out how to accesss them and similar and delete them.

Mike

If it came from your pictuer folder, it is saved there.Just remember, if 

you move the original picture in your picture folder to trash, it will

also remove it from your background folder.

I saved one to my desktop once, and later decided to cleanup my desktop.

After moving the desktop picture to trash, the backgroun picture also 

disappeared.

---

