---
title: "more lib issues"
date: 2005-12-06
forum: Desktop Environments
---

### Post by hollowhead on 2005-12-06
I'm trying to install yet another CAD program.  It came as a an rpm which I turned into a deb using alien then ran dpkg -1 then discovered it contained a tar.gz file and was not a binary.  Unpacked it cd to the dir ran /.configure and got this error at the end (see below).  Errors always seem to turn up at the end.  Ta.

I haven't a clue what this is on about can anyone enlighten me on how to resolve this issue.
checking for gtk-config... no
checking for GTK - version >= 1.0.1... no
*** The gtk-config script installed by GTK could not be found
*** If GTK was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the GTK_CONFIG environment variable to the
*** full path to gtk-config.
configure: error: Test for GTK failed. See the file 'INSTALL' for help

---

### Post by Ampersand on 2005-12-06
Try getting the libgtk1.2-dev and libgtk2-dev packages. Generally when a configure script can't find a library, you can just install the -dev package for it to solve it.

Also, did you try useing dpkg -i first?

---

### Post by hollowhead on 2005-12-06
Thanks for your prompt reply I will try installing the above.  I do find the lib issue confusing and its definitely got worse over the years.  I posted on another lib for CAD software problem a week ago.  I think I solved this the lib was present all along, however, the webpage for the program called it something slightly different from what it is called on my system. I'm sorry for anyone that replied to this not to havethanked you but I cannot find any of my posts on the newsgroup they don't turn up using the search tool.  Anyway this program runs but is half in english and german and I cannot work out how to use it.  Hence my attempts with other ones.

While we are talking about dpkg and alien I have found a problem with alien (maybe its just me doing something wrong) if I run sudo alien -i mypackage.rpm the program makes a pretence of installing but dosen't!  So for example I cannot get the tar.gz version of acrobat to install at all so I downloaded the rpm version.  Running alien as above added an acrobat icon to my gnome menu but nothing happened since it wasn't really installed.  I poked around the web and tried sudo alien -k mypackage.rpm.  This creates a deb file which I install in the normal way.  It all then shows up in synaptic which is very nice.  Its livable with but slightly irratating.  Sorry about the length of post.  Hollowhead.

---

### Post by hollowhead on 2005-12-06
Thanks ampersand that got the program past configure.  I shall remember your advice. Some errors? (same ones) came up during make and make install (not many) but I cannot find a biniary file to exec!  I posted the errors to the sagcad developers newsgroup.

---

