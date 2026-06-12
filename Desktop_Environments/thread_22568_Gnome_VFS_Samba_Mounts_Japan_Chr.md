---
title: "Gnome VFS Samba Mounts Japan Chr"
date: 2005-03-28
forum: Desktop Environments
---

### Post by dwanders on 2005-03-28
Maybe someone out there can help me out. I have a situation where the following is occuring:

By mounting a Windows Share with Samba:
e.g. sudo mount -t smbfs ...
The windows share will mount fine, and I can access all folders except those that have Japan characters, which shows up as ?????? [and of course, I am unable to cd ??????, I get no such file or directory. 

However, when I use the Gnome way of accessing these shares:
e.g. Places -> Network Servers -> Windows Server Name (I am prompted for Username, Domain, Password) -> Shared Folder
The Japan characters show up great - I can even browse the subdirectories and everything looks great!

But I need to access these shares in the Gnome virtual file system from a command line in order to back them up with some scripting. Would anyone have any suggestions?

---

### Post by el3ktro on 2006-02-02
I figured that using cifs instead of smbfs made all my character issues (with German umlauts etc.) go away magically. Don't know if Ubuntu supports cifs though, but you can try it (mount -t cifs ...)

Tom

---

