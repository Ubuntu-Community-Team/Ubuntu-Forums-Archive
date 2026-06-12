---
title: "gedit sftp read only"
date: 2005-12-07
forum: Desktop Environments
---

### Post by vav on 2005-12-07
I'm having problems editing files on a remote server. I open my folder on the server using sftp://user@server and then double click on a text file but it opens as read only in gedit... I have to copy it to my machine, edit it and then write back.

How do I get around this?

--Vav

---

### Post by 23meg on 2005-12-08
I don't use sftp myself but perhaps it has to do with your level of access to sftp service. You need to have write permission on any file you need to modify; otherwise it will be opened as read only, and in the case of sftp, since the files are on a remote computer, your access to them may be limited by default.

I know I'm not providing a solution but maybe this will give you an idea on where to look for solving it.

---

### Post by dhayes on 2005-12-08
I am having the exact same problem (only after upgrading from 4.10 to 5.10). It is interesting that I can copy and paste the the sftp site as a normal local folder without doing anything special. For example I can overwrite a file or delete a file, but I can't open in gedit and save? Wierd. 

Any ideas on how to attack this annoyance?

Cheers,
Dan

---

### Post by vav on 2005-12-08
I saw a post through google search which mentioned this as a known bug in gedit, but it was supposed to be fixed by 2.8 and we're on 2.12.

I tried modifying the permissions on the remote server to 666 (which worked). And I can overwrite the file thru nautilus, but not thru gedit...

--vav

---

### Post by vav on 2005-12-08
Interestingly, I opened the text file in openoffice and it asked me for the password to the server, then let me modify it. (didnt work with gvim: do I need some specific options?)

gedit automatically looks at the keyring, I have to give the keyring password and it uses that to get the remote server password...

--Vav

---

### Post by Ocxic on 2005-12-08
this is just a guess, but try doing a sudo from a termnial
ie:
sudo gedit pathTOfile/your_file_here

---

