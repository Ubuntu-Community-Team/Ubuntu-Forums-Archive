---
title: "Open a terminal and run a script from launcher"
date: 2009-02-08
forum: General Help
---

### Post by jpaulb on 2009-02-08
I would like to open a terminal with the gnome launcher and have a script of mine run in that terminal.

I have the first part opening the terminal figures out just gluing the other script to it eludes me.

---

### Post by grndslm on 2009-02-08
Use the ln command to create a symbolic link from /usr/bin/scriptName to the path of your script...  or just mv it there.  That should be half the trick right there if it doesn't automatically open gnome-terminal up to do that from the gnome launcher.

---

### Post by jpaulb on 2009-02-17
> **grndslm said:**
> Use the ln command to create a symbolic link from /usr/bin/scriptName to the path of your script...  or just mv it there.  That should be half the trick right there if it doesn't automatically open gnome-terminal up to do that from the gnome launcher.


Thanks.

---

### Post by mikewu on 2009-02-17
If that doesn't work, you might want to try the -e or -x flags.

```
-e, --command=STRING
                 Execute the argument to this option inside the terminal.

-x, --execute
                 Execute the remainder of the command line inside the terminal.
```

And just change the launcher command to to include those flags.

---

### Post by geirha on 2009-02-17
You could set the command to:
```
gnome-terminal -e "/path/to/script"
```

---

### Post by jpaulb on 2009-02-18
Thanks 
now it works

---

