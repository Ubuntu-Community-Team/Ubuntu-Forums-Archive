---
title: "Can I use Firefox as a file browser?"
date: 2009-04-20
forum: General Help
---

### Post by Free Thinker on 2009-04-20
I used to use internet explorer to browse my files and other computers' shared documents. Is there a similar way to do this in firefox with your filesystem?

For example, in IE I would type things like:

C:\Program Files

to browse Program Files

and 

//xxx.xxx.xxx.xxx/c$

To browse xxx.xxx.xxx.xxx's C drive.

Any advice is appreciated.

---

### Post by leandromartinez98 on 2009-04-20
The local files can be browsed, using, for example:

/home/username

will show your local home directory.

I don't know the details on browsing a remote directory, because that may
depend on the type of connection that the server you are trying to connect
allows. For example, if it is an ftp connection, you can use

[ftp://yourserver](ftp://yourserver)

something like that. 

On the other side, I think the best way to browse the file of other machines
in Ubuntu is to use the Places -> Connect to Server option, in such a way
that you will browse your server as it was another local directory, and be
able to edit, move, copy, etc. the files there.

---

### Post by lovinglinux on 2009-04-20
You could use [Firefly](https://addons.mozilla.org/en-US/firefox/addon/3076) extension for Firefox, which is a file manager extension.

---

### Post by aeiah on 2009-04-20
id just use nautilus if i were you.

ssh://user@ipaddress:/path/to/files

save them as bookmarks in nautilus and then just treat the files like you would local ones.

you should be able to do it for samba shares the same way too, or similar anyway

---

### Post by Free Thinker on 2009-04-20
Thanks! It's all working fine now.

---

