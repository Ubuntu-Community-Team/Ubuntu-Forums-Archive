---
title: "Nautilus remote file permissions"
date: 2009-01-27
forum: General Help
---

### Post by Captain Giraffe on 2009-01-27
I have a folder at a remote ubuntu machine to connect to both by using regular console ssh and via nautilus File Browser ssh/sftp mode.
How come I'm allowed to change files in that folder over ssh but not via Nautilus ssh/sftp?

sftp command line shell works.

My user is not the owner, but belongs to a group with write permissions.

Thanks in advance
/Captain

---

### Post by Captain Giraffe on 2009-01-28
For great justice and soft yarns.

---

### Post by oraknabo on 2009-02-06
Right click on some files and look at the owner and group info.

I am having an issue in Ibex where nautilus is showing the owner and group as their numeric IDs on the server when connecting over sftp. The only way to work on files is to save a copy to my desktop and drag it to the window to overwrite the original. This changes the permissions which I don't want, so I have to periodically run a chown on the directory through a regular ssh connection.

The only thing close to a fix I've found is to have an identical user and group on my local machine with the same UID and GID. This shown the correct name in the info>permissions tab, but there's still a problem. Even if I make the connection through the user that owns the file, it still won't let me edit the files if I'm not logged into my machine as the same user.

The only thing I can do in the end is duplicate my local user to the server and chown all the files to my user, but I really don't want to do that.

---

### Post by Ishino on 2009-02-09
Is there a way to prevent the permission changes? Either in nautilus or on server side?


greetz

---

