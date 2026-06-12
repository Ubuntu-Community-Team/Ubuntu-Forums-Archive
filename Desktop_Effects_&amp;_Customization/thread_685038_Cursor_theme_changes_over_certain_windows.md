---
title: "Cursor theme changes over certain windows"
date: 2008-02-01
forum: Desktop Effects &amp; Customization
---

### Post by Thorning on 2008-02-01
I have a problem with displaying cursor themes. I have no problem in selecting a cursor theme (using sys -> pref -> appear -> customize. It loads just as it should.

However it's only displayed when I move the cursor over spaces like boxes or the display window in mozilla (html) or over plain text etc etc.
But when I hover over graphics like window titlebar, desktop or applications like AWN the cursor reverts back to the "white", default theme.

Any suggestions?

I cannot use gcursor becouse of this bug (which I can't find a solution for):
[https://bugs.launchpad.net/ubuntu/+source/gcursor/+bug/138491]("https://bugs.launchpad.net/ubuntu/+source/gcursor/+bug/138491")

---

### Post by Fraktyl on 2008-02-02
If you're using Compiz, install the settings manager
[FONT=monospace]
```

sudo apt-get install compizconfig-settigns-manager
```[/FONT]

Open this, and click the general tab.  There should be an option for mouse theme.  Type in the name of the mouse theme you're using.  It should use that over all windows now.

---

### Post by Zero Prime on 2008-02-03
Or, if there is a theme name listed in the general section you can delete that name.  You have to restart X for the changes to take affect.  You will then have the cursor theme that you selected.

---

