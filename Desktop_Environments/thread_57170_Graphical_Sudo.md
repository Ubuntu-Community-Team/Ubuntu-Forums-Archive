---
title: "Graphical Sudo"
date: 2005-08-15
forum: Desktop Environments
---

### Post by Sephiriz on 2005-08-15
I have a very basic script that calls up another script, sorta acting like a shortcut:

```

#!/bin/sh
cd /usr/bin;
sudo sh peer.sh;

```

Of course, this will only work if I run it in the terminal, but I know that GNOME has a graphical password input command, or at least I think it does.  Could anyone tell me how to implement that in this script?  I'm just curious, since I'd like my peer.sh to run without a terminal constantly open in the background.

---

### Post by PeP on 2005-08-15
gksudo

---

### Post by Sephiriz on 2005-08-15
Does that instantly get passed on to the script?  So if I simply replace sudo with gksudo, the script is supposed to run fine?  I just attempted that, and it didn't seem to work.  Do I need to somehow pass something along to the script?

---

### Post by PeP on 2005-08-15
RTFM:> 
 Note that <command> and all its arguments should be passed as one single  argument  to  gksu  just
       like one would to when using su.


then you have to write

> #!/bin/sh
cd /usr/bin;
gksudo "sh peer.sh"

---

