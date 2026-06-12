---
title: "Revert to Python 2.5 from 3.0"
date: 2009-02-09
forum: General Help
---

### Post by JJErtai on 2009-02-09
Hello, somewhat ashamed to admit that the cause of my problem was myself, but I guess everyone is new to linux at some point and makes mistakes :)

To cut a long story short, I decided I'd install Python 3.0 on my ubuntu 8.10 system and get the latest pydev plugin for eclipse (updating that too, beyond the repository version to the current one at their website). Being new to ubuntu I followed a guide, and I think it changed a few bits and bobs around, installing python 3.0 and making it the default version. All was good and fine...

Until restarting the computer. Now Wicd has stopped functioning, won't load at all either on startup or via terminal. It gave some errors that pointed to the changes to the python code used, which suggests to me that that's where the problem lies.

Of course, I tried to revert my version of python by changing the usr/bin/python symlink to python2.5 as well as editing the usr/shared/python/debian_defaults file to point to 2.5 as the default version.

Now when I run Wicd from the terminal it says it's loading a .pn file (I think) and then just stops.

Any ideas how to completely revert back to 2.5 and get rid of any errors? I do not have internet access on the partition ubuntu is on because due to intel wireless drivers, wicd is the only thing that works. Hence, I can only install new features or download anything by copying across from windows.

Thanks for your time.
-JJ

---

### Post by JJErtai on 2009-02-09
FIXED:

Am writing this from Ubuntu so all fixed now. For anyone looking at this in the future after installing and making as default python3.0 on Ubuntu 8.10, this is how you fix broken wicd:

-make sure to point the usr/bin/python symlink to python2.5
-update usr/share/python/debian_defaults to point to python2.5 as default.
-reinstall wicd using the debian files downloaded from here: [http://sourceforge.net/project/showfiles.php?group_id=194573](http://sourceforge.net/project/showfiles.php?group_id=194573) and ran with:
sudo dpkg -i file.deb (run from directory you've put your .deb in :)
-relog

---

