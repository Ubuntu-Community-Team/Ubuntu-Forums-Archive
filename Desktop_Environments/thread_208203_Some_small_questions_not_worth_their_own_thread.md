---
title: "Some small questions not worth their own thread"
date: 2006-07-03
forum: Desktop Environments
---

### Post by HAARP on 2006-07-03
Hi there,
I've got some small questions/issues I've collected which I wanted to resolve. Making 10 new threads for it just isn't worth it ;)
Some things aren't important tho.

1. Is it possible to extract Icons from Win .exe files with Ubuntu? **-solved**

2. Is it possible to set a global mousewheel speed?

3. k3b seems to be the best cd burning software out there right now. Can it run on Gnome? **-solved**

4. When i press alt+f2 i get the "Run application" screen. However, when I type gksu, i strangely get the Ethereal icon. Is something messed up with the icons?

5. In synaptic, is it possible to automaticly open the list of downloads when installing/updating as well as the terminal when packages are set up?

6. When I try to drag'n'drop out of File-Roller into some other place, it immediately stops after i release the mousebutton. I have to try it several times in order to get File-Roller to extract without me "holding hands"

7. Also File-Roller seems to be unable to open password-protected files.

```
7-Zip (A) 4.30 beta  Copyright (c) 1999-2005 Igor Pavlov  2005-11-18
p7zip Version 4.30 (locale=en_US.UTF-8,Utf16=on,HugeFiles=on)

Processing archive: /media/hdb1/Backups/mp.7z

Enter password:
Error: /media/hdb1/Backups/mp.7z is not supported archive

```

Of course it's not supported, File-Roller doesn't even ask for a password and the menu item is greyed out so it won't even transmit a password to the command-line utility...
Happens with all pw-protected files, not only 7z.

8. For the console, does a command exist which clears the screen, just like **cls** on Winblows? **-solved**

9. How can I change the buffer of the commandline? Right now, I'm just able to scroll up a few pages, but that's about it. ( I mean tty1-6, not the Gnome-Terminal)

10. In nautilus, when right clicking on files/folders, is it possible to have a command which copys the file's path into the clipboard?

11. Also, nautilus is awfully slow when trying to show big directories like /usr/bin. I guess he's scannning every file for it's header to determine it's type? Can you switch this off?


Whew, quite a list. Hope someone can answer some of them :) Thanks!

---

### Post by bartbes on 2006-07-03
3) Gnome programs run in KDE and KDE programs run in Gnome, just one thing.. the graphics..
4) I have the same, doesn't hurt (or does it?)
8 ) It's easy (I didn't know either for a long long while) it's ```
clear
```
11) I haven't got an answer to that, but I think it is always that way..

---

### Post by pepolez on 2006-07-03
Damn, beat me to the only ones I knew :P I'll have a look around for some answers

---

### Post by HAARP on 2006-07-03
You guys are great. 4 minutes after I posted, I get the first answers. Can't compare any commercial service to that \\:D/ 



[QUOTE=bartbes]4) I have the same, doesn't hurt (or does it?)[/QUOTE]
Nah, in fact, I don't even care. Just thought there's something messed up which I should resolve..

---

### Post by bom28 on 2006-07-03
1)install icoutils, it contains command-line programs to do that (wrestool for .exe)
11) in nautilus preferences you can deactivate some previews, maybe it can help

---

### Post by HAARP on 2006-07-03
[QUOTE=bom28]1)install icoutils, it contains command-line programs to do that (wrestool for .exe)[/quote]
Works like a charm, thanks

> 11) in nautilus preferences you can deactivate some previews, maybe it can help
It indeed did help, but that was one of the first things i ever set in Ubuntu ;)

---

### Post by HAARP on 2006-07-05
Ok, now I've come to the conclusion that File-Roller sucks. It doesn't have the functionality I need, it doesn't work with passwords, its slow and buggy.

Is there any other archive-manager front-end which can integrate into nautilus?

Also, 2 and 10 would be important to me. Anyone any ideas?

---

