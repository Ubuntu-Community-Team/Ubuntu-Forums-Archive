---
title: "Resetting ubuntu without reinstalling"
date: 2009-06-22
forum: General Help
---

### Post by saltynay on 2009-06-22
My optical drive is broken and I do not have a thumb drive. I want to take ubuntu back to default uninstalling all the extra packages and applications I have in only a few steps. I have a reasonable grasp of linux and using the terminal but can't seem to write a code which will enable me to do what I want. If at all possible I would like to keep my personal preferences.

---

### Post by Cheesemill on 2009-06-22
First create the following script (you can use gedit):
```

#! /bin/sh
TEMPFILE=`tempfile`
cat /var/log/installer/initial-status.gz | gzip -d |grep '^Package:' | awk '{ print $2}' > $TEMPFILE
aptitude search -F %p '~i!~M' | awk '{ print $1}' | grep -v -F -f $TEMPFILE
rm $TEMPFILE

```and save it as installedpackages.sh in your home folder. Then open a terminal and do:
```
chmod +x installedpackages.sh
./installedpackages.sh > toremove
```

This will give you a text file which contains a list of all of the packages you've installed. Then run the following command:
```
cat toremove | xargs sudo apt-get purge -y -s
```This will simulate the actions that apt-get will take. If you're happy with the results then run the above command again but without the -s
If all goes well you can then do:
```
sudo apt-get autoremove
``` to get rid of any dependencies that are no longer needed.

Any packages that show up in the simulation that you don't want to remove (for example kernels or graphics drivers) you can remove from the toremove file before proceeding.

Qudos to boga for providing the original script in this thread:
[http://ubuntuforums.org/showthread.php?t=576629](http://ubuntuforums.org/showthread.php?t=576629)

---

### Post by saltynay on 2009-06-22
I created the file but
```

chmod +x installedpackages.sh
./installedpackages.sh > toremove
```

is not doing anything

---

### Post by Cheesemill on 2009-06-22
Yes it is, it's creating a file in your home directory called toremove which contains a list of the packages you've installed. If you do a
```
cat toremove
```
you can see the contents of the file.

---

### Post by saltynay on 2009-06-22
Sorry should of explained it created that file but it was empty thus none of my packages are being removed...

nvm just tried again and it work :) thankyou

---

### Post by saltynay on 2009-06-22
nope didn't work :( it said it was going to purge everything but never did. Trying again...

I think I have fixed it by adding --force-yes

```
cat toremove | xargs sudo apt-get purge -y --force-yes
```

---

### Post by Cheesemill on 2009-06-22
I've never used the script for this purpose myself, I use it for keeping a list of installed packages for easy re-installation when I re-install Ubuntu (see the original thread I linked to above).

I just tried to adapt it to your needs so I'm probably not the best person to troubleshoot it :)


Edit - You could try substituting apt-get for aptitude, it sometimes handles package removal better (it will also automatically remove unneeded dependencies, so no need for apt-get autoremove afterwards).

---

### Post by saltynay on 2009-06-22
Yay atleast I now have ubuntu completely removed :) your coding is a ubuntu killer. No worries though I prefer maryan got any ideas on how to install a live disk via external he'd

---

### Post by geirha on 2009-06-22
There are many ways of installing Ubuntu. See [https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

---

### Post by saltynay on 2009-06-22
Well to be honest I loathe ubuntu so being lost of it is not so bad.

---

### Post by aspartam on 2012-02-21
> **Cheesemill said:**
> First create the following script (you can use gedit):
```

#! /bin/sh
TEMPFILE=`tempfile`
cat /var/log/installer/initial-status.gz | gzip -d |grep '^Package:' | awk '{ print $2}' > $TEMPFILE
aptitude search -F %p '~i!~M' | awk '{ print $1}' | grep -v -F -f $TEMPFILE
rm $TEMPFILE

```and save it as installedpackages.sh in your home folder. Then open a terminal and do:
```
chmod +x installedpackages.sh
./installedpackages.sh > toremove
```

This will give you a text file which contains a list of all of the packages you've installed. Then run the following command:
```
cat toremove | xargs sudo apt-get purge -y -s
```This will simulate the actions that apt-get will take. If you're happy with the results then run the above command again but without the -s
If all goes well you can then do:
```
sudo apt-get autoremove
``` to get rid of any dependencies that are no longer needed.

Any packages that show up in the simulation that you don't want to remove (for example kernels or graphics drivers) you can remove from the toremove file before proceeding.

Qudos to boga for providing the original script in this thread:
[http://ubuntuforums.org/showthread.php?t=576629](http://ubuntuforums.org/showthread.php?t=576629)

i wanted to get the list what i have installed, to make a sh script which is able to install everything to me... many thanks!

---

