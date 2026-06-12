---
title: "How to install Program Offline"
date: 2005-07-14
forum: Desktop Environments
---

### Post by Mic on 2005-07-14
Just installed Ubuntu but do not have broadband.

E.g. the Firefox that comes default is 1.0.2. but the available at mozilla.org is 1.0.5

After downloading the tar.gz package (thru a friend) from mozilla.org, how can I install Firefox 1.0.5 offline.

Can I assume this is the same method that can be applied to all other programs , eg. thunderbird , Openoffice, Acrobat reader etc.

Thank in advance for the advice. :grin:

---

### Post by dave9191 on 2005-07-14
The firefox that comes with your system has been moddified to and patched to work best with ubuntu (gnome). The version from mozzila hasnt and wont work as well. If you update your system then you will get the lastest patches from the ubuntu team for firefox 1.0.2, but no newer version will be supplied till the next release of ubuntu which will ship with firefox 1.0.4 if Im not mistaken. 

But if you still want to install the latest version from the mozzila site, then firefox comes with an installer. Uncompress the tar.gz file and run the installer in the folder using the sudo prefix and your password. 

Some program will come with their own installers such as firefox and teamspeak, but most will not. In that case you should try and get hold of a deb package and install that using the 'dpkg -i package_name.deb' command. 

And then there is always compiling the program from source, but lets not get into that :) 

Dave

---

### Post by DirtDawg on 2005-07-14
I too have a linux box not hooked to the "net". When you have access to an internet connection, go here: [http://packages.ubuntu.com/hoary/](http://packages.ubuntu.com/hoary/)  At this website are several hundred pieces of software specifically tailored for Ubuntu. Download what you want, put them on your computer, then open the terminal and navigate it to the folder with the ".deb" file. Then type: sudo dpkg -i yourmomsprogram.deb (i think that's the syntax. I sort of forget though, so you may want to double-check). 

Occasionally you'll run into dependancy problems, but those are available to download from the same site via links you'll see (with red dots next to 'em). 

Hope that helps!

---

