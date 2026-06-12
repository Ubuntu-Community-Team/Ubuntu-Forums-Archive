---
title: "0dd menu error on custom item"
date: 2009-01-25
forum: General Help
---

### Post by M4rotku on 2009-01-25
Hello all,

I am trying to use Data Crow.  I downloaded it from the site and I am able to run via cl with(in the proper folder): sh datacrow.sh

So far, so good.  However, when I attempted to create a menu launcher for this program, I received the following error:

> Could not launch menu item
Failed to execute child process "/home/joey/System/datacrow/datacrow.sh" (Permission denied)

Does anyone know why I am getting this.  Note, when making the launcher I navigated to the datacrow.sh.  I don't know if this is significant or not, but since it works from the terminal I'm just wondering if I directed the shortcut to the wrong thing.

I guess I could try to put sudo in front of the launch command, but I want to use this program as a regular user.  The sh file is within my home directory, so I shouldn't have to sudo.

Any help?

much thanks,
M4rotku

---

### Post by M4rotku on 2009-01-25
Another, maybe unrelated, problem is with Data Crow itself.  I'm running it using the .sh executable while everything else is telling me that I'll need to use the .jar executable and specify an installation directory.  Does this make a difference?

---

### Post by Aearenda on 2009-01-25
You'll probably find the script just starts the .jar file with the appropriate folder.
Try doing this at a command line:
```
chmod u+x /home/joey/System/datacrow/datacrow.sh
```
Then try to start it from the menu again.
If this doesn't work, please post the output from ```
ls -l /home/joey/System/datacrow/datacrow.sh
```

---

### Post by M4rotku on 2009-01-25
Ok, i changed the permissions as said and now i don't get the error message, but it still doesn't work.  I click on it and it does nothing.  However, it still works when run from the terminal.  Here is the output of the command you gave me:

> joey@joey-laptop:~/System/datacrow$ ls -l /home/joey/System/datacrow/datacrow.sh
-rwxr--r-- 1 joey joey 32 2007-09-25 20:37 /home/joey/System/datacrow/datacrow.sh


---

### Post by Aearenda on 2009-01-25
When you run it from the command line, do you always cd into that directory first, so that it is current? What happens if you do these two commands:```
cd
System/datacrow/datacrow.sh
```

EDIT: On reflection, it sounds like you need to create a small script which does this:```

#!/bin/bash 
# Script to start Datacrow from menu

cd /home/joey/System/datacrow
sh datacrow.sh
```
Try calling this from the command line first, without cd'ing into the folder manually.
If it works then change the menu launcher so it runs this script.

---

### Post by M4rotku on 2009-02-03
Thanks, that worked.

---

