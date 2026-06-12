---
title: "How can I install Unison 2.17.1 ???"
date: 2007-10-04
forum: Desktop Environments
---

### Post by Daminator on 2007-10-04
I use Unison ([http://www.cis.upenn.edu/~bcpierce/unison/](http://www.cis.upenn.edu/~bcpierce/unison/)) all the time on my windows machines. It's fantastic. It's also cross platform but the version that's in the repositories is something like 2.13.x. How can I install version 2.17.1? I'm sure it's very easy when you know how, but I really can't get anything to work.

Here's the Linux downloads section of the unison site:
[https://svn.cis.upenn.edu/svnroot/unison-contributed-binaries/linux/](https://svn.cis.upenn.edu/svnroot/unison-contributed-binaries/linux/)
Please help!

Cheers
Damian

---

### Post by Daminator on 2007-10-09
For enyone else who needs this, I got some great advice that works perfectly (apart from not having a menu icon)

> 
I assume you want to get rid of unison 2.13.16. If so use Synaptic to 
uninstall (see Note following) 2.13.16. 
Note: I usually do a complete removal. I don't know if that means Synaptic 
will get rid of your profile files . Just in case go to the .unison directory 
in your home directory and copy the *.prf files somewhere for safekeeping. 
Also, you will be syncing with a new version so when you do the first syn 
after upgrading Unison will create new data files for tracking the state of 
both sides of the syn.c. In other words it may take more time than usual.

Go to URL below and fetch 
[https://svn.cis.upenn.edu/svnroot/unison-contributed-binaries/linux/unison-2.17.1-linux-gtk2.bz2](https://svn.cis.upenn.edu/svnroot/unison-contributed-binaries/linux/unison-2.17.1-linux-gtk2.bz2)
Note this is the GTK version which can be run as either GUI or text. I tested 
on my system here (Dapper) and it works as GUI.

Use bunzip2 to unzip above file:
aklaver@tucker:~/test$ bunzip2 unison-2.17.1-linux-gtk2.bz2

This will result in:
unison-2.17.1-linux-gtk2

Then do below:
aklaver@tucker:~/test$ sudo cp unison-2.17.1-linux-gtk2 /usr/bin/

Then:
aklaver@tucker:~/test$ cd /usr/bin/

Then:
aklaver@tucker:/usr/bin$ sudo chmod 755 unison-2.17.1-linux-gtk2

Then:
aklaver@tucker:/usr/bin$ sudo ln -s unison-2.17.1-linux-gtk2 unison

This will allow you to type unison and get the 2.17.1 version.


---

