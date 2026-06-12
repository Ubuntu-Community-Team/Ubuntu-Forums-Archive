---
title: "Compiz Fusion border Tip: Dont close the Terminal"
date: 2007-07-06
forum: Desktop Effects &amp; Customization
---

### Post by murak on 2007-07-06
So I got Compiz fusin working on my Xpress 200M laptop (thanks Vorian!!!) and the "USB stop problem" is now gone, but I noticed that the borders (what to call them, "brown lines above the windows"?) disapered for me. Then I noticed that it was when I closed the terminal that the borders disapered. So, can someone else confirm this?

regards

---

### Post by davobrosia on 2007-07-06
How are you starting Compiz? Do you run "compiz --replace" from a terminal? If so, try running it with Alt+F2.

---

### Post by znaut on 2007-07-06
I had the same problem.  Running from ALT F2 didn't help.

---

### Post by hyperair on 2007-07-07
Run emerald --replace from Alt+F2 after running compiz --replace.

---

### Post by citadin86 on 2007-07-07
After my laptop had an automatic update, compiz fusion wasn`t working.
In the update "list" there were a lot of things with compiz.
now, when I hit Alt+F2, and write compis --replace, I don`t have any bar, aqnd minimize button, and so on.
From my beryl manager, if I select window manager, compiz, I have the oldstyle compiz installed.
I f you need more information, please say so.

---

### Post by hyperair on 2007-07-07
Well don't use the Beryl Manager, because it has no support for Compiz Fusion. I'll assume you installed Compiz Fusion by following Trevino's howto, so run "compiz --replace -c emerald" and post the terminal output here please.

---

### Post by citadin86 on 2007-07-07
> **hyperair said:**
> Well don't use the Beryl Manager, because it has no support for Compiz Fusion. I'll assume you installed Compiz Fusion by following Trevino's howto, so run "compiz --replace -c emerald" and post the terminal output here please.
Firts of all. I tried compiz --replace, and I had no borders. now I wrote compiz--replace into the terminal, and it replied > bb@bb-laptop:~$ compiz --replace/usr/bin/compiz.real (core) - Error: Can't load plugin 'ccp' because it is built for ABI version 20070606 and actual version is 20070706
/usr/bin/compiz.real (core) - Error: Couldn't activate plugin 'ccp':
bb-laptop, being my computer`s name.
Second, I use beryl manager, to jump to metacity, when I have no boerders in compiz.

---

### Post by hyperair on 2007-07-07
Well Compiz isn't loading at all. Make sure you fully upgrade your system. From what I see there, your system's only partially upgraded.

```

sudo apt-get update
sudo apt-get upgrade
```

---

### Post by murak on 2007-07-07
I start compiz with the "compiz --replace" from the terminal, will try Alt+F2 later (working now). Im glad Im not the only one, then the problem surely is going to get fixed sooner or later. Its not like I suffer from this, having the terminal open is not really a problem.

I tried guides for both compiz and beryl before, but it was only with compiz fusion that I managed to get the spining cube done right. This does not mean that only fusion works on my laptop, after all Im new to this.

---

### Post by LouisvilleLIP on 2007-07-07
Assuming that everything with Compiz Fusion is installed properly, type the following at the terminal:

"(exec compiz --replace &)"

Close the terminal.  It should work.  Let me know if it doesn't.

---

### Post by murak on 2007-07-07
Thanks LouisvilleLIP, Ill try it tonight.

---

### Post by OffHand on 2007-07-07
Or use my toggle compiz/metacity script: [http://ubuntuforums.org/showthread.php?t=489341](http://ubuntuforums.org/showthread.php?t=489341)

---

### Post by murak on 2007-07-07
LouisvilleLIP was right, the boarders stays eventhough I close the terminal. Big thanks LouisvilleLIP!

Bear with me, but how do I make compiz start automaticly when I log in?

---

### Post by hyperair on 2007-07-08
Add it to your Startup Programs in Sessions (System->Preferences->Sessions).

---

### Post by murak on 2007-07-09
Missing something basic here... When I ad ```
(exec compiz --replace &)
``` to the startup programs, it does not work. Am I suppose to wright something else in there also?

---

### Post by hyperair on 2007-07-09
Don't put that in your sessions. Use this instead:
```

compiz --replace -c emerald
```

---

### Post by hyperair on 2007-07-09
EDIT: whoops I accidentally posted a post for another thread here.

---

