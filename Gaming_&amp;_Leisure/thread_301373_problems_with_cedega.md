---
title: "problems with cedega"
date: 2006-11-17
forum: Gaming &amp; Leisure
---

### Post by Shabutie on 2006-11-17
i installed cedega by downloading the .deb file and double-clicking it... when i ran it, i got past the agreement, but after i enter my account info and press forward, it crashes everytime, anyone know whats wrong?

---

### Post by Perfect Storm on 2006-11-17
Try install it via the terminal and afterwards start cedega through the terminal. Check for output.

---

### Post by N'Jal on 2006-11-18
simelar problem, only i can't get the licence agreement to display. It in fact locks my whole system up, short of a hard reboot there is nothing i can do to fix this.

---

### Post by Shabutie on 2006-11-19
> **Artificial Intelligence said:**
> Try install it via the terminal and afterwards start cedega through the terminal. Check for output.

did that... only output was "Killed" when i had to force quit,  any other suggestions?

---

### Post by BIGtrouble77 on 2006-11-19
I'm having the same problems, but in the i386 version (so it's not a 64bit issue).  I was able to get into the program by downloading the cedega engine from the website, but I can't get anything else like the fonts and mozilla crap.  It seems to be an issue with the auto update feature.

---

### Post by BIGtrouble77 on 2006-11-19
I found an answer to the problem on the transgaming forums.  Here's the fix (it worked for me):
> sudo dpkg-reconfigure dash

...and select "No" when it asks wether dash should be installed as /bin/sh. It will then make /bin/sh a symlink to /bin/bash as Cedega (and many other scripts) expects. 
Then try running Cedega again, and check for updates (it probably will automatically if you've never gotten past that point after installing it).

---

### Post by Shabutie on 2006-11-19
sweet! got it to update and run... now its time to go play! thanks again for the solution

---

### Post by TMOL on 2006-11-20
I'm having another problem, whenever I open any of the files in cedega, no matter which one it is, nothing happens, a window pops up and it is simply blank. I can't get past this problem because, obviously, there's nothing to click. I thought it may be a problem with Ark, but I'm not sure. Can anyone help me?

---

