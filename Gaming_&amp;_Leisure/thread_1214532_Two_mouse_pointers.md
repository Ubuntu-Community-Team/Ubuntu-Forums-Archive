---
title: "Two mouse pointers?"
date: 2009-07-16
forum: Gaming &amp; Leisure
---

### Post by shyce on 2009-07-16
When initiating OpenGL, the X-Mouse cursor is stuck in position and I have a game cursor that moves freely. 

I'm running an Intel 965GM chipset with X3100 graphics by Intel. I've applied the latest kernel and done all the Jaunty Intel work-arounds but I'm still running into this issue.

Anything in xorg I can change to fix this?

---

### Post by shyce on 2009-07-16
It seems like nobody else has this problem with a stock install of Jaunty. So I've got it pretty much narrowed down to either my Touchpad (Alps), or my graphics chipset GM965 Intel.

Anyone with more insight on this?

---

### Post by mgmiller on 2009-07-17
I ran into the exact same problem running UT2k4 with nvidia graphics.  I needed to turn off compiz and all was well.  I now have a button in my menu to enable metacity to play and another to go back to compiz when I'm done.

---

### Post by shyce on 2009-07-17
Does setting Visual Effects to "None" in Appearance turn off compiz and switch to metacity?

---

### Post by shyce on 2009-07-17
Does:

```
metacity --replace
```

persist through restarts?

---

### Post by Bölvaður on 2009-07-17
> **shyce said:**
> Does setting Visual Effects to "None" in Appearance turn off compiz and switch to metacity?
yes

---

### Post by shyce on 2009-07-17
> **Bölvaður said:**
> yes

You sure? I've had visual effects off for a while and it was always doing this. Then I ran "metacity --replace" in terminal and the pointer acts as expected. 

I'm still not sure if "metacity --replace" persists through restarts however, or if I need to "set" it as the default somewhere.

---

### Post by mgmiller on 2009-07-17
Actually, the choices to go back and forth are in the menu system, they're just not turned on by default.

Right click Applications and select Edit menus.
On the left side, click to select "Other".

On the right side, look for the entries for Compiz and Metacity.

The one for Compiz is ok by default, just put a check mark in its box.

The entry for metacity needs to be edited slightly.
right click it and select Properties.

The entry in the Command: box should look like this:
```
metacity --replace
```

Click Close and then put the check mark in the box.

Close the menu editor.

If the entries are not immediately visible, log off and back on, then you will see them.

That's how I do it.  Before running ut2k4, I click on metacity and after, I click on compiz.

---

