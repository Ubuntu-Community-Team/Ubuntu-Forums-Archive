---
title: "Change theme for Nautilus ran as root"
date: 2005-09-25
forum: Desktop Environments
---

### Post by edemark on 2005-09-25
Hi all

I have a small inconvenience. Many time i have to use nautilus in sudoer mode (gksudo nautilus) to get acces to some of my user accounts. My problem is that the nautilus opened in this way is somehow ugly as it does not have icons (just a basic type that i guess is the default for the case that there are no other icons present which do not have to different icons for files and directory)

Is there any way to change this?

thanks

---

### Post by aysiu on 2005-09-25
There are two ways to do this--I'm guessing on both counts as to whether they'll work.

1. Find out what the command is for the theme preferences and preface that with *gksudo*, then install the themes you want.
2. Create a root account and log into it and install the themes you want. Then log out.

---

### Post by edemark on 2005-09-26
Guess than I am going for the first option 

thanks for the idea

Anyway if someone knows that command so pls 

thanks

---

### Post by mcduck on 2005-09-27
well. the command would be 'sudo gnome-theme-manager', but that doesn't work for me. Theme window opens and I can change the theme, but nothing changes..

Perhaps I should try the second option.

---

### Post by stoffepojken on 2005-09-27
[http://www.ubuntuforums.org/showthread.php?t=23798](http://www.ubuntuforums.org/showthread.php?t=23798) <-------Have you tried this?

Stoffe

---

### Post by mcduck on 2005-09-27
[QUOTE=stoffepojken][http://www.ubuntuforums.org/showthread.php?t=23798](http://www.ubuntuforums.org/showthread.php?t=23798) <-------Have you tried this?

Stoffe[/QUOTE]
Thanks for the link.

I had to remove .themes and .icons from /root, then I made symlinks from my home dir's .themes and .icons and now sudo apps look same as my normal apps. What I wanted was Industrial theme for sudo apps, not the same theme that I use normally, but at least now my eyes don't hurt and I actually have icons when I sudo nautilus ;)

---

