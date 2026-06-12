---
title: "Stuck Apt-get with open office dependencies"
date: 2009-01-20
forum: General Help
---

### Post by inadaze on 2009-01-20
Hello,
I am having problems with Openoffice on Intrepid.  It began with having an issue with Java so I tried to uninstall openoffice and re-install it so that I would get the default dependencies downloaded.  Now I get a problem with the installation of openoffice and everytime I use apt-get.

Apt-get gets stuck forever on this line :
```
Adding extension /usr/lib/openoffice/share/extension/install/writer2latex.uno.pkg...
```

until I cmd+C the operation.  Then it gets stuck on :
```
Adding extension /usr/lib/openoffice/program/mailmerge.py...
```

until I cmd+C the operation.  Then I get

```
dpkg: error processing openoffice.org-emailmerge (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 openoffice.org-writer2latex
 openoffice.org
 openoffice.org-emailmerge
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I need help to remove these errors from apt-get and to install openoffice correctly.

Thank you
Jay

---

### Post by inadaze on 2009-01-23
Perhaps I should refine my question a bit.  

I have a problem with apt-get.  Everytime I run it now, it gets stuck on 
```
Adding extension /usr/lib/openoffice/basis3.0/program/mailmerge.py...
```

How can I either install or remove this so that I don't have to press ctrl+c to exit?

cheers
Jay

---

### Post by Kevbert on 2009-01-23
Try running
```
sudo apt-get install -f
```
Hopefully this will help.

---

### Post by inadaze on 2009-01-23
I wish.  I have "googled" this issue for a few days and it seems to work for everyone else but not for me.  It just sticks at the same line....

thanks for the response anyway. :D

---

### Post by inadaze on 2009-02-03
i am bumping this issue.  I really need help here.  I cannot install open office on my computer properly.  it is all because of this emailmerge package that doesn't want to install.  It downloads the package but freezes my apt-get when trying to configure.  I even tried to install ooffice 3 and it just didn't work at all.  I feel like I am chasing my tail here.

---

### Post by swidmer on 2009-02-03
:( your not the only one - I have a similar issue with the dovecot packages -  I can finish the install and I can not remove the package - I'd love to hear how to manually remove the package to allow apt to try again fresh - anyone??

---

### Post by swidmer on 2009-02-03
:D  Try the instructions on this page: [http://www.linuxforums.org/forum/debian-linux-help/133537-subprocess-usr-bin-dpkg-returned-error-code-1-a.html](http://www.linuxforums.org/forum/debian-linux-help/133537-subprocess-usr-bin-dpkg-returned-error-code-1-a.html)


I believe they just helped me fix my issue.

---

### Post by inadaze on 2009-02-04
seems like there is some issue with ubuntu / openoffice and javaldx.  When I was running openoffice, I checked the running processes and killed it and VOILA openoffice opened.  I googled it and got this :

[http://www.oooforum.org/forum/viewtopic.phtml?t=18133](http://www.oooforum.org/forum/viewtopic.phtml?t=18133)

He suggests renaming javaldx on your system.  Worked for me.  The problem with mailmerge and writer2latex installing/configuring seems also related to this.  but I don't have time to investigate further for the moment.  Just happy that openoffice works now.

---

