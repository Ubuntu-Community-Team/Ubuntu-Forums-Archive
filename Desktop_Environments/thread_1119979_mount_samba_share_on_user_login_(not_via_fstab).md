---
title: "mount samba share on user login (not via fstab)"
date: 2009-04-08
forum: Desktop Environments
---

### Post by StuffedLion on 2009-04-08
Hi,

I run a samba PDC (using ubuntu 8.10) that serves some shared folders to a small windows network (and handels logins, profiles etc) but users can also login on the Ubuntu PDC istelf and work with gnome.

Now it showed to be quite difficult to find a way that users can also use the shared folders when they work on the PDC itself. I want them to find a similar user experience like when they sit in front of there windows client. i.e. they should find a (network) drive symbol for the shared folders, either on the desktop or at least in nautilus. And of course everyone has to have full access to the shared files.

I think the only way to do this is to mount the shared folders via cifs every time a user logs into his or her user account. How can I do this? Is there a way to do it? Pls help! :)

First I tried to mount the samba shares via fstab. However, this can not work since on startup "mount -a" is done bevore the samba server even starts. yes, I could alter the starting order but I rather don't want to mess with the init...

Then I tried to simply bind the folders in questions via fstab into a folder in /media. However, unlike when you mount any drive or network share into /media you wont get a drive icon on the desktop when only binding a folder. That sucks. There is no help in having these folders binded into /media as long as users can not find them (since they have no idea about where to look).

Third I added a softlink into each users home directory that would lead them to the coresponding shared folder. However, that also wont work well. I did set the sgid bit on the folders and when a user creates a new file in the shared folder it gets the correct user group (i've set up a user group for all user of the domaene) so that others can have full access to those files. But when someone copys an existing file into that directory his or her usergoup sticks to it and no one else can work with this files. Furthermore, since user now have folders that contain all shared files in there home dir, I fear someone could delete everything, thinking he would only delete his own files...

Thats why I believe the only thing that would help is if there is a way to mount the shared folder on logon. How can I do that?

thanks
Lion

---

### Post by StuffedLion on 2009-04-11
bump?

---

### Post by mc_scRAT on 2009-09-29
Strange, but I got this in my fstab:
//192.168.0.1/mc_scrat /home/mc-scrat/smbmount/ cifs user,credentials=/home/mc-scrat/&#1044;&#1086;&#1082;&#1091;&#1084;&#1077;&#1085;&#1090;&#1099;/smbmount,uid=mc-scrat,gid=mc-scrat,iocharset=utf8,file_mode=0600,dirmode=0700 0       0
and have no mount problems - the mountpoint if in the wireless network and via samba, so it only mounts when I got in my home network and server is on. no problem
but there's another question: how 'bout to mount it when I log-in (as posted in the header)??
another way of saying it: I know what command/script to make/write to make it true. but where to insert this script? what actions made under root privileges when user logs-in??

---

### Post by doas777 on 2009-09-29
it seems that connecting via the System -> Sessions list (Startup Applications in intrepid forward) should do it, right?

---

### Post by mc_scRAT on 2009-10-02
> **doas777 said:**
> it seems that connecting via the System -> Sessions list (Startup Applications in intrepid forward) should do it, right?
guess only in case of noauto and user strings in fstab. I I'll try it now

---

### Post by kgas on 2009-10-02
have you tried to mount the share with mount.cifs command?(try to put a small function in .bashrc of the user to check the share is available if so mount it)

---

### Post by karlson on 2009-10-02
> **StuffedLion said:**
> Hi,

I run a samba PDC (using ubuntu 8.10) that serves some shared folders to a small windows network (and handels logins, profiles etc) but users can also login on the Ubuntu PDC istelf and work with gnome.

Now it showed to be quite difficult to find a way that users can also use the shared folders when they work on the PDC itself. I want them to find a similar user experience like when they sit in front of there windows client. i.e. they should find a (network) drive symbol for the shared folders, either on the desktop or at least in nautilus. And of course everyone has to have full access to the shared files.

I think the only way to do this is to mount the shared folders via cifs every time a user logs into his or her user account. How can I do this? Is there a way to do it? Pls help! :)

First I tried to mount the samba shares via fstab. However, this can not work since on startup "mount -a" is done bevore the samba server even starts. yes, I could alter the starting order but I rather don't want to mess with the init...

Then I tried to simply bind the folders in questions via fstab into a folder in /media. However, unlike when you mount any drive or network share into /media you wont get a drive icon on the desktop when only binding a folder. That sucks. There is no help in having these folders binded into /media as long as users can not find them (since they have no idea about where to look).

Third I added a softlink into each users home directory that would lead them to the coresponding shared folder. However, that also wont work well. I did set the sgid bit on the folders and when a user creates a new file in the shared folder it gets the correct user group (i've set up a user group for all user of the domaene) so that others can have full access to those files. But when someone copys an existing file into that directory his or her usergoup sticks to it and no one else can work with this files. Furthermore, since user now have folders that contain all shared files in there home dir, I fear someone could delete everything, thinking he would only delete his own files...

Thats why I believe the only thing that would help is if there is a way to mount the shared folder on logon. How can I do that?

thanks
Lion

Have you looked at automounter on Ubuntu instead of using Samba?  Or are the shared folders on a Windows Machine?

---

### Post by Gonz-IT on 2009-11-09
Use the small app named:

nautilus-connect-server

Make sure you check the "Add a Bookmark" checkbox.

Now everytime you login you just have to clic on the share name in your bookmarks list (Nautilus) and the share will be automounted.

To be able to browse this shares from applications, just run:

 ln -s .gvfs/ Shares

And you will always have a Shares folder in your home where every mounted filesystem is browseable.

Gnome rocks, it's just not very well documented sometimes, or the documentation is not created having the Windows network typical scenarios in mind.

---

