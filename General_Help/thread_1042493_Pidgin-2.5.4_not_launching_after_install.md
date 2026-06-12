---
title: "Pidgin-2.5.4 not launching after install"
date: 2009-01-17
forum: General Help
---

### Post by maphco on 2009-01-17
I installed the new version of pigin and compiled it like it instructed on the website

[http://developer.pidgin.im/wiki/Installing%20Pidgin#Compiling](http://developer.pidgin.im/wiki/Installing%20Pidgin#Compiling)

I downloaded and extracted the pidgin-2.5.4.tar.bz2 file onto my desktop and then followed the instructions.

The executable is found in /usr/local/bin

Should I move the files on the desktop to a new location?

(P.S. Sorry if this was the wrong place to place this question.)

---

### Post by maphco on 2009-01-17
Could someone tell me where their pidgin files are installed on their computer so I could try moving the files there and see if it works that way?

---

### Post by Arup on 2009-01-17
Did you remove the older Pidgin before installing this one?

---

### Post by maphco on 2009-01-17
Yes, I ran sudo apt-get remove pidgin.

---

### Post by Arup on 2009-01-17
It would have been better to do a --purge as you need to remove libpurple and pidgin-data as well.Can you type pidgin in terminal and get it working?

---

### Post by maphco on 2009-01-17
Typing pidgin gives this

pidgin: symbol lookup error: pidgin: undefined symbol: purple_smileys_get_all

Do you know how I can remove all the files that "make install" installed on my computer then I can run that purge command?

Also, how would I run the purge command?

---

### Post by maphco on 2009-01-17
I got rid of the files I extracted on the desktop and extracted them to my home folder.

I also reinstalled pidgin using "sudo apt-get install pidgin" then used "sudo apt-get remove --purge pidgin"

Then redid what it says to do on the pidgin website.

EDIT: still didn't work.

---

### Post by maphco on 2009-01-17
Help please :(

---

### Post by -jay- on 2009-01-18
uninstall it & try using the deb from here

> [http://www.getdeb.net/app/Pidgin](http://www.getdeb.net/app/Pidgin)


this worked for me

---

### Post by kevdog on 2009-01-18
Here is a guide for ubuntu how to install pidgin.  [http://ubuntuforums.org/showthread.php?t=975783](http://ubuntuforums.org/showthread.php?t=975783)

Unless you specified a path with the ./configure --prefix=<path>
then by default all the executables are placed in the /usr/local tree, such as /usr/local/bin, rather than the /usr tree, such as /usr/bin.  If you keep with the convention, its very possible to have 2 pidgin installs on your machine, since both executables are located in different directories.  To find out which pidgin you may be using:

which pidgin

---

