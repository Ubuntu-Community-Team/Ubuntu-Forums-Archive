---
title: "Gmail applet broke chrome launcher"
date: 2013-10-23
forum: Desktop Environments
---

### Post by kd6C7fP on 2013-10-23
After I installed the "unity Gmail Applet", my launcher button for chrome stopped working (nothing happens when I push it), and when I hover my mouse on it, it says "Inbox (8) - [email]XXXXXX@gmail.com[/email]"  instead of Google Chrome... And the gmail applet doesnt do anything, either. I'm stuck running Chrome from terminal via "$ google-chrome". 

Any help appreciated!

---

### Post by deadflowr on 2013-10-23
What happens when you unlock the launcher(right click unlock launcher) and then try launching chrome from the dash menu?
Click the dash and type chrome and then hit enter.(The first app in the listing will be automatically launched if you press enter)

---

### Post by kd6C7fP on 2013-10-23
Same thing, nothing happens. I've tried purging and reinstalling both Chrome and the gmail applet, but it didnt help...

---

### Post by deadflowr on 2013-10-23
I would guess the next step would be to compare what the .desktop files for each states.
You can look over those files using the text ediotor, gedit.
Open gedit and select file system > then select usr > then share > then applications.
The navigate to the two files listings for google-chrome and whatever the gmail applet is called.

Then in each look for the line(s) that begins with Exec=.
You should probably copy and post what those lines say for each one.

---

