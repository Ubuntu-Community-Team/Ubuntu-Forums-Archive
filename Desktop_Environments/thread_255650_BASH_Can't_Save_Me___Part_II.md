---
title: "BASH Can't Save Me??   Part II"
date: 2006-09-11
forum: Desktop Environments
---

### Post by Kurt_Alan on 2006-09-11
**[FONT="Fixedsys"][SIZE="5"][/SIZE][/FONT]**


As stated before, I evidently misused sudo chown from the shell, locked all my directories, rebooted, and found that gdm was not accessible due to error message:  "GDM could not write to your authorization file. . . Your Home Directory could not be opened for writing."

I thought that, unlike Windows OS, that I had a more powerful system because if the GUI was down I could access the kernal through BASH by entering a tty, and solve the problem.  But I had no responses here and I can't find a solution on the Internet.  I want to keep trying and not reformat, even though I could use some more Linux practice :wink:

---

### Post by Kurt_Alan on 2006-09-11
**[SIZE="4"][/SIZE]**

Besides being a new Ubuntu user I'm also a new Linux user.  Something happened that I didn't even know was possible -- I logged in as root to a "new" gdm with NET access, many of my old programs but my mistakes (all directories locked) also absent.

This is how I did it:
1. boot to default log-in screen (all session choices fail).
2. Ctrl + Alt to F1 (tty1)
3. sudo shutdown now
4. "Give root maintenance password" Entered.
5. startx

In "new" gdm GUI typing now.

How did I get here, where am I, and what does it mean??
To save you trouble, could you just give a brief explanation and point me to a wiki?  I don't even know what search term to use. :confused:

---

