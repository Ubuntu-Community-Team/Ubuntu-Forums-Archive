---
title: "Nautilus - mount at login?"
date: 2009-06-22
forum: General Help
---

### Post by JordyD on 2009-06-22
I've used "Connect to server..." to connect to a SAMBA share we have, and it works fine, but I'd like to know if there is a way to get nautilus to mount it when I log in, instead of when I click the bookmark. Does anybody know how to do it, or if it's even possible?

Thanks,
Jordy

---

### Post by aesis05401 on 2009-06-22
This should be pretty simple.  This link should do it for you:

[http://justlinux.com/nhf/Filesystems/Mounting_smbfs_Shares_Permanently.html](http://justlinux.com/nhf/Filesystems/Mounting_smbfs_Shares_Permanently.html)

---

### Post by JordyD on 2009-06-22
> **aesis05401 said:**
> This should be pretty simple.  You need to create a local mountpoint and an entry in fstab.

This link should do it for you:

[http://justlinux.com/nhf/Filesystems/Mounting_smbfs_Shares_Permanently.html](http://justlinux.com/nhf/Filesystems/Mounting_smbfs_Shares_Permanently.html)

I had played with this before, but the main reason I stuck with the GNOME built-in "Connect to Server" option is that the username and password to connect to the share with would have to be stored in fstab. Plus, I don't want the share to mount if a different user logs in, because the credentials are different per user. I tried using $HOME and ~ in the /etc/fstab file along with a credentials file, but it mounts things before you log in, so the $HOME variable is not set.

I guess I should have put that in my OP.

Thanks for the response, by the way.

---

### Post by aesis05401 on 2009-06-22
Maybe I am not fully understanding.  You shouldn't use $HOME in fstab.

Did you try:
```

#credentials added to new file .smbpasswd in home directory
echo username=mywindowsusername > .smbpasswd
echo password=mywindowspassword >> .smbpasswd
chmod 600 .smbpasswd

#fstab entry hardcoded to credentials file
//servername/sharename /mountdirectory smbfs credentials=/home/myhomedirectory/.smbpasswd 0 0

```

That should work without using environment variables, right?

Edit: the chmod 600 .smbpasswd is your security mechanism... Only you and root can read the file, each user has their own version in their own home folder providing localization right from the get go.

---

### Post by JordyD on 2009-06-22
> **aesis05401 said:**
> Maybe I am not fully understanding.  You shouldn't use $HOME in fstab.

Did you try:
```

#credentials added to new file .smbpasswd in home directory
echo username=mywindowsusername > .smbpasswd
echo password=mywindowspassword >> .smbpasswd
chmod 600 .smbpasswd

#fstab entry hardcoded to credentials file
//servername/sharename /mountdirectory smbfs credentials=/home/myhomedirectory/.smbpasswd 0 0

```

That should work without using environment variables, right?

Edit: the chmod 600 .smbpasswd is your security mechanism... Only you and root can read the file, each user has their own version in their own home folder providing localization right from the get go.

This would work, but what about other users on my system? If I use /home/jordy/.smbpasswd, then when somebody else logs in, they have a SAMBA share mounted with my credentials, no?

Isn't everything in fstab mounted before login with root permissions?

---

### Post by aesis05401 on 2009-06-22
> **JordyD said:**
> This would work, but what about other users on my system? If I use /home/jordy/.smbpasswd, then when somebody else logs in, they have a SAMBA share mounted with my credentials, no?

Isn't everything in fstab mounted before login with root permissions?

fstab is the right place to set user permissions for network shares.  

Unfortunately, we need someone more versed in fstab to say whether the chmod 600 applied to my example credentials file will result in only you and root having access to the share (as I thought it would).

If not, there are ways to pass user permission args in fstab entries, and I believe this is the reccommended way to hardcode network share permissions.. ie: at the root level.

I could be wrong.  Here is one link that I have bookmarked, but have not taken the time to fully research or understand:[http://linux.about.com/od/linux101/l/blnewbie4_2_6.htm](http://linux.about.com/od/linux101/l/blnewbie4_2_6.htm)

I guess I am as interested in the correct answer as you are at this point ;)

---

### Post by aesis05401 on 2009-06-22
Wow, 'man fstab' answers all.  I can't believe I hadn't read that file before now.  

I followed the 'mntops' reference from fstab page to man mount page and find that permissions on mounts can be specified by where you chmod the 'special file' either at user or group level... With 'special file' being the device file.

Hrm.. we still need an expert ;) But long story short it appears you just need to pass the 'owner' argument in your fstab line (maybe google for an example) and then be sure to have the point you are mounting owned by you.

Alternately, you could pass the 'group' arg in fstab, and it would allow you and any users you added to your group to access the share (again, if you set the right permissions on the mount).

Can someone confirm this ;)

---

### Post by Jowi-real on 2009-07-09
Hello,

I was thinking about this myself and - found a solution!
The magic command is "gvfs-mount". There's no need to mess with fstab anymore! 

In my case, I have a [Buffalo Linkstation mini]("http://www.buffalotech.com/products/network-storage/linkstation/linkstation-mini/") that I need to automatically mount when I log in.

Ok, it's quite straight forward:

1. Open the share normally and set nautilus to remember the password "forever" if you need.
2. Create a new file anywhere in your home directory (I call it "mount-linkstation" and placed it in $HOME/bin/) with the following information:

```
sleep 20 && gvfs-mount smb://linkstation/mysharefolder/
```
*Note: since this computer automatically connects to the network via wifi, and it takes awhile before it becomes available, is why I have put a sleep before the command*

3. save the file
4. make it executable by either "chmod +x mount-linkstation" or right click on it, select properties, go to the permissions tab and select the executable checkbox.
5. Now, if you have already mounted the smb share unmount it. Execute the "mount-linkstation" file to see that it works properly.
6. Go to System > Preferences > Startup Applications
7. Create a New entry and select the "mount-linkstation" file.

Log out and Log in again
It worked for me(tm)

P.S. for some unknown reason it didn't work for me if I put in the gvfs-mount directly in the startup applications. I had to create an executable file for it...

edit: To make it user specific you should be able to place the executable in /usr/bin and have a script like this:

```
#!/bin/bash
# Mount smb share when user logs in
USER=$(whoami)
gvfs-mount smb://servername/$USER/
```

---

### Post by JordyD on 2009-07-10
> **Jowi-real said:**
> Hello,

I was thinking about this myself and - found a solution!
The magic command is "gvfs-mount". There's no need to mess with fstab anymore! 

In my case, I have a [Buffalo Linkstation mini]("http://www.buffalotech.com/products/network-storage/linkstation/linkstation-mini/") that I need to automatically mount when I log in.

Ok, it's quite straight forward:

1. Open the share normally and set nautilus to remember the password "forever" if you need.
2. Create a new file anywhere in your home directory (I call it "mount-linkstation" and placed it in $HOME/bin/) with the following information:

```
sleep 20 && gvfs-mount smb://linkstation/mysharefolder/
```
*Note: since this computer automatically connects to the network via wifi, and it takes awhile before it becomes available, is why I have put a sleep before the command*

3. save the file
4. make it executable by either "chmod +x mount-linkstation" or right click on it, select properties, go to the permissions tab and select the executable checkbox.
5. Now, if you have already mounted the smb share unmount it. Execute the "mount-linkstation" file to see that it works properly.
6. Go to System > Preferences > Startup Applications
7. Create a New entry and select the "mount-linkstation" file.

Log out and Log in again
It worked for me(tm)

P.S. for some unknown reason it didn't work for me if I put in the gvfs-mount directly in the startup applications. I had to create an executable file for it...

edit: To make it user specific you should be able to place the executable in /usr/bin and have a script like this:

```
#!/bin/bash
# Mount smb share when user logs in
USER=$(whoami)
gvfs-mount smb://servername/$USER/
```

Neat. But couldn't you just throw 'gvfs-mount smb://linkstation/mysharefolder/' into the startup applications, instead of creating the executable and all that?

Thanks, by the way. This fixes my problem.

---

