---
title: "Items not showing on Desktop"
date: 2007-08-24
forum: Desktop Environments
---

### Post by kendallp on 2007-08-24
Hello,

I am using Feisty and when I download files from Firefox it says it is saving them to desktop but they are not showing up there.  

I then tried going to Places --> Desktop and the files are not listed there but if I do a search, the files do show and the properties list them in /Desktop.

From the terminal doing a "ls Desktop/" shows all the files.

I tried right clicking the desktop and choosing "Clean Up by Name" thinking they were somehow being put off the screen but that did not cause the files to be shown either.

Any ideas what I am doing wrong?


Thanks is advance,
-Kendall

---

### Post by Happy_Man on 2007-08-24
Perhaps you accidentally set it so that icons are not shown in the Desktop by mistake? Go to the Gconf editor ```
gconf-editor
``` and navigate to apps/nautilus/desktop and see if that is the case.

---

### Post by kendallp on 2007-08-24
I currently have items on the desktop and can add new files there.  It is just the files that I download from Firefox.  It says they are going there but they do not show.  I also tried showing hidden files to see if somehow they were getting marked hidden but that didn't work.

The only way I can see downloaded files is through the terminal window or by doing a search.

I did look through the gconf editor and did not see anywhere that could have marked desktop items hidden.


Thanks,
-Kendall

---

### Post by igoddard on 2007-08-24
> **kendallp said:**
> Hello,

I am using Feisty and when I download files from Firefox it says it is saving them to desktop but they are not showing up there.  

I then tried going to Places --> Desktop and the files are not listed there but if I do a search, the files do show and the properties list them in /Desktop.

From the terminal doing a "ls Desktop/" shows all the files.

I tried right clicking the desktop and choosing "Clean Up by Name" thinking they were somehow being put off the screen but that did not cause the files to be shown either.

Any ideas what I am doing wrong?


Thanks is advance,
-Kendall

You said that search shows them in /Desktop.  Do you really mean /Desktop and not /home/you/Desktop (where "you" is your login name)?  If so, that's the answer - you've saved them in the wrong place as /home/you/Desktop is what shows up on your screen.

Ian

---

### Post by kendallp on 2007-08-24
Yes, I did mean /home/you/Desktop.

I did a search with the file browser, found the file that I was looking for, the properties of the files show it's location as /home/you/Desktop but the file is not located as an item on my desktop or in the list when I goto Places ---> Desktop.  So I drug the file from the file browser onto my desktop and it created a copy of the file something (copy).pdf.  If I look at the properties of both files, the one showing on the desktop and the original not showing, they both have the same location /home/your/Desktop.

I am new to Ubuntu and have limited experience with linux, so I figured I was just doing something goofy.

Thanks for the ideas so far.

-Kendall

---

### Post by Wolki on 2007-08-25
I occasionally experienced the bug that nautilus stopped updating the contents of some folders, so I had to do this manually. Try hitting ctrl-r and see if they appear. If they do, it's likely the same bug.

---

### Post by contactmayankjain on 2008-06-19
I am also facing the same problem after online update.

---

