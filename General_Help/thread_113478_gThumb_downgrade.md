---
title: "gThumb downgrade"
date: 2006-01-06
forum: General Help
---

### Post by kes on 2006-01-06
I have a small but very troublesome with gThumb which I use as a default viewer.  For my work I often have to look through the sequence of images, and now this process is perturbed.

After installation of breezy:
doble-click -> image opens in the window, PgUp/PgDn -> I go through the list;
enter -> switch to the directory _**in the same window!**_
I'm happy!

After the very 1st update:
doble-click -> image opens in the window, PgUp/PgDn -> No reaction! I cannot proceed to the previous/next image in the folder!!!
Alt+end -> opens the directory view in the **NEW** window, so I should return and close the window with the single image (to keep the desktop clean :rolleyes:  ). This is very unpractical and extremely annoying!
In the newly opened window "old-manner navigation scheme" works. But sometimes I have to compare several sequences of images in several folders at the same time... It's a living hell........=(

I couldn't find anything in menu "Options" to solve this problem. Would downgrading of gThumb help me to return to previous settings?

Thank you.

---

### Post by sizzam on 2006-02-14
I'm having the same issues.  Are there any updates on this one?

---

### Post by merlyn on 2006-03-08
I agree that the current behaviour of gthumb, (2.7.x) is annoying.

Having said that this **was** implemented as a 'feature' in order to make using gthumb less confusing! :-k

A [bug]("http://bugzilla.gnome.org/show_bug.cgi?id=325557") has been filed, 'prioritised' as normal, with an severity rating of 'enhancment'. 

One can only imagine that means little if anything is likely to be done, with regard to reversing the 'enhancement'. 

In the meantime I also have attempted to 'downgrade', to the 'unenhanced' version, (2.6.x) but with no success.

Cheers.

---

### Post by jBilbo on 2006-03-13
Same here... annoying :-( nothing like the viewer mode in the browser mode (PageUp/PageDown active).

---

### Post by jBilbo on 2006-03-24
wey it's fixed in upstream right now:

[http://bugzilla.gnome.org/show_bug.cgi?id=325557](http://bugzilla.gnome.org/show_bug.cgi?id=325557)

now waiting to the updated package in dapper.

---

### Post by akshaysrinivasan on 2006-03-25
try going to synaptic and search for gthumb.when you can see the package click on it and select an older version from from Package>Force Version

---

