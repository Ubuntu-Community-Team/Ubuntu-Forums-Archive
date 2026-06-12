---
title: "fluxbox configuration errors..."
date: 2008-04-27
forum: Desktop Environments
---

### Post by jorik42 on 2008-04-27
so, im trying to install fluxbox onto my pc; but when i run the ./compile command, i eventually get the following errors:

edit: i meant to say, whenever i run the ./configure command, not the compile command.  sorry for the mixup..

checking for iconv_open in -liconv... no
checking for libiconv_open in -liconv... no
checking for iconv declaration... no
checking for t_open in -lnsl... no
checking for socket in -lsocket... no
checking for X... no
configure: error: Fluxbox requires the X Window System libraries and headers.

im not entirely sure what that means or what to do about it.  Any help or ideas will be much appreciated.

jorik

---

### Post by sorak on 2008-04-28
looks like youre trying to compile from source without the development headers for X. why not just apt-get it?

---

### Post by jorik42 on 2008-04-28
thats a very good question.  for some reason i was under the impression that it wasnt in the repositories (perhaps the last time i tried to apt-get it, i didnt have all the sources selected or something).  either way, thanks to that suggestion were all good here.  

jorik

---

### Post by ja660k on 2008-04-28
i got it off the respo's and i cant seem to open it...

"BScreen::BScreen: an error occured while querying the X server.
        another window manager already running on display :0.0
Error: Couldn't find screens to manage.
Make sure you don't have another window manager running."

please help

---

### Post by kerry_s on 2008-04-28
> **ja660k said:**
> i got it off the respo's and i cant seem to open it...

"BScreen::BScreen: an error occured while querying the X server.
        another window manager already running on display :0.0
Error: Couldn't find screens to manage.
Make sure you don't have another window manager running."

please help

logout, select fluxbox in the session menu & log in.
make sure you run> **sudo update-menus**
before you go to fluxbox or you won't have no right click menu.

---

### Post by ja660k on 2008-04-28
hey cool thanks :)

how can i change the theme? where do i put the theme code for fluxbox themes?

---

### Post by kerry_s on 2008-04-28
> **ja660k said:**
> hey cool thanks :)

how can i change the theme? where do i put the theme code for fluxbox themes?

[http://fluxbox.sourceforge.net/docbook.php](http://fluxbox.sourceforge.net/docbook.php)

---

### Post by spupy on 2008-04-28
[http://box-look.org/index.php?xsortmode=down&page=0&xcontentmode=7400](http://box-look.org/index.php?xsortmode=down&page=0&xcontentmode=7400)
[http://browse.deviantart.com/customization/skins/linuxutil/winmanagers/box/?order=9&alltime=yes](http://browse.deviantart.com/customization/skins/linuxutil/winmanagers/box/?order=9&alltime=yes)

Themes for Fluxbox.

---

### Post by ja660k on 2008-04-29
hey cool, but how do get those themes so i can use them in fluxbox?

im reading the docs but yeah cant seem to figure it out

---

### Post by spupy on 2008-04-29
> **ja660k said:**
> hey cool, but how do get those themes so i can use them in fluxbox?

You should put the files of the theme in a separate folder for the theme, located in /home/username/.fluxbox/styles. Fluxbox themes are called styles. There should be a list of installed styles somewhere in the right click desktop menu (sorry I don't remember the standard menu).

---

