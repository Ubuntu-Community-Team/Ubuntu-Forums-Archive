---
title: "Error message when trying to install mint desktop theme"
date: 2012-04-21
forum: Desktop Environments
---

### Post by Senior_Buckethead on 2012-04-21
Hi there

I was trying to install a mint theme using the following commands:
sudo apt-add-repository ppa:satyajit-happy/themes
sudo apt-get update && sudo apt-get install cinnamon-theme-minty

And after all the package lists were read, I received the following error message:

Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 cinnamon-theme-minty : Depends: cinnamon but it is not installable
E: Unable to correct problems, you have held broken packages.
glenn@acer:~$ 

Can someone please shed light into what has occured? Please let me know.

Cheers
Glenn.

---

### Post by dniMretsaM on 2012-04-21
You need to have Cinnamon installed. Info about a PPA [here](http://www.webupd8.org/2012/02/alternative-cinnamon-ppa-for-ubuntu.html)

---

