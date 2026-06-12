---
title: "Nautilus File Manager Locks"
date: 2006-01-11
forum: Desktop Environments
---

### Post by ProPilot on 2006-01-11
Out of the blue (Ubuntu brown LOL) Nautilus file manager (select Places then Home Folder) locks up. Clicking on the X upper right corner and force quiting shuts it down but then it restarts all by itself and locks up. Doing this sequences is an endless loop of quiting and restart.

I went system-administration-package manager and reloaded the relevant units (at least the ones I thought applied) and no joy.

Any suggestions?

Thanks
Tom

---

### Post by earobinson on 2006-01-11
Is it happining all the time or once in a while? you could bugzilla it.

---

### Post by ProPilot on 2006-01-11
It happened a long while ago but this is the first reoccurance.

I'll bug it later (when back from work in a couple of days) but is there a work around in the meantime?

Tom

---

### Post by pmj on 2006-01-11
It might be that there's a file in the home folder that makes Nautilus crash. It happened to me once. When Nautilus restarts the home folder pops up and it crashes again. Moving the file out of home fixed it for me. I can't remember what type of file it was that did this to me, but if you rencetly added something to your home folder, try moving it out and see if that solves it.

---

### Post by ProPilot on 2006-01-14
Thanks for the suggestion

I did add some files before it locked. Now that it locks how does one move files out when I can't get in to the file manager?

Tom

---

### Post by george_apan on 2006-01-14
Open a terminal window and while in the home folder (~) type (without the $ signs):

$ mkdir temp

to make a temporary directory and:

$ mv myfile temp/

to move a file named "myfile" to the directory you just made.

---

### Post by ProPilot on 2006-01-14
George

Thank you. I guess I had a "blond" moment. While you where typing I figured it out and have deleted (rm) the files. Your suggestion is much better if one needed to save the files which I did not.

Thanks. I am just rebooting the computer.

AND

Presto File Manager now works. This is Tom jumping for joy.

I will submit a bug report.

Tom

---

