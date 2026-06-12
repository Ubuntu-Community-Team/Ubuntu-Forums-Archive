---
title: "gedit hiding text after tab (indent)"
date: 2008-02-11
forum: Desktop Environments
---

### Post by jediosu on 2008-02-11
I've been using gedit to edit my text files for a year or so now (php code)  Now (starting last Friday) when I open a file in gedit I can't see any lines that begin with a tab (indent).  I can open them in kwrite and see everything, I can open them in gedit and print preview and see it, but just opening them in gedit I can't see any lines of text after an indent.  If I use another editor and remove the tabs starting the line I can see the line in gedit, also if I type something in gedit and hit tab before it, the line disappears.   I can't for the life of me figure out whats changed, any ideas?  My text files work fine in gedit on another machine, I've corrupted something or inadvertently changed a setting but I don't know what.

---

### Post by jediosu on 2008-02-14
FWIW I got this fixed.

I didn't pay attention to what box I was logged in to.  My gedit was working in ubuntu, the error was in my SUSE box.  It was readline version 5.1-24.19x86_64 that messed up my tabbing.  

Thanks and sorry for the confusion.  It explains why no one else saw this error :)

---

### Post by shanmcpherson on 2008-02-14
For any other SUSE users out there with the same problem I had to rollback the readline package as well as the cairo package to remedy this problem.

---

