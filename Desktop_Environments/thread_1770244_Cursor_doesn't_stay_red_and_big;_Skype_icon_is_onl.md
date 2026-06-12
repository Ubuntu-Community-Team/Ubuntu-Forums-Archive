---
title: "Cursor doesn't stay red and big; Skype icon is only a pixel big, on top bar."
date: 2011-05-29
forum: Desktop Environments
---

### Post by Nitrozzy7 on 2011-05-29
Finally I found out how to REALLY SOLVE this one.
Now that I'm using Linux Mint and only after reading Mint forums the solution became obvious.
Here's how I solved the random or unstable pointer/cursor issue.
First of, open a window as administrator (root). In Mint is easy. Just right click the file and select the 'Open as Amin' option. On other bistros just use this code in Terminal:
```
gksudo nautilus
```
The file you need to open as root is located here:
/usr/share/icons

Under "/icons" you'll find all the cursors installed on your system. Open the folder with the cursor's name you like and copy the one folder (named "cursors") and the one "index.theme" script you'll find inside to "/usr/share/icons/default", removing the two similar files inside. Log out and back in and your mad cursor will be cured.

---

### Post by Nitrozzy7 on 2011-05-29
Ubuntu 11.04
How to fix this?

---

### Post by Nitrozzy7 on 2011-05-29
Please help

---

### Post by Nitrozzy7 on 2011-05-29
Anyone?

---

### Post by Nitrozzy7 on 2011-05-31
SOLVED
It's amazing how not wanting to see something can change the point of view.
So yeah, it remains unsolved.

---

### Post by Nitrozzy7 on 2011-07-05
Finally I found out how to REALLY SOLVE this one.
Now that I'm using Linux Mint and only after reading Mint forums the solution became obvious.
Here's how I solved the random or unstable pointer/cursor issue.
First of, open a window as administrator (root). In Mint is easy. Just right click the file and select the 'Open as Amin' option. On other bistros just use this code in Terminal:
```
gksudo nautilus
```
The file you need to open as root is located here:
/usr/share/icons

Under "/icons" you'll find all the cursors installed on your system. Open the folder with the cursor's name you like and copy the one folder (named "cursors") and the one "index.theme" script you'll find inside to "/usr/share/icons/default", removing the two similar files inside. Log out and back in and your mad cursor will be cured.

---

### Post by mindgrind on 2011-08-06
> **Nitrozzy7 said:**
> Ubuntu 11.04
How to fix this?

oops. . . bug is identified for Narwhal users.  Solution in the making, I hope. . .

[https://jira.skype.com/browse/SCL-739](https://jira.skype.com/browse/SCL-739)

---

