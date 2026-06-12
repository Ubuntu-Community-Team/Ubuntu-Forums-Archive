---
title: "Openbox theme..."
date: 2012-01-01
forum: Desktop Environments
---

### Post by grobar87 on 2012-01-01
Hi,
Can someone tell me how to remove icons from openbox theme?I really hate icons in top left corner(see screenshot).
Thanks and sorry for my english.
Happy New Year! :)

---

### Post by urukrama on 2012-01-01
You need to configure that in your rc.xml (the general configuration file for Openbox), rather than in the themerc file of the theme you are using.

Look for the following in that file (located in  /home/USERNAME/.config/openbox/rc.xml):

```
 <titleLayout>SLIMC</titleLayout>
    <!--
      avaible characters are NDSLIMC, each can occur at most once.
      N: window icon
      L: window label (AKA title).
      I: iconify
      M: maximize
      C: close
      S: shade (roll up/down)
      D: omnipresent (on all desktops).
  -->
```

Change the letters in the first line to your liking. The above settings are my own, and do not use a window icon (N).

If you have Obconf installed, you can also edit these settings using that application. Look for the settings under the "Appearance" tab.

---

### Post by Elfy on 2012-01-01
Thread moved to Desktop Environments.

---

### Post by grobar87 on 2012-01-01
> **urukrama said:**
> You need to configure that in your rc.xml (the general configuration file for Openbox), rather than in the themerc file of the theme you are using.

Look for the following in that file (located in  /home/USERNAME/.config/openbox/rc.xml):

```
 <titleLayout>SLIMC</titleLayout>
    <!--
      avaible characters are NDSLIMC, each can occur at most once.
      N: window icon
      L: window label (AKA title).
      I: iconify
      M: maximize
      C: close
      S: shade (roll up/down)
      D: omnipresent (on all desktops).
  -->
```Change the letters in the first line to your liking. The above settings are my own, and do not use a window icon (N).

If you have Obconf installed, you can also edit these settings using that application. Look for the settings under the "Appearance" tab.

Yessssss and finaly!!! Thanks a lot man! :)
Happy New Year! :D

---

