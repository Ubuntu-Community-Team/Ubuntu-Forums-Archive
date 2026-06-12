---
title: "How to backup desktop &amp; application settings?"
date: 2007-02-24
forum: Desktop Environments
---

### Post by monocongo on 2007-02-24
After using Ubuntu for about a week now I've finally settled on most of the application and desktop/UI settings I want to keep.  Now I want to make a backup of these configuration settings, and I'm not sure which files/directories I should save.  Will I cover everything if I back up my home directory with all of the hidden (.*) files and directories included?

---

### Post by louis_nichols on 2007-02-24
> **monocongo said:**
> After using Ubuntu for about a week now I've finally settled on most of the application and desktop/UI settings I want to keep.  Now I want to make a backup of these configuration settings, and I'm not sure which files/directories I should save.  Will I cover everything if I back up my home directory with all of the hidden (.*) files and directories included?

Almost. User settings are in those files and folders with a dot that lay in your home folder. So if those are all you need, then it is enough to back them up. However, system wide settings, such as software sources and X server configuration lay in the folder /etc. So you might want to back those up too.

---

### Post by monocongo on 2007-02-24
Thanks for the help/insight.

---

### Post by geoffcj on 2007-02-24
I'm trying to do the same thing.  I used a terminal to go to my home directory, but I don't see any files marked with an *

Are there hidden files, and if so, how do I see them?   And if I just copy the hole directory, and my etc/ directory, could I use those to restore my settings if I screw up while playing around with Linux? 

I've got Beryl up and running, and it looks amazing....

Geoff

---

### Post by monocongo on 2007-02-24
When someone uses * to describe a file name it means any text string, so .* can mean .bashrc, .kde, etc.  The hidden files begin with a dot/period, for example .bashrc, and these files/directories are normally not shown (hidden) when you view a file system with the file manager or when you list files in the terminal console's shell.  To see hidden files type the following at the console command line prompt:```
ls -a
```

I have started using **[keep]("http://jr.falleri.free.fr/keep/wiki/Home")** to perform backups, and I'm backing up my home directory and /etc.  It is basic, simple to use, and seems to work well for a simple restore.  It's for KDE so if you're not using Kubuntu then you'll need to look for another program for backups (there seem to be lots available).

I hope this helps.

---

