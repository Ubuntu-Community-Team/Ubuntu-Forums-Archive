---
title: "Icons and cursor are very small in some of my applications"
date: 2021-03-11
forum: Desktop Environments
---

### Post by garnold on 2021-03-11
I'm not sure why but when running some applications the app icons and the cursor is very small. I mean, super tiny. The cursor is really small when in the app but once I move it out of the app it goes back to normal size. I notice this in the following apps.

gimp
0 AD
KolourPaint
Udemy (the app not the website)

Not all apps are like this, just some.

---

### Post by &amp;KyT$0P# on 2021-03-14
What desktop environment are you using?
How have you installed the affected apps?  Did you install them as deb packages, or flatpaks, or snaps, or ...?

---

### Post by garnold on 2021-03-14
I'm running the out of the box Gnome desktop. All the apps listed where installed via the Ubuntu app program. The odd thing is that other apps that have been installed via this method are looking great!

---

### Post by &amp;KyT$0P# on 2021-03-14
> **garnold said:**
> All the apps listed where installed via the Ubuntu app program. 

That could be any of the 3 package types I mentioned.

If you have GIMP installed as a deb, this Terminal command should list it -
```
dpkg-query -W | grep -F -i gimp
```

If it's a flatpak -
```
flatpak list --app | grep -F -i gimp
```

I don't know the one for snap, as I don't use snapd. :|

---

### Post by garnold on 2021-03-15
Neither of your commands returned anything. I ran a command snap list and I did see gimp in that list. I uninstalled gimp from the Ubuntu app store and installed in via apt but still have the little fonts. Does anyone have any ideas what's up here?

---

### Post by ActionParsnip on 2021-03-29
Great share and glad you got sorted. Please remember to mark as solved

---

