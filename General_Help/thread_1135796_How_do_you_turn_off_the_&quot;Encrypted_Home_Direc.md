---
title: "How do you turn off the &quot;Encrypted Home Directory&quot; feature in 9.04?"
date: 2009-04-24
forum: General Help
---

### Post by somafm on 2009-04-24
I did a fresh install of 9.04, and saw the option to "Encrypt your home directory in case your computer is stolen. The folder contents will be decrypted automatically when you log in.. etc.etc...".

I thought this was a decent idea at first; however, whenever I am not logged onto the computer, my apache2 server returns "Forbidden 403" error messages on all pages. When I log back in, everything is perfectly fine again.. so I think it has to do with this whole "encrypted home directory" feature because my web server files are stored in: /home/user/public_html/

I would prefer to keep my web server pointing to that directory, and just turn off the encrypted home directory. It's really the only thing different I have tried from previous Ubuntu installs.

Short story: How do you turn off the encrypted home directory feature that can be enabled when you install Ubuntu 9.04?

Thanks!

---

### Post by somafm on 2009-04-26
Bump, any ideas?

---

### Post by Le Rob on 2009-05-17
I ripped my hair out over this. I'd be curious to know the answer, too.

EDIT: It's simpler than you think. Simply:

```
>$ rm ~/.encryptfs
```.

---

### Post by capped on 2009-07-14
I realize this thread has been dead for some time now - but i googled the problem and it came up first. I've had problems using public key authorization with ssh - while having an encrypted home directory.

I figured out how to decrypt your home directory: (not an expert so may not be an ideal solution). It worked for me on Ubuntu Server 9.04. 
This guide will need to be adjusted if you have more than one user installed. 

DONT SKIP ANY STEPS ESPECIALLY THE SECOND !
THIS GUIDE IS WRITTEN FROM MEMORY SO COMMANDS/SYNTAXES MAY BE SLIGHTY OFF - DONT JUST COPY/PASTE - MAKE SURE THE COMMANDS WORKS AS INTENDED BEFORE PROCEDING TO THE NEXT STEP

1. Login normally
Your encrypted home directory should now be mounted

2. Backup all your files/directories in you home directory (including any hidden)
Something like the following should work (make sure the backup is intact/valid before proceeding) 
sudo mkdir /backup/
sudo cp -R /home/username /backup/

3. Stop the automounting/dismounting of encrypted home directory
Use the following command:
sudo grep -R "ecryptfs" /etc/

It should list three files (may list files like mtab eg - ignore thoose)
/etc/pam.d/common-auth
/etc/pam.d/common-password
/etc/pam.d/common-session

Open each of the above files in a texteditor(eg nano,vi) and comment out the lines that refers to pam_ecryptfs.so (put the symbol # in front of the lines)

4. Reboot your computer and log in again. 
This time when you login - your home directory should not be decrypted - and should only contain two files. Some readme and some other file. 

5. Backup/remove encrypted home directory: 
Move (dont delete) your encrypted home directory so if anything goes amiss you can restore it.
sudo mkdir /backup/encrypted_home
sudo mv /home/username /backup/encrypted_home

6. Create a new unecrypted home directory
Copy in your unecrypted home directory from your backup folder and set permissions
sudo cp -R /backup/username /home
sudo chown username /home/username
sudo chmod -R u=rwx /home/username

DONE! (At this point it's prob a good idea to restart your system)

---

### Post by magatz on 2009-11-20
Take a look here:
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1134121](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1134121)
by

---

### Post by gregmcd on 2010-05-20
It is possible to simply disable your specific home directory from being unmounted after logging out by removing the file ~/.ecryptfs/auto-umount.  The advantage is that if you are on a system used by multiple users, this offers more than the "all or nothing" approach.

Alas, I do not know the full behaviour.  For example, I do not know what happens across reboots...do you need to log in once to unencrypt?  I would suspect so, but have not tested it.

---

### Post by cozman69 on 2010-07-27
> **somafm said:**
> 
I thought this was a decent idea at first; however, whenever I am not logged onto the computer, my apache2 server returns "Forbidden 403" error messages on all pages. When I log back in, everything is perfectly fine again.. so I think it has to do with this whole "encrypted home directory" feature because my web server files are stored in: /home/user/public_html/


Hi, I found a happy medium that lets me keep my encrypted home directory, while my public_html isn't encrypted.

1) Create a new directory /home/public_html.  That doesn't have to be the name, but it makes it easy to know what it is.

```
sudo mkdir /home/public_html
```

2) Create a subdirectory for yourself inside /home/public_html.  Note, the $USERNAME environment variable should be defined.  If it isn't, just substitute your username for the variable.  Lastly, change the owner/group of the directory to your username (I'm assuming your group name is the same as your user name). 
```
cd /home/public_html
sudo mkdir $USERNAME
sudo chown $USERNAME:$USERNAME $USERNAME
```

3) Now put a symlink from your home directory to this directory.  This is purely for your convenience.  If there is a public_html directory in your home folder, make sure you migrate these files to /home/public_html/$USERNAME and then remove the directory so you can make the symlink.

```
cd ~
ln -s ../public_html/$USERNAME/ ./public_html
```

4) Now, here is the important part.  The apache2 configuration must be updated.  I will assume that you have not setup UserDir before (as it is not setup when you first install Apache), but if you have set it up already, you'll see what needs to be changed (one line really).

Setup the userdir configuration (I use vi, but using gedit here so everyone can edit the file):

```
gksudo gedit /etc/apache2/conf.d/userdir
```

Cut and paste the following code into this file:

```
UserDir /home/public_html
UserDir disabled root

<Directory /home/*/public_html>
AllowOverride FileInfo AuthConfig Limit
Options Indexes SymLinksIfOwnerMatch IncludesNoExec
</Directory>
```

Save and close.

5) Setup the appropriate symlinks that enables the loading of the userdir module into apache.

```
cd /etc/apache2/mods-enabled/
sudo ln -s ../mods-available/userdir.* .
```

6) Reload the apache configuration.

```
sudo /etc/init.d/apache2 reload
```

That's it.

---

### Post by welshmike on 2010-12-10
> **capped said:**
> 
...
I figured out how to decrypt your home directory:
...

It didn't work for me on 10.04.

I failed at the first hurdle:
```
mike@mike-i3-notebook:~$ sudo mkdir /backup/
mike@mike-i3-notebook:~$ sudo cp -R /home/mike /backup
cp: cannot stat `/home/mike/.gvfs': Permission denied
```

2nd attempt failed too:
I bypassed step 2 and copied my home folder using Gnome.
I followed the script precisely from step 3 and when I rebooted at step 4 no desktop contents appeared such as icons and panel, just the default desktop background and no input being accepted from keyboard or mouse.
 
I'd earlier taken the precaution of having a second admin user, mike2.
I restarted Ubuntu using Ctrl Alt Del and logged in to mike2.
I removed the #s from the start of the lines in the three files that referred to pam_ecryptfs. 
I logged out of mike2 and logged in to mike, my working user that has the encrypted home folder. 
This showed desktop contents and panel satisfactorily.

Phew !!!

But my mike home folder remains encrypted (after log out),

---

