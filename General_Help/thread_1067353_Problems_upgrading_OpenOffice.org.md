---
title: "Problems upgrading OpenOffice.org"
date: 2009-02-11
forum: General Help
---

### Post by jonlemur on 2009-02-11
I'm having some frustrations with openoffice.org and apt-get.  I'm upgrading from 2.4 to 3.0, and in the process, I decided to uninstall all of 2.4 before installing 3.0 (actually due to errors in upgrading).  Now, when I run sudo apt-get install openoffice.org, it freezes at every file it tries to download, for instance it stays at
```
Get:1 http://ppa.launchpad.net intrepid/main openoffice.org-math 1:3.0.1-1ubuntu1~intrepid1 [239kB]
0% [1 openoffice.org-math 7862/239kB 3%]
```
The weird thing is that if I Ctrl+c out of it, I can install the individual file that it freezes on no problem.  So here I can ```
sudo apt-get install openoffice.org-math
``` just fine.  But it will freeze at the very next file.  

I remember doing something on another computer with dpkg, purge, and openoffice.org-common, but I can't find what that was.  Any ideas on what I need to do?

---

### Post by mb_webguy on 2009-02-11
What PPA are you using?  [This one]("https://launchpad.net/~openoffice-pkgs/+archive/ppa")?

Make sure you've added the correct entries to your software sources, and added the GPG for the PPA.

---

### Post by abn91c on 2009-02-11
this guide works well, [http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml](http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml)

---

### Post by jonlemur on 2009-02-11
Thanks for your replies.

abn, that's the guide that I used, but it messed up on me.  
mb, I tried your advice, but it fails at the same place.

Any other ideas?

---

### Post by jonlemur on 2009-02-11
Well, I don't know what was causing the problem, but I worked around it by copying all of the file names that were to be installed with sudo apt-get install openoffice.org and pasting them in to their own sudo apt-get install command.

---

