---
title: "Nautilus: cutting long filenames"
date: 2009-09-25
forum: Desktop Environments
---

### Post by TheLumberjack on 2009-09-25
Hi! Nautilus doesn't cut filenames of files when they are too long. Really bad!
How can i fix it?

Thanks!

---

### Post by Minsky on 2009-09-25
Open a terminal window and type gconf-editor. In the left hand pane of the window that opens, go to **apps>nautilus>icon_view**, this will display a list of keys in the large right hand pane.

Right click on **text_ellipsis_limit** and select **Edit Key....** In the small window that opens, click on the value in the large box to highlight it (I think 3 is the default value), and then click on **Edit**. Enter 1 as the value, then click **OK** and **OK** again. Your filenames will be truncated to fit on only one line. I don't know how to further restrict the length of the filename. Hope this helps.

---

### Post by TheLumberjack on 2009-09-26
Hi Minsky, thanks for you answer!
I haven't the key "text_ellipsis_limit" on "apps>nautilus>icon_view", so i tried to add it but it says "this key has no schema" (in the space below).
I've tried INTEGER and STRING as value, but nothing... nautilus doen't restrict filenames.
How can I add the key?

---

### Post by Minsky on 2009-09-27
I'm not 100% sure about this, but from what I can gather, **text_ellipsis_limit** was added to Nautilus v2.23.90. I'm using Jaunty which has v2.26.2 installed, so you may be using an older version of Ubuntu. As far as I can see it, you can either upgrade to a later Ubuntu distribution or you may get away with just downloading and installing the latest Nautilus version for your system from here:- [https://launchpad.net/ubuntu/+source/nautilus](https://launchpad.net/ubuntu/+source/nautilus). Hope that solves it for you.

---

### Post by TheLumberjack on 2009-09-27
Unluckly there isn't a package 2.23 for hardy heron, so i would have to upgrade to intrepid ibex. I hope it is safe!

---

### Post by Minsky on 2009-09-28
Before you do that, try using one of the packages for the later Ubuntu versions and see if that works, you could always upgrade afterwards if it doesn't. If you do upgrade, you may as well go for the current Jaunty version as its stable and if you're using a recent ATI card, then the driver issues seem to have been fixed. You also probably don't need reminding to back up your data first before trying any of the above.

---

### Post by TheLumberjack on 2009-09-28
I tried to install a package for the later ubuntu versions, but it needs some dependencies which aren't in hardy's repositories, so i think the only way is upgrading ubuntu itself.
I'm going to use the autoupgrade to intrepid ibex, maybe after doing that, it will allow me to upgrade to jaunty.
Thanks!

---

### Post by Minsky on 2009-09-29
Just on the offchance, have you enabled the third party repositories in Software Sources? The dependencies that you need may be in there.

---

### Post by TheLumberjack on 2009-09-29
Yes i have enabled them, but for dependecies i mean the same packages installed on my hardy, but later versions... so i would have to upgrade a lot of libraries (manually). I think that result is a partial upgrade to intrepid or jaunty, anyway...
Thanks!

---

### Post by TheLumberjack on 2009-09-30
I've just updated hardy to intrepid ibex and now i can see "text_ellipsis_limit" on gconf-editor. It works perfectly.
It would be nice to set not only lines (height), but also width; anyway i don't want to pretend too muck, so it's really ok!
Thanks again Minsky! Bye!

---

