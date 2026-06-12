---
title: "yes, another remote xterm display thread..."
date: 2010-10-21
forum: Desktop Environments
---

### Post by mr_manny on 2010-10-21
Under 9.04, I've updated the gdm.conf...to enable remote xterm DISPLAYS.

---------------------------------------------------------------------
cd /etc/X11/gdm/

vi gdm.conf

uncomment the line that has DisallowTCP=true and change to =false
save and exit
restart X
---------------------------------------------------------------------

Now that I'm on 10.04, the above is no longer an option.

the only thing that's changed in my env. is my box...

Is anyone familiar w/what config needs to be updated to allow for remote xterm Sessions?

any assistance would be appreciated,
manny

---

