---
title: "Can't install Moksha on 14.04"
date: 2016-03-21
forum: Desktop Environments
---

### Post by smrz14 on 2016-03-21
Has anyone successfully installed Moksha on Ubuntu 14.04?   Supposedly this is possible, but I got the following error:

[INDENT][I]> apt-get install moksha packagekit bodhi-desktop-e17

...
[I]Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:
  
The following packages have unmet dependencies:
    bodhi-desktop-e17 : Depends: e17 but it is not going to be installed
                                     Depends: bodhi-profile-e17 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.[/I]
[/I][/INDENT]

Any thoughts on how to resolve this?

thanks

---

### Post by grahammechanical on 2016-03-21
It is not in the default Ubuntu repositories then it cannot be installed. And that is the impossible situation. You need to add a special repository to do this.

[http://news.softpedia.com/news/how-to-install-bodhi-linux-s-moksha-desktop-in-ubuntu-14-04-lts-and-linux-mint-17-2-491737.shtml](http://news.softpedia.com/news/how-to-install-bodhi-linux-s-moksha-desktop-in-ubuntu-14-04-lts-and-linux-mint-17-2-491737.shtml)

Regards.

---

### Post by smrz14 on 2016-03-22
I've tried the instructions in 
[http://news.softpedia.com/news/how-t...2-491737.shtml]("http://news.softpedia.com/news/how-to-install-bodhi-linux-s-moksha-desktop-in-ubuntu-14-04-lts-and-linux-mint-17-2-491737.shtml")
and they yielded the error message shown above.

---

### Post by goofprog on 2016-03-22
e17 is a windows manager try to install e17 first.  I did not know that ubuntu supported e17.

---

### Post by Frogs Hair on 2016-03-23
The E17 version in the Ubuntu repository is not related to the Bodhi Moksha desktop. The Ubuntu repository version of E17 is dated, bare bones, and missing many modules.Installing it may complicate the package problems if you have already added the  Bodhi repository which would include the latest E17 packages.

---

