---
title: "apt-get install php5 ... php5 not found"
date: 2005-11-09
forum: Desktop Environments
---

### Post by awood on 2005-11-09
Hello, I'm new to Ubuntu, and I am enjoying what it has to offer.  I recently tried to install apache2, php5, and mysql.  I called sudo apt-get install apache2, and it worked beautifully.  However, I tried sudo apt-get install php5, and it said that  php5 could not be found.  I tried the same with php4, and got the same response.  From what I have seen on these forums, these are the proper commands to retreive these packages.  Is there a way for me to update my apt-get repositories?  Is there a way to query apt-get to get a list of available packages that I could | less through? Is there another package name I should be using to get php?

Thanks.

---

### Post by earobinson on 2005-11-09
whoever used that command probaly has a diferent /etc/apt/sources.list than you. ask them to post the /etc/apt/sources.list that they use and add any missing lines to yours

---

### Post by awood on 2005-11-09
I found those commands in the user documentation ([https://wiki.ubuntu.com/ApacheMySQLPHP)](https://wiki.ubuntu.com/ApacheMySQLPHP)).  Is there a standard way of updating my sources.list, or is it normally done manually?  If it is the latter case, then perhaps someone could point me to a place where I can get a list of entries to add.

Thank for your help.

EDIT:
Bah ... I found out how to update my repositories.  The link ([https://wiki.ubuntu.com/ApacheMySQLPHP](https://wiki.ubuntu.com/ApacheMySQLPHP)) links to an explanation as to how this is done.

---

### Post by earobinson on 2005-11-09
your link must be broken.

there are guis/programs that will edit it. I find gedit is the best way.

this might help [http://www.ubuntuforums.org/showthread.php?t=87946](http://www.ubuntuforums.org/showthread.php?t=87946) (i found this by searching the forums for: sources.list)

---

