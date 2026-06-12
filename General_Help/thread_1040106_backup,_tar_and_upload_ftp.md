---
title: "backup, tar and upload ftp"
date: 2009-01-15
forum: General Help
---

### Post by mbarne on 2009-01-15
Hello,

I tried to backup my account using tar and upload it through ftp using a pipe, as I do not have enough space to make the tar.gz first. I need to upload it "real time"... so I used this command

I log to my ftp server, using simple "ftp" linux command and then

put |"tar cvzf - ./" backup.tar.gz

this should work correctly, but I have a problem... the data I have to transfer is over 1 GB and this "put" command takes a lot of time (client and server are not on the same LAN, I use internet to transfer data) and so, for some reason, the connection drops.

Anyone knows a way to split a tar in multiple pieces and submit them via ftp? I know that tar permits to create multiple archives, but I would have to keep them locally (and I don't have enough space...), so this solution is wrong.
I thought of creating a script that:
 - create a piece of tar locally (let's say 100MB)
 - send it through ftp (maybe using lftp that allows batch process)
 - once send is successful, deletes the "temporary" tar-piece created
 - creates another 100MB tar skipping what has already been submitted and the process start again from beginning till end of tars

but...I don't know if there's a way to create a tar-piece "skipping" a number of bytes (at least I don't know that way and I found no info about it...)...

anyone knows how to accomplish that?
Or maybe a better solution...

Bye

---

