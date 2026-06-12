---
title: "ssh server is read-only"
date: 2005-11-06
forum: Desktop Environments
---

### Post by acorrigan on 2005-11-06
I'm trying to connect to my school's ssh/scp server to edit some files on my account there (my web page, homework, etc.)

I click Places->Connect To Server
Service Type: SSH
I type in the server url
the folder: /home/acorriga
and my user name: acorriga

Say I go to file index.html and edit it with Text Editor.  The file is read-only no matter what and I cannot save any changes.

How do I make these files writable?

I think that the problem may be related to the following:
The permissions look ok, the owner (which is set to my local user-name) can read write and execute all of the files in the directory.   I then clicked properties on the server icon which appeared on my desktop and checked the permissions.  The file owner is my local user name and the group is also my local user name, 'users' is not an option.   So that tells me that I'm the owner.  However, there is a message at the bottom: "You are not the owner, so you can't change these permissions"

I clicked "Help" but there was no useful information there.

---

### Post by Cubiq on 2005-11-07
I was going to post the same question...
I also have the same problem with ssh and samba shares. I can copy, move, overwrite, rename any file but I cannot edit it "on-the-fly" with (say) a text editor. Is this a bug or a feature :) ?

Is there any way to have a folder on a network computer behave as it was a local folder? I understand it is a very very very lame question... :(

---

### Post by psusi on 2005-11-07
[QUOTE=Cubiq]I was going to post the same question...
I also have the same problem with ssh and samba shares. I can copy, move, overwrite, rename any file but I cannot edit it "on-the-fly" with (say) a text editor. Is this a bug or a feature :) ?

Is there any way to have a folder on a network computer behave as it was a local folder? I understand it is a very very very lame question... :([/QUOTE]


Sounds like a bug to me, probably in gnome-vfs.  

In the case of samba shares, you might try mounting them instead of browsing them directly in nautilus.  Once mounted, they should behave exactly like local files.

---

### Post by Cubiq on 2005-11-07
[QUOTE=psusi]Sounds like a bug to me, probably in gnome-vfs.  

In the case of samba shares, you might try mounting them instead of browsing them directly in nautilus.  Once mounted, they should behave exactly like local files.[/QUOTE]

thanks for your reply. I mounted my samba share, I have full access (read/write) to all files but I cannot edit them on the fly... all files appear read-only when opened in text editor. Same thing with ssh/sftp connections... any clue?


UPDATE: okay, problem solved with samba thanks to [this]("http://www.ubuntuforums.org/showthread.php?t=26438") thread. Now I think that the same can be done with SSH using SSHFS...

---

### Post by acorrigan on 2005-11-08
I'm not sure about this sshfs, is it something that the server needs or the client needs?

---

### Post by Cubiq on 2005-11-09
[QUOTE=acorrigan]I'm not sure about this sshfs, is it something that the server needs or the client needs?[/QUOTE]

If sshd is running on your server (=you can log into your server with ssh client) you just need to install sshfs on your client and mount the remote directory as usual (I didn't try, thou). Search ubuntuforum for "sshfs", you should find some howtos.

---

