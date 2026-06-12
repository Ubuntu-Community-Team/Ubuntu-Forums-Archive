---
title: "Adding Right-Click Actions in Gnome"
date: 2006-04-10
forum: Desktop Environments
---

### Post by bluemike807 on 2006-04-10
Hi, I want to be able to easily compile existing .c or .cpp (or whatever really), by having a simple right-click option in the file browser. 

Is there any easy way I can make this?

---

### Post by adamkane on 2006-04-10
Here is what a basic Nautilus-script template looks like. This script would perform an action on a single right-clicked file. Also see:
[http://g-scripts.sourceforge.net/](http://g-scripts.sourceforge.net/)

This script doesn't work. It's just an example.

Save this as a text file to your desktop with the name compile-c.

```

#!/bin/bash

gcc --compile $1

```

After you save the file to your desktop, move it to the Nautilus-script directory:

```

cd ~/Desktop
mv compile-c ~/.gnome2/nautilus-scripts
sudo chmod 700 ~/gnome2/nautilus-scripts/*

```

Also see Nautilus Actions:
[http://www.grumz.net/index.php](http://www.grumz.net/index.php)

---

