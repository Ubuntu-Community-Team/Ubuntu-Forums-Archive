---
title: "Different wallpapers on each desktop"
date: 2010-09-10
forum: Desktop Environments
---

### Post by chip616 on 2010-09-10
Being able to have a different background wallpaper on each virtual desktop is a snap in KDE 3.5.  I have not found a way to do this in KDE4.x.

I have found threads here asking similar questions, but they went unresolved.  Is this feature no longer available?  Or does anyone know how to enable it?

I can right click the desktop and select a different wallpaper, but this then applies to ALL desktops, not just the one I want to modify.

I am using Kubuntu 10.04.

Thanks.

Frank.

---

### Post by lykwydchykyn on 2010-09-11
I can't remember if this can be done in KDE 4.4, but if you update to 4.5 from the Kubuntu PPA (see instructions on Kubuntu.org), you can do this.

What you actually have to do is have separate Plasma activities on each desktop; this means you have separate wallpapers and widgets as well (except panels show up on all desktops).

In KDE 4.5 the option is a checkbox on the "Virtual Desktops" settings page.  It says "different widgets on each desktop".

---

### Post by chip616 on 2010-09-11
lykwydchykyn:

OK, I'll give that a try tomorrow.  I wondered how 10.04 LTS was going to keep current with the rapid pace of development in KDE 4.x.  I'll add the PPA and update tomorrow and get back to you.

Thanks.

Frank.

---

### Post by schnelle on 2010-09-11
Go to System Settings/Desktop/Multiple Desktops and check "Different activity for each desktop" option.

---

### Post by chip616 on 2010-09-11
schnelle:

This appears to work just fine in KDE 4.4.2.  Thank you for the kind help!  I moved the jpg images I wanted to use to /usr/share/wallpapers (the default location) as root, and they were there when I wanted to use them.

Now I need to poke around and find out how to add icons to launch programs in each of my 6 virtual desktops.  I understand that KDE4 allows a different set of icons for each desktop 'activity'.  Now I have to learn how to make it work.

Frank.

---

### Post by schnelle on 2010-09-11
Unlock your widgets and then you should be able to add widgets (including icons) independently for each virtual desktop.

---

### Post by chip616 on 2010-09-11
Schnelle:

I have the widgets unlocked.  I don't see how to add an icon for, say, Dolphin, to my desktop.  In the KMenu tree, I navigate to Dolphin, right click, and there is an option to "add to desktop".  I click that, but nothing happens.  Add to panel works.

Frank.

---

### Post by schnelle on 2010-09-12
> **chip616 said:**
> Schnelle:

I have the widgets unlocked.  I don't see how to add an icon for, say, Dolphin, to my desktop.  In the KMenu tree, I navigate to Dolphin, right click, and there is an option to "add to desktop".  I click that, but nothing happens.  Add to panel works.

Frank.

Just drag and drop icons from kmenu to the desktop. This way it works for me :D .

---

### Post by chip616 on 2010-09-12
schnelle:

That works in KDE 3, but not in 4.  At least, not with the selection of different activities for each desktop it doesn't.

I should start a new thread on this anyway.

Thanks.

Frank.

---

### Post by schnelle on 2010-09-12
Drag and drop works for me in Kubuntu Lucid KDE 4.4.5 with unlocked widgets and different activities on each desktop enabled. Anyway, good luck in finding solution. 8)

---

### Post by chip616 on 2010-09-12
schnelle:

I have 4.4.2 and drag and drop does not work.  Right clicking the item in the menu tree allows me to choose 'add to desktop'.  This works, but only on the first desktop.

How did you get 4.4.5?

Frank.

---

### Post by schnelle on 2010-09-12
KDE 4.4.5 is in kubuntu-ppa repository : 

```
sudo apt-add-repository ppa:kubuntu-ppa/ppa 
sudo aptitude update
sudo aptitude safe-upgrade
```

---

### Post by lykwydchykyn on 2010-09-12
If you want icons on your desktop, you have to either:

 - Unlock widgets and add a "Folder View" widget to your desktop
 - Unlock icons, right click your desktop and select "desktop settings".  Go to the "activity" section and change the activity type to desktop.

The first method gives you a region of the screen where you can have desktop icons (by default, the contents of your ~/Desktop folder, like other desktops do).

The second method gives you something more like the traditional desktop, where you can put icons anywhere on the desktop.

This should work in either 4.4.2 or 4.5.

---

