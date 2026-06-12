---
title: "Adding more &quot;image editors&quot; in Hardy Heron?"
date: 2008-08-03
forum: Desktop Environments
---

### Post by boutell on 2008-08-03
Hi,

I'm running Hardy Heron with the stock Gnome desktop.

I use f-spot to manage photos. It works well but there are certain editing operations on photos that I do a lot. So I'd like to automate those. 

I wrote suitable scripts and made them executable so that they could be run in the same way that f-spot runs, let's say, The Gimp. That is, they accept a filename on the command line, and they do the transformation on that file and save it again before exiting.

Now, how do I tell f-spot and the rest of the Gnome environment that these scripts are image editors, so that they will show up in f-spot's right-click menu and the desktop's "open with" menu, etc.?

Once I know how to do that, I'll be able to just right-click and pick the transformation I want rather than tediously doing the transformations in The Gimp.

I'd like to do this in a way that is per-user rather than jamming them into system-wide files that are probably being managed for me by Ubuntu.

Thanks!

---

### Post by mcduck on 2008-08-04
Right-click on one image file, select Properties/Open With, and add your script to the list. This should do the trick for the file manager, at least.

---

