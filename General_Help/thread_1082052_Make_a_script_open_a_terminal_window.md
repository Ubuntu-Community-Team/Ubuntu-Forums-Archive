---
title: "Make a script open a terminal window"
date: 2009-02-27
forum: General Help
---

### Post by theresonant on 2009-02-27
Hello all!

I've written a script which backups some specific folders of mine everytime I start the Apache Server. Works great, just that I'd like to actually see what it is doing and when it has finished working. I thought the best way for that would be to make my script open a terminal window, echo everything in that terminal, and when it's done, close it.

I want something like:

```

#!/bin/sh

##...command to open a terminal window

zip ./mybackuparchive ./myfolder
echo "My Folder has been zipped."

zip ./myotherarchive ./myotherfolder
echo "My Other Folder has been zipped."

##...command to close terminal window, if it doesn't close by itself at the end

```

I hope I explained myself properly. Any ideas, pls?

---

### Post by smani on 2009-02-27
You could create a launcher script, such as
```

#!bin/bash
gnome-terminal -x myscript.sh

```

---

### Post by sisco311 on 2009-02-27
```
gnome-terminal -x /path/to/script
``` ;)

EDIT: uh. i'm slow.

---

### Post by theresonant on 2009-02-27
Thanks guys! That did the trick. Now... the terminal window closes itself when everything is done. But can I sometimes prevent that? I tried adding a & at the end of the line, like 

```

gnome-terminal -x ./myscript.sh &

```

but that didn't keep the terminal open. Anyway, this would be just like the cherry on the top of the cake.

---

### Post by Simian Man on 2009-02-27
Change the script to this:
```
#!/bin/sh

##...command to open a terminal window

zip ./mybackuparchive ./myfolder
echo "My Folder has been zipped."

zip ./myotherarchive ./myotherfolder
echo "My Other Folder has been zipped."

##...Press enter message
echo "Press enter to continue"
read dummy
```

Then you can press enter to close the window.

---

### Post by theresonant on 2009-02-27
Great! Thanks!

---

### Post by smani on 2009-02-27
Well I guess you would like something like: "Press a enter to continue...", you could achive this by adding to the end of the script you call as argument:
```

...
echo "Press enter to continue...";
read confirm;

```
There are also more elegant ways clearly (this just makes the script wait for user input).

Edit: anticipated...

---

