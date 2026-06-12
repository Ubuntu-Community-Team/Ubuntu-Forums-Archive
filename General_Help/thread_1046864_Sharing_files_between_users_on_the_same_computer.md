---
title: "Sharing files between users on the same computer"
date: 2009-01-21
forum: General Help
---

### Post by 3pinner on 2009-01-21
I am running Intrepid (8.10)

I need to share a spreadsheet between 2  users on the same computer.
Both  users need to have read and write permissions for the file.
 I do not want the other user to have any access to my home folder.
Can anyone tell me the simplest way to do this?

Here is what I have done, and it works, but it seems a sloppy way to do it.

I created a user called share.

I created the spreadsheet under my user account, then opened Nautilus as root (sudo Nautilus)
changed the owner to share
Then changed the permissions on the file to:
	Owner: Share
	Access: Read and Write

	Group :cdrom (because everybody can belong to that group)
	Access: Read and Write

	Others: Read and Write.

The folder the file is stored in has permissions:
	Owner:  Share
	folder access: Create and Delete files
	File access: ----

	Group	Share
	folder access:  Create and Delete files
	File Access: ---

	Others
	Folder Access:	Create and Delete files
	File Access: ---

I then created links from both accounts to the file in share.

I can access the file from both accounts, modify it and save it (so far!) But there must be a better way.

Thanks for the help!

---

### Post by epictete on 2009-01-21
I'm not sure **3pinner** but wouldn'it be possible to:

Create a new group "share".

Add both users to the group "share".

Attribute the spreadsheet and the repertory it's stored in to the group "share".

Change the permissions of the spreadsheet to -rwxrwx---

Change the permissions of the directory to drwxrwx---

Every member of the group "share" can enter the directory "dir-share" (x), read (r) and create, erase or modify (w) files in it.

Did I make a mistake?

---

### Post by 3pinner on 2009-01-22
> **epictete said:**
> I'm not sure **3pinner** but wouldn'it possible to:

Create a new group "share".

Add both users to the group "share".

Attribute the spreadsheet and the repertory it's stored in to the group "share".

Change the permissions of the spreadsheet to -rwxrwx---

Change the permissions of the directory to drwxrwx---

Every member of the group "share" can enter the directory "dir-share" (x), read (r) and create, erase or modify (w) files in it.

Did I make a mistake?

Sounds reasonable. I'll try it, and post back.

either this question is so simple, nobody wants to respond,
or so complex, nobody wants to respond!;)
I just need a really good source to learn the permissions for Linux.

---

