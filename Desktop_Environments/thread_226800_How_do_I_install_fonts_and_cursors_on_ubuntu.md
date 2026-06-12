---
title: "How do I install fonts and cursors on ubuntu?"
date: 2006-07-31
forum: Desktop Environments
---

### Post by randell6564 on 2006-07-31
Hi!

I downloaded some fonts and cursors from gnome-look.org

I dont know how to install them.  All the tutorials that I found through google, were installs useing repo's from the terminal.

The fonts package is a .tar.gz and the cursor package is a tar.bz2

When I installed some skins for xmms, I just placed the package into /usr/share/xmms/skins

Is that something that I can do with font and cursor packages?  If so, where do I find these folders in my filesystem?

Thanks!

---

### Post by userundefine on 2006-07-31
System > Preferences > Fonts
System > Preferences > Cursor Selection

---

### Post by randell6564 on 2006-07-31
> **userundefine said:**
> System > Preferences > Fonts
System > Preferences > Cursor Selection

Thanks but there IS no "system>preferences>cursor selection.

Only system>preferences>mouse, and when I go there, there is no reference to installing new cursors.  Same with the fonts.  No reference to installing fonts in system>preferences>font

---

### Post by Uncle Spellbinder on 2006-07-31
> **randell6564 said:**
> Thanks but there IS no "system>preferences>cursor selection.

*system>preferences>cursor selection* does not exist for me either. :-k

---

### Post by randell6564 on 2006-07-31
I should really be clear as to which version of ubuntu I am useing.

Dapper.  Whoo.., THAT was a Bi$%!  I'm exhausted! Need to lay down! Lol!

I'm a newb., That sucks! (exactly just how long can one legitimately claim to BE a newb?), cuz honestly, I've been useing ubuntu for more than a year!

But...ya see., I'm SO use to point-and-click, and NOT having to Google everything that I'm trying to learn, that I guess I just got spoiled.

AND, the killer wine that the wife brings home kinda just makes me want to talk! :P

---

### Post by userundefine on 2006-08-01
> **Uncle Spellbinder said:**
> *system>preferences>cursor selection* does not exist for me either. :-k
Ah, been so long since I installed it I forgot it wasn't default.

```
sudo apt-get install gcursor
```

Then you'll have one.

---

### Post by userundefine on 2006-08-01
> **randell6564 said:**
> Only system>preferences>mouse, and when I go there, there is no reference to installing new cursors.  Same with the fonts.  No reference to installing fonts in system>preferences>font
Sure there is.  Details > Font folder.  Dump your fonts in there.

---

### Post by randell6564 on 2006-08-01
> **userundefine said:**
> Sure there is.  Details > Font folder.  Dump your fonts in there.

AHH! Thank You!

---

### Post by ricesteam on 2006-08-02
Hi,

I tried dumping my fonts in that folder and nothing happens...

I noticed the default fonts has a "pad-lock" icons to them.

Looks like I need to do a sudo cp but I dunno where that Font/ folder is.  Is there security issues with install new fonts? I don't understand.

Please help.

---

### Post by userundefine on 2006-08-02
Alternatively, you can dump them in ~/.fonts.

---

### Post by OrganicPanda on 2006-08-08
Well none of the above suggestions worked for me so I created a new folder in /usr/share/fonts/truetype with pandas-fonts as the directory name then I added:

```

"pandas-fonts" 0 ".dir"

```

To the bottom of the fonts.cache-1 file in /usr/share/fonts/truetype

Now all of the fonts I used to use in windows are working in Inkscape and OpenOffice, I assume it's a system wide font folder that all programs will look in, It's not a pretty way of doing it but it's very organised and it works.

---

### Post by jase21 on 2007-12-09
Thanks buddy

---

