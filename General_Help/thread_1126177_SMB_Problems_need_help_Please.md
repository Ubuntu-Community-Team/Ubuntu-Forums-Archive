---
title: "SMB Problems need help Please"
date: 2009-04-15
forum: General Help
---

### Post by XRTHIS on 2009-04-15
hey guys this is my setup.

Windows Vista Ultimate
3 Hard Drives with Apps on them

1 of my HDD i want my Virtual Machine Ubuntu - Proftpd to host.

i have achieved logins for users fine.

Files and mounting are visable.

When one of my users (ANY) go to download through FTPRush ANYFILE!

i get this msg.

[PHP][1] RETR Crank.2006.avi
[1] 150 Opening BINARY mode data connection for Crank.2006.avi (725084160 bytes)
[1] 426 Transfer aborted. Operation not permitted
[i] Transfer Failed: Crank.2006.avi
[i] Failed 1 file(s) and Skipped 0 file(s)
[1] TYPE A
[1] 200 Type set to A
[1] PASV
[1] 227 Entering Passive Mode (192,168,0,5,224,212).
[1] Opening data connection IP: 192.168.0.5 PORT: 57556
[1] LIST
[1] 150 Opening ASCII mode data connection for file list
[1] 226 Transfer complete
[1] List Complete: 26,864 bytes in 0.22 seconds (122.67KB/s)[/PHP]

Now i have done a search and i think this maybe my problem.

in my /Downloads/Movies Folder Permissions for Folders is *rwxrwxrwx*

BUT 

for all files *rwxrwSrwx*


all help is much appreciated guys and i am sorry for any inconvenience i am new to this but i am learning quickly.

---

