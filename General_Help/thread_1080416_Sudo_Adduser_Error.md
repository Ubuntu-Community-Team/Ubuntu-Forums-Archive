---
title: "Sudo Adduser Error"
date: 2009-02-25
forum: General Help
---

### Post by Ernie Drum on 2009-02-25
Hi everyone,

Have spent a couple of full days trying to sort this one out, via the help pages & forums. I use this machine for business, I really need to get back to work so I thought I'd give in and post the problem here ...

Until I re-build the 'spare' machine I need to let the rest of the family use this one. No problem ! 

I have set up one family member no problems (Temp measure is they're all using the same account until I can resolve the issuse). When I now try to set up a new user (either through software or the terminal) the system tries but fails ??

Here is a copy of the terminal readout I get when I use sudo adduser Username 

ian@ian-laptop:~$ sudo adduser kaity
Adding user `kaity' ...
Adding new group `kaity' (1002) ...
Adding new user `kaity' (1002) with group `kaity' ...
Creating home directory `/home/kaity' ...
Copying files from `/etc/skel' ...
Stopped: open /etc/skel/./ian/Music/Jessica/beks party mix/Dj Sweegy - Hardcore Vibes : No such file or directory
Removing directory `/home/kaity' ...
Removing user `kaity' ...
Removing group `kaity' ...
groupdel: group kaity does not exist
adduser: `groupdel kaity' returned error code 6. Exiting.
ian@ian-laptop:~$ 

I can see that the problem seems to be in relation to the line - 

Stopped: open /etc/skel/./ian/Music/Jessica/beks party mix/Dj Sweegy - Hardcore Vibes : No such file or directory

But, unfortunately it makes no sense to me. the mp3 track it refers to does exist in /home/ian/Music/Jessica/beks party mix  plus it's a music track so what does it have to do with a new user set-up ???

Haven't posted before so am not sure how much additional info you require ? Here is some system info ..

Release - Ubuntu 8.10 (intrepid)
Gnome - 2.24.1 (Ubuntu 2008-10-24)
Kernel - 2.6.27-11-generic (#1 SMP Thu Jan 29 19:28:32 UTC 2009)
GCC version - 4.3.2 (x86_64-linux-gnu)
CPU - AMD Turion(tm)X2 Dual Core Mobile RM-72

Thanks in anticipation, Ernie

---

### Post by Yellow Pasque on 2009-02-25
Can you post output of these commands: 
```
cat /etc/adduser.conf
ls -la /etc/skel
```

---

### Post by cariboo on 2009-02-25
> Dj Sweegy - Hardcore Vibes

Because of tthe spaces linux sees the above file as 5 seperate files. Delimit the spaces by using \ eg:

```
Dj\Sweegy\-\Hardcore\Vibes
```

and it should copy ok.

Personally I use underscores in place of spaces in mp3 tiltes.

Jim

---

### Post by Yellow Pasque on 2009-02-25
cariboo, that may very well be the literal cause of the problem, but I doubt the OP even wants this file copied and I personally would like to investigate how this path worked its way into /etc/skel and whether a bug report should be filed.

Also, the OP would have to rename several files if he wants to work around the issue this way.

---

### Post by Ernie Drum on 2009-02-25
Firstly, thank you for the quick responses ...

**Output ... cat /etc/adduser.conf**

ian@ian-laptop:~$ cat /etc/adduser.conf
# /etc/adduser.conf: `adduser' configuration.
# See adduser(8) and adduser.conf(5) for full documentation.

# The DSHELL variable specifies the default login shell on your
# system.
DSHELL=/bin/bash

# The DHOME variable specifies the directory containing users' home
# directories.
DHOME=/home

# If GROUPHOMES is "yes", then the home directories will be created as
# /home/groupname/user.
GROUPHOMES=no

# If LETTERHOMES is "yes", then the created home directories will have
# an extra directory - the first letter of the user name. For example:
# /home/u/user.
LETTERHOMES=no

# The SKEL variable specifies the directory containing "skeletal" user
# files; in other words, files such as a sample .profile that will be
# copied to the new user's home directory when it is created.
SKEL=/etc/skel

# FIRST_SYSTEM_[GU]ID to LAST_SYSTEM_[GU]ID inclusive is the range for UIDs
# for dynamically allocated administrative and system accounts/groups.
# Please note that system software, such as the users allocated by the base-passwd
# package, may assume that UIDs less than 100 are unallocated.
FIRST_SYSTEM_UID=100
LAST_SYSTEM_UID=999

FIRST_SYSTEM_GID=100
LAST_SYSTEM_GID=999

# FIRST_[GU]ID to LAST_[GU]ID inclusive is the range of UIDs of dynamically
# allocated user accounts/groups.
FIRST_UID=1000
LAST_UID=29999

FIRST_GID=1000
LAST_GID=29999

# The USERGROUPS variable can be either "yes" or "no".  If "yes" each
# created user will be given their own group to use as a default.  If
# "no", each created user will be placed in the group whose gid is
# USERS_GID (see below).
USERGROUPS=yes

# If USERGROUPS is "no", then USERS_GID should be the GID of the group
# `users' (or the equivalent group) on your system.
USERS_GID=100

# If DIR_MODE is set, directories will be created with the specified
# mode. Otherwise the default mode 0755 will be used.
DIR_MODE=0755

# If SETGID_HOME is "yes" home directories for users with their own
# group the setgid bit will be set. This was the default for
# versions << 3.13 of adduser. Because it has some bad side effects we
# no longer do this per default. If you want it nevertheless you can
# still set it here.
SETGID_HOME=no

# If QUOTAUSER is set, a default quota will be set from that user with
# `edquota -p QUOTAUSER newuser'
QUOTAUSER=""

# If SKEL_IGNORE_REGEX is set, adduser will ignore files matching this
# regular expression when creating a new home directory
SKEL_IGNORE_REGEX="dpkg-(old|new|dist|save)"

# Set this if you want the --add_extra_groups option to adduser to add
# new users to other groups.
# This is the list of groups that new non-system users will be added to
# Default:
#EXTRA_GROUPS="dialout cdrom floppy audio video plugdev users games"

# If ADD_EXTRA_GROUPS is set to something non-zero, the EXTRA_GROUPS
# option above will be default behavior for adding new, non-system users
#ADD_EXTRA_GROUPS=1


# check user and group names also against this regular expression.
#NAME_REGEX="^[a-z][-a-z0-9]*\$"

[B]
Output ... ls -la /etc/skel[/B]

total 32
drwxr-xr-x   3 root root  4096 2009-02-24 13:40 .
drwxr-xr-x 169 root root 12288 2009-02-25 18:42 ..
-rw-r--r--   1 root root   220 2008-05-12 19:49 .bash_logout
-rw-r--r--   1 root root  3115 2008-05-12 19:49 .bashrc
lrwxrwxrwx   1 root root    26 2009-02-07 16:03 Examples -> /usr/share/example-content
drwx------  63 root root  4096 2009-02-24 13:44 ian
-rw-r--r--   1 root root   675 2008-05-12 19:49 .profile


May well try the work around but agree that if there's a fixable error it's worth waiting a bit longer

Thank you both, Ernie

---

### Post by Yellow Pasque on 2009-02-25
> drwx------ 63 root root 4096 2009-02-24 13:44 ian
There's your problem.
Now the question is - how did it get there? The modification time is very recent, so I'm guessing it's the result of something you did recently when trying to organize data and create new users.

The workaround would be to remove the "ian" entry from /etc/skel, unless you really want the files contained in it copied to the home directory of any new user you create.

---

### Post by Ernie Drum on 2009-02-25
I spent a while trying to get the other users desktop to have the look etc. of mine. I gave up, thinking it wasn't such a good idea. Just new desktops for them to learn on is fine. Anyway, during the effort I guess I took a wrong turn. Thankfully a recoverable situation thanks to yourself. 

Excuse my ignorance but when I look in **/etc/skel** the only files I can see are - **.bash_logout**, **.bashrc** & **.profile** none of which seem to have the line drwx------ 63 root root 4096 2009-02-24 13:44 ian ... Where should I look exactly ?

---

### Post by Yellow Pasque on 2009-02-25
It's there, but you don't see it in nautilus because only root has read permissions.

```
cd /etc/skel
sudo rm -rf ian
```

---

### Post by Ernie Drum on 2009-02-26
That's excellent, thank you. Works beautifully now.

If you still have a bit of time ?

I understand the rm - remove, what does the -rf actually mean, I expect the 'ian' bit is a reference to the line itself ?

As this particular issue is now resolved is there a way for me to tag it so ?

---

### Post by Yellow Pasque on 2009-02-26
-r = recursive
Since ian was a directory, this was necessary to remove its entire contents.

-f = force
Ignore broken symlinks and execute the removal without prompting the user

> As this particular issue is now resolved is there a way for me to tag it so ?
The forum used to have a SOLVED tag, but this is disabled (temporarily?) because the staff suspected it caused or contributed to database issues.

---

