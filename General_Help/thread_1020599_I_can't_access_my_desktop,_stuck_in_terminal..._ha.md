---
title: "I can't access my desktop, stuck in terminal... hardy heron"
date: 2008-12-24
forum: General Help
---

### Post by Johnny-Cache on 2008-12-24
Hi,

I've had hardy heron running for several months and all of a sudden it just craps the bed.  It boots to the login screen, but when I sign in I get the error message "seahorse and librsvg2-common and librsvg2-2 are doing bad things" ....or something like that...  

I removed and reinstalled all three of those things.

still no desktop access

I then thought maybe my gnome desktop pooped so I installed KDE.

Now when I log in, the screen goes black for a second then comes back to the login prompt like nothing happened.

if I change the session to terminal access and try startx I and error that says "FreeFontPath: FPE .... refcount is 2, should be 1; fixing"  But everything I read says it's a non-critical error.  I was getting a gnome_keyring_ error when I used the gnome desktop, but not with kubuntu.

Bottom line:  I either need to figure out how to get back in to my desktop OR find a way to reinstall ubuntu/kubuntu without losing my data in my home directory.

I'm sure you will need more info about my system, but I don't know what to show ... still a ubuntu N00B :)

Thanks!

---

### Post by LowSky on 2008-12-24
sounds like your xorg.conf file is messed up. try botting into recovery mode and fixing xorg

---

### Post by Johnny-Cache on 2008-12-24
I did apt-get install --reinstall xorg

it ran successfully, but still did not work...

---

### Post by Johnny-Cache on 2008-12-24
and not really sure how to manually edit the xorg.conf

---

### Post by iponeverything on 2008-12-24
At grub boot menu, choose recovery mode and run xfix from the recovery menu.

---

### Post by zeronothing on 2008-12-24
if the recovery doesnt work try using this command.

sudo dpkg-reconfigure xserver-xorg

this will hopefully reconfigure the xserver but selecting the recovery mode during boot should do the trick..

---

### Post by Johnny-Cache on 2008-12-24
-bash: xfix: command not found
I'm still stuckk

------edit
I'm dumb, I remembered where I seen xfix right after I posted this...

Still didn't work though

---

### Post by Johnny-Cache on 2008-12-30
Thanks for the help and the back logs of this forum.  I have fixed my problem.  Lessons learned:

The install disks for all Linux are very open to errors which will confuse any A+ guy.  Burn it slow and use the same cd drive to boot it up.

I booted off the liveCD for ubuntu with an extra hard drive installed that was formated to NTFS.  I then had to force mount it by 
$sudo mount -t ntfs /dev/sdb1 /media/disk2 -o force

my system then thanked me for being cool.

---

