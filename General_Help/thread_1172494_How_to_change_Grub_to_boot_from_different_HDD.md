---
title: "How to change Grub to boot from different HDD"
date: 2009-05-28
forum: General Help
---

### Post by roundhay on 2009-05-28
I have 4 HDD in my PC:

sda - Has Ubuntu 8.10 installed

sdb - storage drive

sdc - has Ubuntu 9.04 installed

sdd - a second storage drive

The Grub boot file is curently installed on HDD sda and I have updated it so that I can dual boot as start up. However if I don't choose to boot into 9.04 8.10 boot automatically. I would like to chnage this so that 9.04 boots automatically. Ideally I would like the Grub file to be on HDD sdc

Does anyone know how I can do this?

---

### Post by celticbhoy on 2009-05-28
To change your default startup, 

open a terminal
type 'cd /boot/grub' without quotes
type 'cp menu.lst menu.bak'
type 'sudo gedit menu.lst' & enter password when prompted

[QUOTE]# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		15
/QUOTE]

Look for the line like the above code that says default = 0

now is the bit you need to think, default=0 means boot from grub entry 1
so default=1 means grub entry 2 and so on.

now look down the file to your list of entries count down the entry number you want to use for default and take one away, then change the default = setting at the top of the file and save.

The only problem with this is that if you get a kernel update it will knock it all for six!

A better idea is to install startup-manager from the repo's and tell it what entry to use for default, you can also tell it how many kernels to keep and display so that when you have a kernel update it all still works.

---

### Post by celticbhoy on 2009-05-28
With regards to using grub from the other partition, you have to run

sudo grub

from a terminal and run the following commands

root (hd2,0)
setup (hd2)

if all goes well then you are done and you can quit.

You would then need to check your grub entry to ensure that you had listing for your other OS.
If you can understand my babble and it all goes well post back and I will try and help you add the missing entries.

---

### Post by celticbhoy on 2009-05-28
With regards to using grub from the other partition, you have to run

sudo grub

from a terminal and run the following commands

root (hd2,0)
setup (hd2)

if all goes well then you are done and you can quit.

---

### Post by ajgreeny on 2009-05-28
You could also probably just boot into 9.04 and then run ```
sudo grub-install /dev/sdc
```
Don't forget that depending on the order in which you installed the OSs, you may not have an entry for both Ubuntu installs in the /boot/grub/menu.lst file in both versions of Ubuntu.  You can easily edit either or both so that is not a show-stopper, just something to consider so you are not shocked if you see no way to boot to the other version.

---

### Post by celticbhoy on 2009-05-28
Every day is a school day!

---

