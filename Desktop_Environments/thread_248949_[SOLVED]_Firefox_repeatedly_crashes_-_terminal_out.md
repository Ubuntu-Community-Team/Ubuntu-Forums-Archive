---
title: "[SOLVED] Firefox repeatedly crashes - terminal output"
date: 2006-09-01
forum: Desktop Environments
---

### Post by altonbr on 2006-09-01
My father's computer (the one I am currently on) will continuely crash Firefox when I try to open it... it's been happening for about 2 weeks now.. I'll check the first time that I sent a TalkBack report next time it crashes, but as an estimate, it was around August 22nd.

I forgot you can run a program through the terminal and have an output given when something happens (in this case, crashing).

The output is:

```
/opt/firefox/run-mozilla.sh: line 131:  7505 Segmentation fault      "$prog" ${1+"$@"}

```

Does anyone recognize the problem here? I'm using firefox ```
1.5.dfsg+1.5.0.5-0ubuntu6.06.1
``` and I do NOT use automatix on this computer.

Other packages included:

```
firefox-dom-inspector
firefox-gnome-support
```

And that's as much as I know for now.

Thanks for the help :) :wink:

---

### Post by roostishaw on 2006-09-01
Close to the same thing happend to me. Make sure all of the folders relating to firefox have the correct permissions. As in, you can read/write/execute all of those files.

---

### Post by altonbr on 2006-09-02
Mmm, that's not the problem... all the permissions seem to be set correctly.

---

### Post by altonbr on 2006-09-04
Guys, my dad's BROWSER isn't working... does anyone know what's going on? ](*,)

---

### Post by cwaldbieser on 2006-09-04
> **altonbr said:**
> Guys, my dad's BROWSER isn't working... does anyone know what's going on? ](*,)

Not sure what is going on-- the error you gave basically says the startup script tried to launch the program and died.  One of the following may help figure out what is going on:

1) Install another browser and see if that works-- rules out network problems.
2) Completely uninstall and reinstall Firefox-- something may just have become misconfigured.  You can export all your favorites, and reimport them so you won't lose anything.
3) Try the live CD and see if Firefox is working in that.  This doesn't prove anything by itself, though it might help determine what is wrong by comparing settings, etc.

---

### Post by altonbr on 2006-09-04
1) Not done.. BUT I know it's not a networking problem... because sometimes Firefox decides to work.. he says usually on the third try.. I myself don't see a pattern though...

2) I have completely uninstalled and reinstalled Firefox and installed different add-on packages and it's still crashing.

3) I've tried the LiveCD and it works...



Is there any way that I can print a more verbose error message regarding the crash? Maybe that will help.

---

### Post by nikosft on 2006-09-13
The same thing happened to me and the reason was that the disk where the profile was stored was almost full (it had 5mb free space). May be this is also your case.

---

### Post by carontis on 2006-09-13
Try to uninstall it and re-install it. Probably something missing that you can't see

---

### Post by swamytk on 2006-09-13
I too face same kind of problem. Please look at this thread.
[http://www.ubuntuforums.org/showthread.php?t=256418&highlight=segmentation+fault](http://www.ubuntuforums.org/showthread.php?t=256418&highlight=segmentation+fault)

---

### Post by crossedout on 2006-09-13
Check the ownership of your /home/.mozilla and subdirectories.

Navigate to the home folder, ctrl+h -> right-click .mozilla -> Properties -> Permissions -> File Owner

The file owner name should be your login name.

-Xout

---

### Post by altonbr on 2007-09-16
Deleting the personal preferences from ~/.mozilla/ works.

Silly ignorant me last year ;)

---

