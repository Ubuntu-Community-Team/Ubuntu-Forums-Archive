---
title: "Nautilus: No &quot;View as image collection option&quot;"
date: 2005-03-28
forum: Desktop Environments
---

### Post by swerner on 2005-03-28
I remember a while ago, not long after I first installed Ubuntu there was a "View as image collection" option when I was viewing a folder with many jpegs in it.  Now I don't have that option anymore, all I get is "view as list" or "view as icons". This has been annoying me for a while, and today I removed all my .gnome* .gconf* folders for a fresh start.  But  still no "view as image collection" option.

btw, I'm not using spatial nautilus, I switched this off via the GConf Editor (apps->nautilus->preferences->always_use_browser=false).
But it makes no difference what I choose.

Does anyone have any ideas?

Cheers.

---

### Post by oracledarren on 2005-03-28
This still works for me.  How big are the image files ?

The reason I ask is in SYTEM->PREFS->FILES MANAGEMENT under the preview tab there is an option that sets to max filesize for previews to work correctly  ;-)

---

### Post by swerner on 2005-03-31
I've upgraded to Hoary and still there's no "View as image collection" and my image sizes are not too big, about 1 MB on average. The size limit for previewing local images is 5 MB.

---

### Post by darrenadams on 2005-03-31
The reason that you can't see that option anymore is that the program responsible for supplying the "View as Image Collection" item (Eye of Gnome) doesn't provide that option anymore. If you need it, you can either use Eye of Gnome directly (called "Image Viewer under the Graphics menu in Gnome), or another program for viewing your image collection, such as gThumb or GQView

---

### Post by swerner on 2005-10-02
That's a shame.  I really liked that feature, I have just upgraded to Breezy and check to see if it there, but alas it's not :(.

---

