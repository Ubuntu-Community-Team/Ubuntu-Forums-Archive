---
title: "nautilus launcher"
date: 2005-03-30
forum: Desktop Environments
---

### Post by nix4me on 2005-03-30
Hi,

 I am trying to place a launcher on the launch bar that starts nautilus with root privledges.  I cannot seem to make it work.
 
I am trying this:

gksudo nautilus --no-desktop --browser

Anyone have any ideas?
 
Mark

---

### Post by TravisNewman on 2005-03-30
make it look like this:
gksudo "nautilus --no-desktop --browser"

That's what mine is. The quotes are your friends ;)

---

### Post by nix4me on 2005-03-30
That did it, thanks.

---

