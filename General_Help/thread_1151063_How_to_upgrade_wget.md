---
title: "How to upgrade wget"
date: 2009-05-06
forum: General Help
---

### Post by kev-o on 2009-05-06
Hi, (First time poster, million time reader)

     I've got an issue with wget on a Gutsy server.  I've got version 1.10.2 (wget), and I believe that this version doesn't transfer hidden files.  But the 1.11 version does.  I've got Jaunty on my laptop and it's version is 1.11.4.  So I ran sudo apt-get install wget, and it says "wget is already the newest version".  But I know that it's not, so perhaps my sources list needs modifying?  I updated the list sudo apt-get update, but still no dice.  I'd really just like to get the newest version?  This must be possible?  I'd like to do it via the apt-get method, as I suck at compiling binaries, and this server is fairly important, and I'd hate to screw it up.

Any help would be great!!

-kev

---

### Post by chriskin on 2009-05-06
why not installing wget from [http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=wget](http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=wget) ? i don't know if it works for sure, but every time i tried installing a package from a later release, i never had any problem. might have been luck though - you can always uninstall it and reinstall the one in your repositories if anything goes wrong , so i see no risk in trying

and there is always the obvious of upgrading from gutsy to a later version, isn't gutsy a little too old?

---

### Post by EXCiD3 on 2009-05-06
If you have proposed and/or backports enabled you might get a newer version through there.

---

### Post by coffeecat on 2009-05-06
> **kev-o said:**
> I've got an issue with wget on a Gutsy server ... So I ran sudo apt-get install wget, and it says "wget is already the newest version".

Gutsy is now unsupported and all Gutsy packages have been withdrawn from the repositories. See the announcement in the first post of this thread:

[http://ubuntuforums.org/showthread.php?t=1104965](http://ubuntuforums.org/showthread.php?t=1104965)

You need to upgrade to Hardy at least, or do a fresh install of Jaunty server.

---

