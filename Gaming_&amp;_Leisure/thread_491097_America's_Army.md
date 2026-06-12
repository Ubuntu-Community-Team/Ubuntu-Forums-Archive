---
title: "America's Army"
date: 2007-07-03
forum: Gaming &amp; Leisure
---

### Post by gogreenpower on 2007-07-03
hello,

i have been using ubuntu 7.04 since its release which is also my total linux time and i can manage most things but i cannot figure out how to install americas army, i have downloaded the linux 2.5 run file but just not having any luck installing it, any help for a linux newbie would be appreciated

---

### Post by Howler9443 on 2007-07-03
There are a couple of things to try. 

First make sure that the file is executable. You can do this by issuing the following command

user@localhost>ls -la

On the left side are the permissions for the files. The America's Army file should have an 'x' or three listed. This indicates that the file is executable by owner,group and world.  If this is not the case you can issue the following command.

user@localhost>chmod +x <america's army file name goes here>

Don't include the brackets.  This command sets the file you name to executable.

Once thats done you can then issue the following command.

user@localhost> ./<America's Army file name goes here>

Please note that there is a "./" (dot and a slash) that simply tells the command line to look in the current directory  before exploring the set path and execute the file named.

I hope this helps.

---

### Post by gogreenpower on 2007-07-03
worked a treat thank you

---

### Post by Howler9443 on 2007-07-03
Glad I could help!

---

