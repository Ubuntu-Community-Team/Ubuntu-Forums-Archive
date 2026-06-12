---
title: "Beryl - cube sides problem"
date: 2007-05-05
forum: Desktop Effects &amp; Customization
---

### Post by Ru$$i@N on 2007-05-05
Hi,

When i turn the cube, i see blank sides of the cube and top and bottom panels. No shortcuts on desktops either.
Beryl used to work fine. Looks like all the other effect are working fine. I might be wrong, but i think that the problem appeared after I put both "beryl-manager" and "beryl" as startup programs. Now i only have "beryl" in there, but that didn't solve my problem.
And another thing; i don't know if it's related to beryl somehow or not. Sometimes i see "USA" as keyboard indicator and sometimes it changes to "us". Any ideas why?

Some additional info:
Ubuntu Feisty Fawn AMD64
Nvidia 7500

The pictures show what i see.
Any help is appreciated.

---

### Post by tophatandy on 2007-05-05
well run ```
beryl-manager
``` in terminal and then check the opacity of your cube sides..

then try putting beryl-manager in startup.. 

I only have beryl-manager in my startup and everything works fine.

---

### Post by Ru$$i@N on 2007-05-05
hmm...
Now the walls are there. Thank you for that.
But now i don't see _any_ panels or shortcuts. I used Alt+F2 to launch firefox to reply.
All i see is my wallpaper. The cube, though, seems to work perfectly fine, and windows do wobble.
I have also noticed that now when i double click the window header, it (i don't know how do you call that officially) rolls up into a line instead of maximizing as it did before.

---

### Post by Ru$$i@N on 2007-05-08
Problem solved.
I didn't realize that I had both Beryl Settings Manager and Beryl Settings Manager (Simple) installed.
As soon as I uninstalled the simple one, everything became normal.

---

