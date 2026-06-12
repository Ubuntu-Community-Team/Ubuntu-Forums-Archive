---
title: "Incorrect Mouse Cursors in Firefox and Thunderbird"
date: 2005-10-13
forum: Desktop Environments
---

### Post by Watter on 2005-10-13
I have did a clean install of Breezy today (AMD64) and while most things are fairly nice, there are a few issues. One of them is that in Firefox and Thunderbird, the mouse cursors switch away from the Ubuntu Human theme to the basic X cursors (i.e. black pointer, sideways hand over links, etc.). I initially though that perhaps this was a GTK issue, however the same problem doesn't occur with Synaptic or OpenOffice. Both of those apps correctly use the mouse cursors specified KDE's System Settings.

I tried to run the downloadable versions of these apps (i.e. from Mozilla's site as opposed to "apt-get install firefox"), but I seem to be missing some libraries. I suspect this is due to my being on AMD64. The erro indicats that I'm missing libxp.6.so however I do have that librarby installed. I think it's looking for the 32bit version of that library, though. Installing ia32-libs-gtk didn't help.

Any ideas?

---

### Post by mlomker on 2005-10-13
I haven't seen that, exactly.  Have you installed gtk2-engines-gtk-qt yet?  It forces gtk apps to use your KDE theme.

---

### Post by monkey89 on 2005-10-13
I had the same issue myself.  I worked around it by setting the default cursor theme on the system to kubuntu.  Create /usr/share/icons/default/index.theme (the default directory won't exist at first) with this:

[Icon Theme]
Inherits=kubuntu

Log out of KDE, and you might need to restart X, but then all apps should have the kubuntu (default) mouse theme.

-Monkey

---

### Post by Watter on 2005-10-14
Thanks, Monkey 89. That worked, however, I do wish there as a way to make it a little more seamless and have the icons change for all apps when they were changed in the KDE settings. 

I always have to think about these things because I setup and maintain several Ubuntu/Kubuntu installations for friends and family, and while I have no problem doing what you suggested every time I change my icons (which isn't often, I guess), there's no way I could have expected the others to have done so. 

That's one of the reaons I I've liked Ubuntu/Kubuntu int he past; things just worked. Unfortunately, Breezy has been far less polished than previous releases for me. I have three other significant "polish" issues yet to address, and there all just as annoying as this one unfortunately.

---

### Post by GoldBuggie on 2005-10-14
Thanks for this fix...it annoyed me alot. Now lets hope some other things get their way into fix soon.

---

### Post by ghoshe on 2005-10-18
I noticed that you can change the "inherit" variable with any cursor theme installed in the system.

[IconTheme]
Inherits=PolarCursorTheme

PD: very good theme ;) see it in kdelook.org

---

### Post by Navyblue on 2005-10-18
I have this same problem on both 32 bit and 64 bits version.

---

### Post by tapple on 2005-10-27
I had this issue when I upgraded to gtk+ 2.8.6. downgrading to gtk+ 2.6.10 solved the problem for me.

---

### Post by AndEat on 2005-11-02
[QUOTE=monkey89]I had the same issue myself.  I worked around it by setting the default cursor theme on the system to kubuntu.  Create /usr/share/icons/default/index.theme (the default directory won't exist at first) with this:

[Icon Theme]
Inherits=kubuntu

Log out of KDE, and you might need to restart X, but then all apps should have the kubuntu (default) mouse theme.

-Monkey[/QUOTE]
I tried this; didn't work. Tried several variations, still no luck. Any suggestions?

---

### Post by obibok on 2005-11-10
Just to bump this one up...

Another simple way to set the Kubuntu themed mouse cursor in Firefox (and possibly other apps where it would appear different):

```
cd /usr/share/icons
sudo ln -s kubuntu default
```

---

### Post by xMetaRidley on 2006-01-04
[QUOTE=monkey89]I had the same issue myself.  I worked around it by setting the default cursor theme on the system to kubuntu.  Create /usr/share/icons/default/index.theme (the default directory won't exist at first) with this:

[Icon Theme]
Inherits=kubuntu

Log out of KDE, and you might need to restart X, but then all apps should have the kubuntu (default) mouse theme.

-Monkey[/QUOTE]

Thank you, I had this problem after upgrading X.org to 6.9 and this fixed it.

---

### Post by Tosa on 2006-01-05
I have the same problem with Firefox, but neither method fixed it... :(

---

### Post by louis_nichols on 2006-01-09
ghoshe's solution fixed it for me, although not perfectly: I still se the X cursors qhile the app is loading and even when pages are loading :( and for a brief moment while hovering over some widgets. Should't it all be more simple and out-of-the-box, though?

---

### Post by obibok on 2006-01-24
Note that incorrect/generic appearances of mouse cursors ](*,) are often a result of the actual cursor themes being incomplete. These things are quite confusing as apparently there isn't any real coherent, standardized naming convention for X cursors. So, naming/linking files to cover all bases (KDE, GNOME, GTK1, etc.) is not an easy task. Read [this]("http://jmoiron.net/rant/?id=235") for some introductory info, if you're interested... :-\"

The best idea after installing a new mouse theme is to point to its directory in **~/.icons/default/index.theme**

Example:

```
[Icon Theme]
Inherits=*ComixCursors-White-Large*
```

---

