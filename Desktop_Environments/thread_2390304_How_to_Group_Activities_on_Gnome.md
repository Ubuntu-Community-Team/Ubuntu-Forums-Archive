---
title: "How to Group Activities on Gnome"
date: 2018-04-27
forum: Desktop Environments
---

### Post by 7-webmaster on 2018-04-27
I would appreciate some guidance on organizing the list of "activities" that is provided by the Gnome desktop.  As it comes from Canonical there are only two groups, Sundries and Utilities, and the list of activities therefore runs on for several pages.  I just installed JDK 8, which added 7 icons, and Eclipse, which adds an icon for each CDT.  I would like to group those together.  I would prefer a drag and drop UI similar to that used in the Files dialog: right click on the desktop to create a "folder" and then drag and drop or cut and paste to move icons into the "folder". Could someone direct me to a current site with documentation of how to organize these icons?

---

### Post by sevendogsbsd on 2018-04-27
A quick google revealed this:

[https://github.com/BenJetson/gnome-dash-fix](https://github.com/BenJetson/gnome-dash-fix)

No clue if it works, use at your own risk. I have done this manually in stock Gnome a few years ago but it was an enormous P.I.T.A. I would suggest reading the author's documentation and the script(s) to see what they are doing before you run anything. Also, might want to back up your /home directory first, in case the script creates a mess and you have to back out.

EDIT - did a quick read of both the python code and the shell code. The shell code looks like what I did before, manually and the python looks to be interactive. If you speak python :) I would read through it to confirm if there is a way built into the script to back out of the configuration, in case you don't like it. I think there is, but can't guarantee because I am not a python programmer...

---

### Post by thenailedone on 2018-04-28
> **7-webmaster said:**
> I would appreciate some guidance on organizing the list of "activities" that is provided by the Gnome desktop.  As it comes from Canonical there are only two groups, Sundries and Utilities, and the list of activities therefore runs on for several pages.  I just installed JDK 8, which added 7 icons, and Eclipse, which adds an icon for each CDT.  I would like to group those together.  I would prefer a drag and drop UI similar to that used in the Files dialog: right click on the desktop to create a "folder" and then drag and drop or cut and paste to move icons into the "folder". Could someone direct me to a current site with documentation of how to organize these icons?

There seems to be many ways of achieving this (not sure of an automatic way). If you have a look at [https://www.omgubuntu.co.uk/2017/04/add-app-folders-gnome-shell-overview]("https://www.omgubuntu.co.uk/2017/04/add-app-folders-gnome-shell-overview") they mention two more ways of doing so (but please note this post is more than a year old and with newer versions of Gnome-shell your mileage may vary).

I personally don't care for the icons as I am always searching for the apps I want to run, or pinning the ones I use a lot to favorites so they are always front and center.

---

### Post by vanadium on 2018-04-29
Both methods mentioned in the omg ubuntu post should still work fine.

---

### Post by sevendogsbsd on 2018-04-29
Great tip, I didn't know this is now possible in Gnome/Ubuntu software

---

