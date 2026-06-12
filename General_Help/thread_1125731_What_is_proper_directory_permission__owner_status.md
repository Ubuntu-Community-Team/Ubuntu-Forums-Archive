---
title: "What is proper directory permission / owner status"
date: 2009-04-14
forum: General Help
---

### Post by sofasurfer on 2009-04-14
I haven't yet learned proper usage of permissions via 'chown' and 'chmod'. I only make changes when needed via right-click>permissions.

In the process of weening my wife off of winblose I added an Ubuntu OS to her pc. But now I see that EVERY one of her directories has a padlock icon attached to it and the permissions of every directory are set to 'root'.

I have no problem changing her user directory to 'user'. 

Here are my questions...
1) On my pc there are NO directories which have the padlock icon. On her pc every directory has the padlock icon. Yet on both pcs the permissions are the same. For instance, my /etc is set to root with no padlock. Her /etc is set to root but HAS the padlock. What is the padlock for?

2) Is the proper permission scheme to have every directory and file in 'user' directory set to 'user' and ALL other directories set to 'root'?

---

### Post by pytheas22 on 2009-04-14
> On my pc there are NO directories which have the padlock icon. On her pc every directory has the padlock icon. Yet on both pcs the permissions are the same. For instance, my /etc is set to root with no padlock. Her /etc is set to root but HAS the padlock. What is the padlock for?

The padlock just lets you know that the folder is owned by someone else, meaning that you can't write to it.  I'm not sure why your wife's computer has a padlock icon on every folder (is it every single folder, or only those owned by root?).  Did you make any changes to the system theme or the settings in Nautilus (the file browser)?  Or was the padlock displayed on every folder the first time you booted into Ubuntu?

> Is the proper permission scheme to have every directory and file in 'user' directory set to 'user' and ALL other directories set to 'root'?

Yes.  Everything under /home/username should be owned by username.

---

### Post by sofasurfer on 2009-04-14
But why is it that her root-owned files have the padlock but MY root-owned files do not have the padlock?

---

### Post by pytheas22 on 2009-04-14
I don't know why, but I would guess that it has to do with some preference that she set in Nautilus.  Try deleting her ~/.nautilus directory to force it to default back to the original settings.

Also, I notice that on my system, the padlock only seems to appear on root-owned folders that are inside my /home directory.  There is no padlock on /etc, for example.

---

### Post by ajgreeny on 2009-04-14
Is it perhaps a different theme on the two machines with icon differences between the themes?

---

### Post by sofasurfer on 2009-04-14
While I'm asking questions about permissions, heres another...

While reading about permissions at [http://linux.about.com/gi/dynamic/offsite.htm?zi=1/XJ&sdn=linux&cdn=compute&tm=80&f=00&su=p284.9.336.ip_p504.1.336.ip_&tt=2&bt=1&bts=1&zu=https%3A//wiki.ubuntu.com/FilePermissions](http://linux.about.com/gi/dynamic/offsite.htm?zi=1/XJ&sdn=linux&cdn=compute&tm=80&f=00&su=p284.9.336.ip_p504.1.336.ip_&tt=2&bt=1&bts=1&zu=https%3A//wiki.ubuntu.com/FilePermissions) I followed an example about the file /etc/shadow, which stores user passwords. When I listed it saw that group ownership is granted to 'shadow'. 

~$ ls -l /etc/shadow
-rw-r----- 1 root shadow 971 2009-04-14 17:37 /etc/shadow

When I went to administration>user-and-groups I see that there is no 'shadow' group. Explain?

---

### Post by pytheas22 on 2009-04-14
> When I went to administration>user-and-groups I see that there is no 'shadow' group. Explain?

Never noticed that before.  My only guess is that this has to do with the fact that Ubuntu, unlike most other distributions, has no 'root' group (on my Red Hat server, /etc/shadow belongs to the group 'root').  This may be how Ubuntu works around it.  As for why 'shadow' isn't listed when you type 'groups', I'm not sure.

---

### Post by lloyd_b on 2009-04-14
> **sofasurfer said:**
> While I'm asking questions about permissions, heres another...

While reading about permissions at [http://linux.about.com/gi/dynamic/offsite.htm?zi=1/XJ&sdn=linux&cdn=compute&tm=80&f=00&su=p284.9.336.ip_p504.1.336.ip_&tt=2&bt=1&bts=1&zu=https%3A//wiki.ubuntu.com/FilePermissions](http://linux.about.com/gi/dynamic/offsite.htm?zi=1/XJ&sdn=linux&cdn=compute&tm=80&f=00&su=p284.9.336.ip_p504.1.336.ip_&tt=2&bt=1&bts=1&zu=https%3A//wiki.ubuntu.com/FilePermissions) I followed an example about the file /etc/shadow, which stores user passwords. When I listed it saw that group ownership is granted to 'shadow'. 

~$ ls -l /etc/shadow
-rw-r----- 1 root shadow 971 2009-04-14 17:37 /etc/shadow

When I went to administration>user-and-groups I see that there is no 'shadow' group. Explain?
Just a guess, but I suspect that the program is simply suppressing the "shadow" group, since no user should ever be a member of that group (for security reasons).

It's probably also suppressing the "bin" and "sys" groups, for the same reason.

Lloyd B.

---

### Post by Stupendoussteve on 2009-04-14
Shadow appears in the /etc/group file. Not every group appears in the GUI.

---

### Post by CatKiller on 2009-04-15
The padlock icon will only appear if you're using an icon theme that supports it; those additional graphical bits are called Emblems, I believe. If your theme supports them, you'll get the padlock emblem for any file that you don't have write permissions for. Even if you own them. So if you copy a file from a cd, for example, those files will have the padlock emblem since files on a cd are necessarily read-only.

It is perfectly normal for a user to own the files in their Home folder and for root to own everything else. This is by design. You should not attempt to change this.

---

### Post by sofasurfer on 2009-04-15
Thank you.

---

