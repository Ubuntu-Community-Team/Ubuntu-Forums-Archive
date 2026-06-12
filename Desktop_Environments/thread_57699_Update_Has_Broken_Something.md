---
title: "Update Has Broken Something"
date: 2005-08-17
forum: Desktop Environments
---

### Post by mickc1303 on 2005-08-17
I noticed on my status bar in the top right that there were several updates available for Ubuntu (Just installed yesterday).

There was a warning when the upgrade finished unfortunately I didn't take not of it but saw it was relating to mozilla firefox.

I just went into Synaptic and it warned me that there was 1 broken package, which is listed as:

mozilla-firefox-gnome-support 1.0.6-1ubuntu1~5.04upb1 1.0.6-1ubuntu1~5.04upb1 dummy transitional package.

As firefox seems to be working well I just left this as it was.

I then attempted to install mozilla-thunderbird 1.0.6-0ubuntu5.04 to which the following message appeared:

"The chosen action also affects other packages.  The following changes are required to proceed.

To be removed>
mozilla-firefox-gnome-support
ubuntu-desktop

I cancelled the installation as the removal of ubuntu-desktop doesn't seem to be a wise idea.

Can somebody suggest a fix for this bearing in mind that I'm a total n00b basically when it comes to linux/ubuntu.

TIA

---

### Post by woedend on 2005-08-17
i always have gotten error messages when installing firefox...for some reason if i just try 2 or 3 times it finally works.  It appears it has selected to remove firefox gnome support in synaptic.  first, unselect thunderbird.  then in the bottom left click custom, then select broken from the list.  this lists the broken packages...try doing a reinstall.  If you still can't get it...just for a note.  Ubuntu-desktop is not ubuntu.  It's like a mapping file of packages in ubuntu...theoretically you could use ubuntu without it.

---

### Post by mickc1303 on 2005-08-17
I did as suggested and all works fine now :)

Thanks for your prompt reply.

---

