---
title: "Started insalling Kiba... messed up... need to remove and stat over..."
date: 2008-04-12
forum: Desktop Effects &amp; Customization
---

### Post by JZeFF on 2008-04-12
EDIT:  Im using Compiz Fusion..  ubuntu 7.10   And trying to install the 32 bit version

Well i was using this guide
[http://ubuntuforums.org/showthread.php?t=554127](http://ubuntuforums.org/showthread.php?t=554127)
And about half way through im pretty sure i messed up..  right around this part
"Next just do the following - Typing each line at a time"
I kept typing them one after another.. and in the end it didn't come up right.  It wouldnt even start....


Well ive done all i can think of to try and remove everything kiba related, but i just cant do it...  When i hit Applications/Accessories... there is still Kiba-Dock and Kiba-settings

But neither of them work...
Any suggestions please?   im relatively new to Ubuntu and linux in general..

EDIT:   When i get to typing this in terminal

"
cd akamaru/
./autogen.sh --prefix=/usr --exec-prefix=/usr
sudo make install
cd ..
"

It tells me this in return..

"
jeff@jeff-ubuntu:~$ cd akamaru/
bash: cd: akamaru/: No such file or directory
jeff@jeff-ubuntu:~$ ./autogen.sh --prefix=/usr --exec-prefix=/usr
bash: ./autogen.sh: No such file or directory
jeff@jeff-ubuntu:~$ sudo make install
make: *** No rule to make target `install'.  Stop.
"

---

### Post by JZeFF on 2008-04-12
I spent a good amount of time last night trying to figure it out myself... i just am not good enough in ubuntu to do it...


EDIT:  Under Applications/Accessories   it still shows Kiba-Dock and Kiba-Configure    But if i go to add/remove programs and do a search it does not find anything for Kiba-dock
And if i just do a system search it does not find anythign either...   I have moved all the folders used to try and get it installed to the trash, but it will not let me delete them...

Im still trying... just not getting anywhere =/

The error message i get while trying to delete it    
"
"/home/jeff/.../akamaru.o" cannot be deleted because you do not have permissions to modify its parent folder
"

After more screwing around..  trying to run through the install process again, and taking the files back out of the trash

"
jeff@jeff-ubuntu:~$ kiba-dock

** (process:8242): WARNING **: Error (main.c @ line 126):
        Failed to locate Plugins at '/usr/lib64/kiba-dock'
Please install the Plugins at '/usr/lib64/kiba-dock' or use the '--plugin-path' command line parameter.

        For a core dump, run kiba-dock with --g-fatal-warnings.
"

gah.....

---

