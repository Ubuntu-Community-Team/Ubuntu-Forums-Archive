---
title: "Cedega Timedemo: Ran ONCE ok, now won't run :("
date: 2006-01-06
forum: Gaming &amp; Leisure
---

### Post by mr_chippy on 2006-01-06
I downloaded the 14 day time demo yesterday.. when I ran the install script, a few errors popped up about missing folders in the terminal output but the graphic installer said everything had installed fine.. all the hardware tests ran ok as well, and the program even ran the first time.. then when I came back to it later I had a shortcut for Cedega in "lost and found" on my menu, if I click it nothing happens, Cedega shows in the taskbar for a few seconds then disappears again. If I try and run it from the Konsole I get error messages about missing folders. I can't run the program, and I can't run the uninstall script either, it says "cannot find suitable uninstaller." I tried reinstalling the program but you have to manually confirm the overwiting of hundreds of files..any ideas?  is this because I used the an sh script not a deb package?? I'm pretty new to LINUX and I basically now have a nerfed Cedega install that I can't remove.. Would paying for the full version and getting a deb package help?

---

### Post by Perfect Storm on 2006-01-06
Please post the terminal error output.

---

### Post by Voodoo71 on 2006-01-24
[QUOTE=mr_chippy]I downloaded the 14 day time demo yesterday.. when I ran the install script, a few errors popped up about missing folders in the terminal output but the graphic installer said everything had installed fine.. all the hardware tests ran ok as well, and the program even ran the first time.. then when I came back to it later I had a shortcut for Cedega in "lost and found" on my menu, if I click it nothing happens, Cedega shows in the taskbar for a few seconds then disappears again. If I try and run it from the Konsole I get error messages about missing folders. I can't run the program, and I can't run the uninstall script either, it says "cannot find suitable uninstaller." I tried reinstalling the program but you have to manually confirm the overwiting of hundreds of files..any ideas?  is this because I used the an sh script not a deb package?? I'm pretty new to LINUX and I basically now have a nerfed Cedega install that I can't remove.. Would paying for the full version and getting a deb package help?[/QUOTE]
same problem here..
i used the root account to fix that uninstall problem...

---

### Post by maxol on 2006-03-08
I have the same problem, running the uninstall as root makes no difference.

I receive the error "Could not find a usable uninstall program. Aborting."

The uninstall is present.

Any ideas?

---

### Post by akiro.yamamoto on 2006-03-15
The uninstaller should be located in transgaming_cedega_timedemo 
directory in your home folder.
To uninstall run:
```
sh transgaming_cedega_timedemo/uninstall
```
This should do the trick!
Of course this only applies if you had installed as a normal user ;)

---

### Post by maxol on 2006-03-15
I installed as root and the uninstaller is in /usr/local/games/transgaming_cedega_timedemo as you would expect.

I'm running the uninstaller as root but having no luck.

I'll certainly not be buying a subscription to Cedega.

---

### Post by Perfect Storm on 2006-03-15
As a subscription it's a .deb file yo install.


What the output when you try to uninstall, does it say it doesn't exist?

---

### Post by maxol on 2006-03-16
The output is:

"Could not find a usable uninstall program. Aborting."

The uninstall is present though.

---

### Post by Kirzzy_Boy on 2006-03-18
I had the same problem a few minutes ago.
Solution I found was to first change to root in terminal, and then uninstall

```
su
sh /usr/local/games/transgaming_cedega_timedemo/uninstall
exit
```
After the uninstall I noticed that the directory was still there. It was lots of fun removing everything.

What I'd be interested to know is how to install with sudo and still have permissions to use the programm as usr..... I think something needs to be changed, but have no idea what it is.

---

### Post by maxol on 2006-03-21
Thanks Kirzzy_Boy that worked.

I'm curious why it worked as su but not as sudo.

---

