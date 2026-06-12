---
title: "switch back to ubuntu from xubuntu"
date: 2007-02-11
forum: Desktop Environments
---

### Post by arron on 2007-02-11
I wanted to try out the xubuntu environment to see if there was any speed difference.  So looking on here, in a post i found a apt-get command to install xubuntu desktop (i cant remember the exact command, and cant find the thread again), but it installed a whole wack of applications.  Anyhow, i did it and played some with xubuntu.  It was nice, but i liked the extras and layout of the ubuntu desktop.

So not i want to go back to the ubuntu desktop.  I have a xubuntu login screen, and i switched the login to the ubuntu desktop environment so i got the gnome desktop.  But i want to get back the ubuntu login screen and remove all the extra applications that were installed.

Does someone know how to get the login back, and what apps to remove?  Maybe if someone could apt-get **xubuntu desktop** and just copy and paste the applications installed onto a standard ubuntu install, i could remove those packages.  Or any other ideas without reinstalling everything.

---

### Post by raja on 2007-02-11
Apparently if you installed the xubuntu desktop with apt-get (and not aptitude), you cant just do an 'apt-get remove xubuntu-desktop'. You have to specify all the packages to remove. If you are using edgy (I presume you are), [this site]("http://www.psychocats.net/ubuntu/purekde") provides the command to remove the xubuntu packages that you can paste in our terminal.

---

### Post by ubuntu27 on 2007-02-11
Raja, you gave him the link for pure KDE He wants **GNOME** ;) hehe. 

Here is the link:

[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

GO arron!!

By the way, Arron, you should read this little page: 

[http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)

So you could know the difference between Aptitude and Apt-get  command.

---

### Post by arron on 2007-02-11
Thanks for the info guys.  I see aptitude removes all the dependancys better than apt.  I guess old habits are hard to get rid of, since i run debian on my server for over 8 years now.

All i can say is Ubuntu rocks!  this forum rocks!  Thanks.

---

### Post by ubuntu27 on 2007-02-11
> **arron said:**
> Thanks for the info guys.  I see aptitude removes all the dependancys better than apt.  I guess old habits are hard to get rid of, since i run debian on my server for over 8 years now.

All i can say is Ubuntu rocks!  this forum rocks!  Thanks.

You're very welcome. :popcorn:

---

