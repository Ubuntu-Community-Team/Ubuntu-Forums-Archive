---
title: "Nautilus Freezes when folder contains *.svg files"
date: 2011-09-13
forum: Desktop Environments
---

### Post by cwarner7_11 on 2011-09-13
I have recently encountered a problem where Nautilus freezes when I open a folder containing *.svg files created with Inkscape Version 0.47.  This happens whether I start Nautilus with the "Places" menu or from the command line.  No error messages are presented on the command line.  The files in question can be opened from the original program that created them, and using the ls command I get a complete list of the files.  System specifics:

Ubuntu 10.04 (64 bit)
Gnome 2.30.2
Nautilus 2.30.1
Kernel 2.6.32-33-generic

I have searched the forums and bugs and find nothing that can tell me where the problem lies.  

Any suggestions?

---

### Post by cendo on 2011-09-19
I have the very same problem of freezing Nautilus on folder with SVG files. I haven't found better solution than turning of preview for all images, but thats not enough for me.

Does anybody know of a solution?
thanks
peter

---

### Post by Copper Bezel on 2011-09-19
There's an active bug for this in Launchpad - [_here_]("https://bugs.launchpad.net/ubuntu/+source/librsvg/+bug/305546") - although it seems to have been resolved in Natty. I didn't realize that there had been any recent activity, so I thought perhaps it was unrelated the first time I saw this topic. There was a workaround in a previous version of Nautilus, but it doesn't seem available now. Sorry. = (

---

### Post by cwarner7_11 on 2011-09-19
Thanks for the links.  There was a lot of information that confirmed my experiences.  it seems this is an issue specific to Inkscape files with embedded bit maps.  I have not had this problem with Nautilus with other *.svg files, or even *.svg files created in Inkscape without bit maps. Unfortunately, it doesn't seem there is much interest in fixing this for the older distros, and I am not quite ready to update to a newer distro.  So, hiding the offending files in their own folder seems to be the only viable work around for my situation.

---

