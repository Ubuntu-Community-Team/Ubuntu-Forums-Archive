---
title: "Help! mhddfs and Samba"
date: 2009-01-21
forum: General Help
---

### Post by cdg52 on 2009-01-21
Help :-)

I am trying to use mhddfs to merge all my drives into one big folder and access this over my network so I can listen to my music, watch my movies and see my pictures from going to one network share on my Windows computers but each time I attempt to access it I get this message in my samba logs

[INDENT]
[2009/01/21 18:12:39,  0] smbd/service.c:make_connection_snum(1156)
  '/media/Media' does not exist or permission denied when connecting to [Media] Error was Permission denied
[/INDENT]

Now I look at the folder /media/Media/ and here is the ls -l of that

[INDENT]
drwxrwxrwx 1 root  root      0 2009-01-21 18:14 Media
[/INDENT]

Does Anyone have any idea why I keep getting rejected? I have managed to make it work once, but never again :-/

Please help!

---

### Post by cdg52 on 2009-01-21
got it you need to add "-o allow_other" to the end of the mhddfs command

---

### Post by ias2 on 2011-05-08
In case of "canonicalize_connect_path failed for service XXXX" samba error, do as suggested above and add the "x" flag permission to all directory objects in the samba shared tree.

---

