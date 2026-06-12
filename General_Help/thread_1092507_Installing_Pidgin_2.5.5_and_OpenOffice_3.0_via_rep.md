---
title: "Installing Pidgin 2.5.5 and OpenOffice 3.0 via repository?"
date: 2009-03-10
forum: General Help
---

### Post by kcredden on 2009-03-10
Folks: Been trying to install Pidgin 2.5.5 without success. The getdeb .DEB of Pidgin don't work, get all sorts of dependency hell. I've also been trying to upgrade OpenOffice to v3.0. 

So does anyone know if there is a Ubuntu 8.04/10 repository that has Pidgin 2.5.5 and OpenOffice 3.0 on it?

I just tried Jaunty's but I'd have to upgrade to it and I don't need too for 2 program. 

- Kc

---

### Post by CrusaderAD on 2009-03-10
Try this:

[http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml]("http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml")

It worked for me. I'm not sure about Pidgin tho.

---

### Post by kcredden on 2009-03-10
Thanks, but it didn't work either. One frigging file had dependency problems, and nothing I did would fix it. Even erased my *old* open office, now got to wait 2 hours to reinstall it. 

I'll just wait till v9.04 (or so) comes out, so I can upgrade to pidgin, and OO

Boy I miss Windows's 1 file DL installing of programs. Linux still needs work on this installing problem. 

- Kc

> **raptormanad said:**
> Try this:

[http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml]("http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml")

It worked for me. I'm not sure about Pidgin tho.

---

### Post by exploder on 2009-03-10
> Boy I miss Windows's 1 file DL installing of programs. Linux still needs work on this installing problem. 

Ah, but you are forgetting dll hell. You can get Pidgin 2.5.5 here.

[http://www.getdeb.net/search.php?keywords=pidgin](http://www.getdeb.net/search.php?keywords=pidgin)

Make certain to remove the old packages before installing the new ones and you will have to reinstall pidgin-otr when you are finished. The new version works great!

Here is how to get OpenOffice 3.0.1 from the ppa repo. Just copy and paste this command into the terminal.

gksu gedit /etc/apt/sources.list

enter your password and then paste this to the bottom of the list, skipping a space.

deb [http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu) intrepid main

Close gedit saving the changes. Open synaptic and refresh the package list and select and upgrade OpenOffice. (Just ignore the public key error, you can uncheck the ppa repo after you upgrade.

---

