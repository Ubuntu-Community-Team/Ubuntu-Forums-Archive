---
title: "Desktop Icons Problem"
date: 2009-04-05
forum: General Help
---

### Post by Rickles65 on 2009-04-05
My wife was doing a bit of "customizing" of her desktop. Using the properties option for several of the icons, she changed them to another folder icon for example.

Now she doesn't like what she's done and wants to go back to the Human-Clearlooks set that's part of the default theme. OK, so I change the theme to something else and then back to Human-Clearlooks. The icons she changed via the properties dialog are not changing when the them changes...

How can I do a full reset of her desktop preferences? I figured sure as hell changing the them would do it but it didn't.


Thanks in advance!

---

### Post by _Purple_ on 2009-04-05
Go to System > Preferences > Appearance

In Theme tab, click Customize.

In Icons tab, select Human.

---

### Post by Rickles65 on 2009-04-05
That was the first thing I did (referenced above), that doesn't reset them nor does a full theme change.

i.e. if you manually change a folder icon via right click > properties and change it on the first tab the theme no longer controls the icon.

---

### Post by _Purple_ on 2009-04-05
Try deleting your ~/.gnome2. Its better to make a backup of the file before deleting. Some settings might get rest. 
Then log out and login back again.

---

### Post by Rickles65 on 2009-04-05
Ack! Nope, that didn't work either. Hmmm, I wonder if there's a conf for each user located elsewhere?

It only affects her login on the machine, so maybe this particular pref is kept elsewhere?

---

### Post by rotwang888 on 2009-04-05
If you select properties for an item with a custom icon, clicking the image, then clicking "revert" will change it back to the standard icon.  This might be a pain if there are many of them, but it should work.

---

### Post by Rickles65 on 2009-04-05
Jeebus! That took a bit of digging... finally decided to grep all the files for one of the icon names. 

When the icon pref is changed via the link properties (right click > Properties > Basic tab) it then becomes part of Nautilus configs in .nautilus.

You can either edit the xml file to manually set it or delete them and then logout and back in resetting them globally for that users login. :guitar:

---

### Post by Rickles65 on 2009-04-05
> **rotwang888 said:**
> If you select properties for an item with a custom icon, clicking the image, then clicking "revert" will change it back to the standard icon.  This might be a pain if there are many of them, but it should work.

Oh yeah *now* he posts :lolflag:

Thanks! Will remember that next time! At least I found a global way to do it too... 

The wife loves changing her icons. Can't get her to just switch them via the theme manager.

):P

---

