---
title: "Noob screwed up using root acct...."
date: 2008-12-30
forum: General Help
---

### Post by monde on 2008-12-30
I know...this is exactly what you are **not** supposed to do....anyways, I had set up a guest account, and wanted to change the permissions for the entire system such that the guest could not access any files aside from those in their home directory. Opened nautilus as root, went to the mountpoint (I think), right-clicked and tried to change the permissions, which worked except that.... All icons have disappeared, both in menus and on the desktop. I cannot load any applications, although firefox is still open and working perfectly. Clicking on any of the menu items produces no result. I am not sure how I would even get back to the folder preferences to change them back, as I cannot go anywhere....

I would rather not re-install Ubuntu.
If anyone has any other suggestions, they would be greatly appreciated.

Thanks!

---

### Post by gettinoriginal on 2008-12-30
Reboot > during grub splash, hit escape > Recovery mode > Enter (let finish)
Repair Broken Packages > Enter (if it asks about updates hit N) (let finish)
Try to fix X server > Enter (Let finish)
Resume normal Boot > Enter

---

### Post by clw3388 on 2008-12-30
Hello
not sure what you mean by mount point? maybe im dumb? if ya would elaborate..
In either case you can open a terminal from X or go to another terminal (control alt f6) log in as root and if i understand you right you can run 
chmod 775 / or chmod 775/*
this will reset the permissions on your (mount point?)

does anyone else understand?

---

### Post by Sin@Sin-Sacrifice on 2008-12-30
Or start using sudo in stead of logging in as root... sudo nautilus is good for moving files but that's about it. Everything else you should ascertain from experienced users and then do from terminal using sudo.

Post Script: If you want to change permissions of your files so that no one else can see them then change the permissions of /home/user not of the whole mount point or file system.

---

### Post by monde on 2008-12-30
> **gettinoriginal said:**
> Reboot > during grub splash, hit escape > Recovery mode > Enter (let finish)
Repair Broken Packages > Enter (if it asks about updates hit N) (let finish)
Try to fix X server > Enter (Let finish)
Resume normal Boot > Enter

Went through above steps...upon startup I am presented with the ubuntu splashscreen....I login, but then receive a message informing me that "GDM could not write to your authorization point...in any case, it is not possible to log in". (obviously I am on a different computer now)...

---

### Post by monde on 2008-12-30
> **clw3388 said:**
> Hello
not sure what you mean by mount point? maybe im dumb? if ya would elaborate..
In either case you can open a terminal from X or go to another terminal (control alt f6) log in as root and if i understand you right you can run 
chmod 775 / or chmod 775/*
this will reset the permissions on your (mount point?)

does anyone else understand?

By mountpoint I mean the highest directory....I unfortunately can't open terminal anymore, as I have restarted the computer and cannot login with any account. I tried your suggestion in the GRUB command line (which I have never used), but to no avail.

---

### Post by snova on 2008-12-30
> **monde said:**
> By mountpoint I mean the highest directory....I unfortunately can't open terminal anymore, as I have restarted the computer and cannot login with any account. I tried your suggestion in the GRUB command line (which I have never used), but to no avail.

So, you changed the permissions on the top level directory?

Boot a Live CD and fix them from there.

Booting into recovery mode might not work at this point, I'm unsure.

---

### Post by bgerlich on 2008-12-30
In recovery mode menu choose root terminal (?) and create a new user - useradd my_new_user , after that passwd my_new_user         

Now you can log in as my_new_user and either change your old home (!) dir permissions to suit your needs (user can read, write, others and group can not) or delete the old account and keep using the new one.

---

### Post by monde on 2008-12-30
> **snova said:**
> So, you changed the permissions on the top level directory?

Boot a Live CD and fix them from there.

Booting into recovery mode might not work at this point, I'm unsure.

I am downloading the iso...I am not sure that will work, as immediately after I changed the permissions, I attempted to revert them while still in ubuntu, but it didn't work....will wait a few hours for the dl to finish, then try again

---

### Post by monde on 2008-12-30
> **bgerlich said:**
> In recovery mode menu choose root terminal (?) and create a new user - useradd my_new_user , after that passwd my_new_user         

Now you can log in as my_new_user and either change your old home (!) dir permissions to suit your needs (user can read, write, others and group can not) or delete the old account and keep using the new one.

created new account, but a login attempt brought up the same "GDM could not write..." message.

Thanks to all for your suggestions - keep 'em coming!

---

### Post by bgerlich on 2008-12-30
try one more thing - chmod 777 /tmp

---

### Post by monde on 2008-12-30
Everything seems to be back to normal....a very heartfelt thanks to everyone....you have saved me a ton of time in reinstalling ubuntu and apps. etc.

Thanks!

:D

---

