---
title: "Strange Apt Error"
date: 2006-07-24
forum: Desktop Environments
---

### Post by XAsmodeanX on 2006-07-24
I haven't done anything out of the ordinary apt-wise and I just ran this command and got this output:

xasmodeanx@archangel:~$ sudo apt-get install xine-ui
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  xine-ui
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 1606kB of archives.
After unpacking 3596kB of additional disk space will be used.
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe xine-ui 0.99.4-0ubuntu6 [1606kB]
Fetched 1606kB in 54s (29.6kB/s)                                               
(Reading database ... 
dpkg: serious warning: files list file for package `example-content' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `festival' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `fdutils' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `gtkhtml3.8' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `fastjar' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `festlex-cmu' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `festvox-kallpc16k' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `festlex-poslex' missing, assuming package has no files currently installed.
157645 files and directories currently installed.)
Unpacking xine-ui (from .../xine-ui_0.99.4-0ubuntu6_i386.deb) ...
Setting up xine-ui (0.99.4-0ubuntu6) ...


Any idea on what that is and how to fix it?

---

### Post by catlett on 2006-07-24
Run ```
sudo aptitude update
``````
 sudo aptitude upgrade
```If no errors are returned then don't worry about it. If the same errors appear-then you may want to try uninstalling xine-ui and then re-installing xine-ui. I am assuming this error first occurred when you ran apt-get install xine?
I do not know that error. I would assume the package somehow got corrupted or didn't download entirely. It appears apt was opening the tar file and couldn't find what it expected to find.
But if aptitude doesn't come up with any errors, I wouldn't worry about it. 
FYI...aptitude is another front end for apt. I prefer it because aptitude deals with dependencies better than apt-get as well as it will uninstall any dependencies that were installed with a particular package. Whereas apt-get will just uninstall the package and leave the dependencies. And aptitude will try and resolve dependencies where apt-get will just say package broken.

---

### Post by XAsmodeanX on 2006-07-24
Still got the same error.  It updated the lists, downloaded some updates, and then threw out the same errors but went ahead and installed all the updates.  It doesn't seem that this is connected to xine-ui.

Edit:
Problem was fixed by re-downloading and reinstalling all of the "broken" packages as described above.  What a weird thing to just happen out of the blue.

---

### Post by catlett on 2006-07-24
Seems like you answered your own problem. I never saw an error like that. At least it was fixable and not something to bring your system down. I'm still surprised because apt has always been rock solid for me. I never had an issue with how it retrieved packages and installed them. I still think it must have to do with apt untarring the file and not finding those packages when it was esxpecting top.
Well at least you solved it and if it happens to someone else, the solution appears to be- reinstall the packages listed in the error.

---

