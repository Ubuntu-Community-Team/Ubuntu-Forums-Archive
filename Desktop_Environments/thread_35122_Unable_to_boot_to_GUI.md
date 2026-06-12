---
title: "Unable to boot to GUI"
date: 2005-05-17
forum: Desktop Environments
---

### Post by NoTiG on 2005-05-17
I have a HUGE problem . my ubuntu linux 5.04 34 bit distro won't boot up into GUI. it was working fine and i booted it up ... and it failed on 3 processes:

art-stop daemon unable to start /sbin/klogd : permission denied [FAIL]
starting gnome display manager [FAIL]
starting deferred execution scheduler [FAIL]

IT won't boot into gui, so it boots into tty and asks for my log in but when i try it says:

"unable to cd to /home/notig"

wtf is this all about ?? it has nothing to do with my xorg.conf file... i tried backing that up. Usually when there is a problem with a computer somebody has posted the exact same problem but i searched and didn't find anything :(

I really dont expect anyone to actually help me fix this but just trying to see what the hell happened. I could reinstall but i would rather know wtf is going on ! .

EDIT: btw its not a hardware issue either... i have a working 64 bit distro on the second partiion and windows on the first.

---

### Post by lepetitalbert on 2005-05-17
hello,

do you checked the permissions in the /home/notig.

I had a similar prob and found files and folders in  /home
owned by root.
Gave the files/folders back to the user and it worked again.

Maybe ?!

Have anice day.

---

### Post by NoTiG on 2005-05-17
I just checked .. Nope... no files owned by root. 


THe only things i can think of:

Im trying to remember what i installed last. Nothing that i can remember :(

I was playing around with anjuta... maybe i compiled something and it over wrote memory somewhere?

OR 

i was playing around with my second partition. maybe when i installed.. and reinstalled grub to the mbr it did something ?

OR 

I cp'ed the xorg.conf file from my 32 bit distro to my 64 (the 32 on the third partition is the one that doesnt work) . So i mounted the 3rd partition and browsed etc.... maybe that accidentaly did something ? 

Okay here is a weird one: when i created a folder under /mnt called storage 

/mnt/storage

the problem was i couldnt change directory to storage.. it wouldnt let me . and 
sudo cd /mnt/storage .... doesnt work . so the only way i could access the /mnt/storage was by using the root terminal. HOWEVER . to try to fix that i chown and changed the owner of storage to notig.... while i had hda3 mounted .. maybe that did something . argh.

I dont know.. but isnt there a log file somewhere that might list recent changes that could be accounted for ?

---

### Post by nad on 2005-05-17
Ahhhh...  The trials and tribulations of running as root. The .bash_history file of each user is a great resource to try to get out of problems like this.

It certainly seems that you changed the permissions of something that you shouldn't have. Don't forget to check the group ownership of those names also.

---

### Post by Daicogra on 2005-08-10
Hi,
it's late... but maybe other people will have the same problem.
I had this problem, too. You should check if / had enough permissions.
After I changed it everything works fine.

/ --> 755 with root:root

---

