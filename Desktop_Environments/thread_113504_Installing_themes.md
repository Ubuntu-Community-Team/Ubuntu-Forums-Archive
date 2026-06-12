---
title: "Installing themes"
date: 2006-01-06
forum: Desktop Environments
---

### Post by Minyaliel on 2006-01-06
Yes, when it comes to themes, I'm a newbie n00b. I've downloaded a theme ([http://www.kde-look.org/content/show.php?content=13969](http://www.kde-look.org/content/show.php?content=13969)) but I have no idea how to install it. Any help would be very much appreciated :)

---

### Post by Omnios on 2006-01-06
I think this theme needs to be compiled as writen on the theme page

 ```
- Crystal needs KDE >=3.2 and QT>=3.2.
- May be very slow and memory consuming
- Don't forget to breathe, while drooling.


-- INSTALL ---------------------
Basic Installation (from the console):
- Step 1
$ ./configure
OR: $ ./configure --prefix=`kde-config --prefix`
- Step 2
$ make
- Step 3 (as root)
# make install

If you used a previous version before, you need to restart kde to use the upgraded version (or at least kwin with `kwin --replace`
--------------------------------
```

 Also they wrote its heavy on resouces wich probably means you should have a pretty fast computer.

---

### Post by Minyaliel on 2006-01-06
Aw, darnit. Well, thanks anyway. (Any tips on how to make windows transparent?)

---

### Post by TikkiRo on 2006-01-06
[COLOR="Purple"]Ok - i'm in a similar position having done the same with one on a different site - [http://www.gnome-look.org/content/show.php?content=30011](http://www.gnome-look.org/content/show.php?content=30011).  Now i've unpacked it into its own folder, but can't seem to find any way of getting it loaded into the Themes directory?  Does it also have to be configured or something else first?  Walk-through if possible please.  have some confidence in Terminal at least so can manage so long as I know what commands to use :)).  Tks[/COLOR]

---

### Post by Omnios on 2006-01-06
In gnome go to menu: System / Administration / Log in screen Set Up.

 And click on install theme or just try to drag and it into the theme manager.

 Im not shure how it works in Xubuntu though but basicly the format seems to be putting the file in the same directory with the other GDM's

---

### Post by TikkiRo on 2006-01-06
[COLOR="Purple"]PERFECTO thanks for that - didn't know about that section and great to see the options available there too.  Not just SO brave yet to go digging about too much in such things unless given the goahead by smart people like you :)))[/COLOR]

---

### Post by wishyjr on 2006-01-15
hello guys, ive been trying to configure the source for the crystal theme on my amd64 system. It chuggs along nicely until its gets to this:

checking for X... configure: error: Can't find X includes. Please check your installation and add the correct paths!

any ideas on what its referring to?ive tried updating my kde and qt headers but i'm still getting the same error. not too sure which packages im supposed to install to update the headers for Qt mind so any advise would be well recieved. thanks.

---

### Post by tadashi on 2006-02-22
I tried to run sudo ./configure and for the last line I get:
checking for C compiler default output file name... configure: error: C compiler cannot create executables

I get the same thing when I use the --prefix line.  What am I doing wrong? :p

Figured out my problem.  I was missing some build-essential files and KDE dev files (the dev files will fix wishyjr's problem).  Did a reboot, added some lines to my xorg.conf, reboot and whalla.

This is an awesome theme but it sure can be resource intensive.  I only have 1.2GHz Pentium M and 1 GB DDR2 RAM.  Just moving a window around jumps my CPY usage to about 70%-80%. :(  But I love it too much to get rid of it.  Heck I have no clue how to uninstall it. lol

---

