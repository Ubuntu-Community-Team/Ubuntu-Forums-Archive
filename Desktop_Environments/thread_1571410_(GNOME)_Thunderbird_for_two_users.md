---
title: "(GNOME) Thunderbird for two users"
date: 2010-09-09
forum: Desktop Environments
---

### Post by Sciezyna on 2010-09-09
I am very new to Ubuntu (5 days). I run version 10.04 GNOME.

My problem is (after substantial searching) that I need to have both users ('juliusz' and 'sarah') running Thunderbird but with the same profile (settings, email, accounts etc. preferably of 'juliusz'). The only results on the internet are share Thunderbird between Windows and Ubuntu.

It probably is very easy to setup for the more advanced users for me it seems impossible.

So:

I have two users juliusz and sarah.
I need either of them to have the same profile, always in synch whenever they logon to own account.

When I tried to edit sarah's /home/sarah/.mozilla-thunderbird/profile.ini by inserting:

Path=/home/juliusz/.mozilla-thunderbird/xxxxxxx.default

after i run Thunderbird for 'sarah' I get message: "Thunderbird is already running, but is not responding. To open a new window, you must first close the existing Thunderbird process, or restart your system."

I checked with "ps aux" there is no Thunderbird running in sarah's session. There is no Thunderbird running in juliusz's session when I reloged to juliusz.

Please help.

Thank you.

---

### Post by oldfred on 2010-09-09
Not quite sure what it is you are doing. It is that you have two totally different users in Ubuntu but only one email account for both of you?

You are probably into permission and ownership issues as the thunderbird profile in your home only has your rights.

I share my thunderbird but it is in a separate NTFS partition do I can boot windows or my other Ubuntu installs and have the same profile.

I do not know a lot about setting this up but I think you may want a separate folder/partition for shared data. I saved this post which a user wants to share a music folder with two users.

Two users to share music folder - group & permissions -BoneKracker:
[http://ubuntuforums.org/showthread.php?t=1484221](http://ubuntuforums.org/showthread.php?t=1484221)
[http://ubuntuforums.org/showthread.php?t=1488065](http://ubuntuforums.org/showthread.php?t=1488065)
See lucky's post on network based shares & setting permissions commands
[http://ubuntuforums.org/showthread.php?t=1498422](http://ubuntuforums.org/showthread.php?t=1498422)

The 2 at the beginning makes the directory SGID (Set Group ID). That means any files in the directory automatically will inherit the group of the folder, as opposed to the group of the user putting the file there.

mv ~/music /home
chown root:music /home/music
chmod 2774 /home/music  or 3774

would not recommend using the /media folder.

Group File, Directory and Device permissions: chmod
[http://www.yolinux.com/TUTORIALS/LinuxTutorialManagingGroups.html](http://www.yolinux.com/TUTORIALS/LinuxTutorialManagingGroups.html)

---

### Post by areeda on 2010-09-09
I'm kind of confused on what you are trying to do also.

I do something similar in that I run thunderbird on several systems and several accounts.  The trick is with the mail servers not T-bird itself.

If your mail accounts support imap it's easy.  Who provides the mail?  (like gmail.com or yahoo.com...) For gmail, I leave the messages there and can read/write from any system or account.

Joe

---

### Post by Sciezyna on 2010-09-11
The solution works but I am afraid is not very elegant so if more knowledgeable users find simpler way I will edit my post.

I run Ubuntu 10.04 GNOME Thunderbird for two users on single PC

I have two accounts: juliusz and sarah. juliusz is my account, the one that I installed Ubuntu with, so there also is juliusz Group. It was be a bit confusing for novice like me to have account juliusz and a Group juliusz - with the same name but that how it is.

Account juliusz is for my workspace and sarah is for my wife - we use the pc for different things.

I needed to be able to have the same email profile in Thunderbird being used by both juliusz and sarah while they are logged on to their desktops.


To acheive sharing the profile I used the advice given in postby 'oldfred' above. Thank you.

There are couple of different suggestions but I've selected one that worked for me:

1. Find unused HDD space (I had unused 60GB on my old windows boot disk).

2. Create ext4 (or ext3 or ext2) partition of say 10GB by GParted or Disk Utility - Disk Utility is easier and safer.

3. Make the partition's label to be eg. mine is 'utemp' (no quotes).

4. Even though the advice was not to mount the new partition in /media I did so because I am not fluent in mounting - that is system partitions mounting - so I used Disk Utility to mount it and by default the mount point enden up as /media/utemp.

5. Make sure that there are the right ownership and permissions set to the new /media/utemp 

TERMINAL:
=======================================
sudo chown -R juliusz:juliusz /media/utemp

sudo chmod -R 774 /media/utemp
=======================================

EXPLAIN - chown = change ownership;
    - -R recurscively 
    - (user:group) give ownership to group juliusz:juliusz
    - /media/utemp directory wher new ownership is to be set.

    - chmod = apply permissions to a file/directory
    - -R = recursively
    - 774 = root rwx; user rwx; other users r
    - /media/utemp directory for new permissions

Create hidden directory in /media/utemp with thunderbird default name .thunderbird

=====================================
sudo mkdir /media/utemp/.thunderbird
=====================================
EXPLAIN:
The dot '.' in front of thunderbird makes the directopry hidden

Take ownership of the new directory

======================================
sudo chown -R juliusz:juliusz /media/utemp/.thunderbird
======================================


Now copy the profile content, (with the werid name) from the original install place of Thunderbird which is (installed by juliusz) in /home/juliusz/.mozilla-thunderbird/xxxxxxxx.default, into the new directory and take ownership of it and apply new permissions.

=========================================
sudo cp /home/juliusz/.mozilla-thunderbird/xxxxxxxx.default /media/utemp/.thunderbird

sudo chown -R juliusz:juliusz /media/utemp/.thunderbird

sudo chmod -R 774 /media/utemp/.thunderbird
==========================================

The -R OPTION will take care of all directories and files under /.thundirbird

Now the Thunderbird profiles.

Change entries in profiles.ini for each user in their home directories, they are:

/home/juliusz/.mozilla-thunderbird/profiles.ini
/home/sarah/.mozilla-thunderbird/profiles.ini

Original content is as below:
---------------------------------
[General]
StartWithLastProfile=1

[Profile0]
Name=default
IsRelative=1
Path=/xxxxxxxx.default
----------------------------------

Each file needs to be changed (login to each account, find the profiles.ini and make changes)


New contents
----------------------------------------------
[General]
StartWithLastProfile=1

[Profile0]
Name=default
IsRelative=0
Path=/media/utemp/.thunderbird/xxxxxxxx.default
-------------------------------------------------

The 'IsRelative' regards the path of the file xxxxxxxx.default, and =1 says that the file is relative to the place where profiles.ini is.

Change it to =0 to say that the path is a custom one, the whole current path, from the mount point to the profile's storage.

The settings above work but there is one trick with Thunderbird. It creates a lock file (in xxxxxxxx.default with the name 'lock') and if present it prevents the /xxxxxxxx.default to be opened/used by more than one user at a time.

So if juliusz has running Thunderbird and does not logout but just switches to sarah and opens Thunderbird it will not run it will, properly, display message:

"Thunderbird is already running, but not responding. To open a new window, you must first close the xeisting Thunderbird process. or restart your system"

So before switching users one must close Thunderbird first.

I will, now have to figure out a script and way to run it to shut-down Thunderbird at the user switching time.

---

### Post by oldfred on 2010-09-11
I am no expert & that is why I recommended bonecrakers advice in above posts.

But as I read it, you have given yourself permissions & ownership but not your wife. You need to create a group say email or thunderbird and make both you & your wife part of the group. Then you make the group have full ownership & permissions with the commands bonecraker & sysco311 gave in the links.

Ubuntu actually uses UIDs and GIDs. That you have the same UID & GID is standard as you are part of your own group. man commands groupadd, useradd, chgrp, usrmod. I do not know enough as I have not had to do this.

---

### Post by Sciezyna on 2010-09-11
Thanks for looking at this issue. I believe that we both have permission by:

=========================================
sudo cp /home/juliusz/.mozilla-thunderbird/xxxxxxxx.default /media/utemp/.thunderbird

sudo chown -R juliusz:juliusz /media/utemp/.thunderbird

sudo chmod -R 774 /media/utemp/.thunderbird
==========================================

juliusz is the owner, the wife is in juliusz group.

I still have problem thought with the thunderbird lock files but working on that (learning fast).

Thanks

---

### Post by Caf1683 on 2012-11-08
Sorry for the late answer, but I hope this can be useful to future users:

In fact, yo[FONT=monospace]u were on the right track on your first post: all you had to do was replace the line

[/FONT]IsRelative=1

with

IsRelative=0

in the profiles.ini file.

---

