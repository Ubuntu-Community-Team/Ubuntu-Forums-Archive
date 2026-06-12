---
title: "ImageJ install"
date: 2009-06-03
forum: General Help
---

### Post by kedmond on 2009-06-03
I installed ImageJ using apt-get.  So I just typed:

sudo apt-get install imagej

This worked well, but there are no plugins.  I copied all my plugins into /usr/share/imagej/plugins/.  These load now.  I also have a .imagej directory in my /home directory.  It has plugins and macros in it, but I do not know how to make ImageJ use those instead.  No big deal.

The one problem I am having so far is with updating ImageJ using the built-in plugin.  Plugins > Utilities > Update ImageJ...

The option downloads the latest version, and then quits, but the command-line says "/usr/bin/imagej: line 495: : No such file or directory"

How do I fix this?  Thanks.

-Kedmond

---

### Post by nekrum on 2009-07-29
Hi I fix it just saving the new ij.jar in the /usr/share/java directory.
I hope this could help you.

---

### Post by kedmond on 2011-01-06
Thanks for the help.

I ended up just running ImageJ as root, and then I can update it normally.  Works well.

> **nekrum said:**
> Hi I fix it just saving the new ij.jar in the /usr/share/java directory.
I hope this could help you.

---

