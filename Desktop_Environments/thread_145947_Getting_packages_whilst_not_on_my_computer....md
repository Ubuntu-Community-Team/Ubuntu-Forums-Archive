---
title: "Getting packages whilst not on my computer..."
date: 2006-03-17
forum: Desktop Environments
---

### Post by Blutack on 2006-03-17
Odd question...I've been using Kubuntu 5.10 Breezy for a month or so and love it.  However I do not have a high bandwidth internet connection at home and downloading new packages is very difficult.  I have a high speed internet connection at work and can download packes directly from the ubuntu packages site but with complex packages knowing which packs need dependencies etc etc is extremely difficult.  Not only do I not know which packs I already have installed but tracking down the web of dependencies on dependencies is impossible.  I managed to update my sources list and have access to all the packages I want but cannot download.  Is there any way to take the adept "list" and use it from a flashdisk on a windows machine to work out what to download?  From my linux experiences so far someone has probably built a fantastic little program that runs off a flashdisk for doing just this...
Many thanks for any help and I am sure that I am not alone in this problem...

---

### Post by vidak on 2006-03-18
I think **aptitude** is your friend. Search the package, which you want, by pressing "/" and entering a regexp, or just a part of the package name. You can search eg. in the descriptions by using ~dexpression. Step through the list matching the regexp using "n".
After you found the package you want, press "+", which selects the package for install (you don't have to be root to do this). After you've made your selections, press "g" (go), and on the next screen you can see all the packages that will be installed, with the dependencies. Write down these ones, download them to the flash disk, and install them with 
sudo dpkg -i foo.deb bar.deb
It's maybe not the most elegant way, but hope it works...

---

### Post by GeneralZod on 2006-03-18
Look into [apt-zip](http://packages.debian.org/unstable/admin/apt-zip.html) and see if it meets your needs :)

---

### Post by nrwilk on 2006-03-18
Maybe you could, while at home, mark the packages you want to install for install.  Then, check what synaptic (adept?) wants to install as dependencies, and write them down.  Then, when at work, download those packages.  I guess that isn't too much work to get stuff downloaded, as long as you know what you want before you leave for work.

Just an idea.

---

### Post by Blutack on 2006-03-23
Brilliant!  Thanks guys.  I've actually discovered that I can use apt-get at the command line to do a "dry run" type thing where it displays the URL of each of the packages instead of downloading them.  I just copy the stuff from Konsole into Kate and save it as a text doc, then post it into the dreaded IE at work...
Many Thanks for all your help

---

### Post by nrwilk on 2006-03-23
Nice feature, good find!  :D

---

