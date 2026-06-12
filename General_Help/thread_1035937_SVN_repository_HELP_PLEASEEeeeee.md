---
title: "SVN repository HELP PLEASEEeeeee"
date: 2009-01-10
forum: General Help
---

### Post by netvampire on 2009-01-10
Hello,
I really would appreciate it if anyone can guide me through what I need to do.

I previously was running Ubuntu Feisty and had an SVN server with multiple repositories running and working great for over a year.

I recently decided to do a clean install of Ubuntu Hardy. To back up my previous SVN repositories I simply copied the directory that the repository were created in to a usb key. 

Now I have a clean install of Hardy, with subversion installed, however I am clueless how to go about restoring my previous repositories.

Help would be really appreciated. I am unable to get my work done until I get this figured out. Please assist. Thank You!

---

### Post by netvampire on 2009-01-10
PROBLEM SOLVED!

After much searching and reading I discovered that using this command I was able to set the root directory of my svn repositories to the location of my backed up repository folders..

```

svnserve --daemon --root "C:\Path\to\Subversion Repository"  


```

---

