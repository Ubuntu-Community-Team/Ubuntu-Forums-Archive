---
title: "Execute Command in Terminal Through Shortcut"
date: 2006-09-07
forum: Desktop Environments
---

### Post by Inhumane on 2006-09-07
I'm configuring Steam right now and all, but I need to open Terminal and type in ```
cd ~/.wine/drive_c/"Program Files"/Valve/Steam/
``` and then ```
WINEDEBUG="fixme-all" wine steam.exe
```, is there a way to make a shortcut and tell the shortcut to first launch terminal and then input those commands in for me?:-k

---

### Post by pyros on 2006-09-07
> **Inhumane said:**
> I'm configuring Steam right now and all, but I need to open Terminal and type in ```
cd ~/.wine/drive_c/"Program Files"/Valve/Steam/
``` and then ```
WINEDEBUG="fixme-all" wine steam.exe
```, is there a way to make a shortcut and tell the shortcut to first launch terminal and then input those commands in for me?:-k
I suppose you could use the command
```

cd ~/.wine/drive_c/"Program Files"/Valve/Steam/ && WINEDEBUG="fixme-all" wine steam.exe
```
in the launcher and check the box to run in terminal?

---

### Post by Inhumane on 2006-09-07
It doesn't work :( it briefly launches the console and then shuts it down

---

### Post by Paul133 on 2006-09-07
Well, you could try a bash script I guess...

---

### Post by Inhumane on 2006-09-07
How do I do that?

---

### Post by pyros on 2006-09-07
> **Inhumane said:**
> How do I do that?
basically,
type this:
```

#!/bin/bash 
cd ~/.wine/drive_c/"Program Files"/Valve/Steam/
WINEDEBUG="fixme-all" wine steam.exe

```
in a text file. Try naming it something like script.sh
I think doing that will give you the option of display or run when you open it. but I think you are going to get the same result.

---

### Post by Inhumane on 2006-09-08
Doesn't work either :mad: it opens up gedit, and if I tell it to open it with Terminal it just loads for a few seconds and then nothing happens. Anyone else?

---

### Post by TyphoonJoe on 2006-09-08
make sure the script has its mode set to executable.

From the command line enter:
chmod a+x script.sh

Then run:
 ./script.sh 

From the command line and see if that works.  If this does not work, please post any error message you get back from the command line.

---

### Post by Inhumane on 2006-09-08
Typing those in launches it fine, how do I set the .sh file to be an executable?

---

### Post by pyros on 2006-09-08
> **Inhumane said:**
> Typing those in launches it fine, how do I set the .sh file to be an executable?
The short answer is: that's done in the filesystem-- either from a terminal (as has been previously explained) or by right-clicking on the file, going to properties, and checking "execute" on the permissions tab.

---

