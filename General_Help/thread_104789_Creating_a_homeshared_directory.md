---
title: "Creating a /home/shared directory"
date: 2005-12-16
forum: General Help
---

### Post by jdmpike on 2005-12-16
Hello all,

I was wondering if I could get a little help creating a directory that all members of my group 'users' could access.

Essentially what I want is a central repository that all users on my machine (only me and my finace, but it is the principle darn it!) can copy music and pictures to one place and all members of the group will have +rwx to all files in that directory, no matter who put them there. Like a shared folder in Winbl0ws.

So here is where I am at so far. I have created a /home/shared directory and chgrp'd it to 'users' and chmod -R 2775'd it. This will set the perms the way that I want them, but I want people to just be able to drop stuff in and it automatically sets these!

Can anyone help?

Thanks!

---

### Post by grj on 2005-12-16
menu

Applications->System Tools->Run as different user

In the Run box type nautilus
In the As user box enter root

In Nautilus move to the /home folder

Right mouse click and select Create Folder, name it as you wish

Right mouse click your new folder and select Properties


Select the Permissions tab and check the read, write, execute values as desired

---

### Post by jdmpike on 2005-12-17
setting the perms on the directory wasn't the problem. Setting the folder up such that it would modify the permissions whenever you drop new files or folders in the shared directory is what I am unsure how to do..

Any thoughts anyone?

---

### Post by jdmpike on 2005-12-17
I know I could use a cron job to just go and set the permissions on the directory every X minutes, but that isn't what I want to do - I only want to set the perms when members of the group users drop files into the shared directory.

Dooglus in the Ubuntu channel, recommended checking out Gamin ([http://www.gnome.org/~veillard/gamin/index.html](http://www.gnome.org/~veillard/gamin/index.html)) and I think that looks just like the thing I need. I want to monitor a directory and poll it for changes, when there are modifications to the directory, I want to kick off a script that chmods and chgrps accoringly.

Now, does anyone out there have any experience with gamin or gam_server?

I would really appreciate some direction with these - thanks!

---

### Post by curtis on 2005-12-17
I might be wrong...
But wouldn't "chmod 1777 /home/shared" work?
That is what /tmp uses to keep all files to 777 permissions.

---

### Post by BathroomNinja on 2005-12-17
[QUOTE=curtis]I might be wrong...
But wouldn't "chmod 1777 /home/shared" work?
That is what /tmp uses to keep all files to 777 permissions.[/QUOTE]


Let me know if that works, because I've been using a cron job to do the same thing and I would rather not have to use it.

---

### Post by titaniumlou on 2005-12-17
You should be able to set the file and directory creation mask in the smb.conf file:
```

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
;   create mask = 0700

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
;   directory mask = 0700

```

So you would set that in the section for the /home/shared share that you've defined in the smb.conf file

---

### Post by BathroomNinja on 2005-12-17
[QUOTE=titaniumlou]You should be able to set the file and directory creation mask in the smb.conf file:
```

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
;   create mask = 0700

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
;   directory mask = 0700

```

So you would set that in the section for the /home/shared share that you've defined in the smb.conf file[/QUOTE]


I think that would work with Samba, however, I don't think he is using Samba for this.  If I understand it correctly, he is doing everything local on one computer.

---

### Post by earobinson on 2005-12-20
looks like this feature may be in the dapper drake!

---

