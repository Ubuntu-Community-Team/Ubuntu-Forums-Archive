---
title: "Conky Help"
date: 2007-08-31
forum: Desktop Effects &amp; Customization
---

### Post by derekr44 on 2007-08-31
So I'm following the instructions listed [here](http://ubuntuforums.org/showthread.php?t=205865&highlight=conky), but am stuck in a very simple spot...

> sudo checkinstall

Results in checkinstall not being a valid command and:

> gedit /home/derek/.conkyrc

Gives me an error saying that gedit cannot interpret the file for edit, ends up asking me to use UTF-8 or Western... which neither works anyway.  Opening it in nano (of course) results in all sorts of junk because .conky is apparently binary...

So where do I go from here?

---

### Post by testube_babies on 2007-08-31
The version of conky in the repositories is newer than the version in the tutorial.  Just 'sudo apt-get install conky' to get it.  If you want to that method anyway, you'll need to install checkinstall with 'sudo apt-get install checkinstall'.

.conkyrc being a binary makes no sense.  You should be able to safely rename it so that you can create your own .conkyrc as a text file.

---

