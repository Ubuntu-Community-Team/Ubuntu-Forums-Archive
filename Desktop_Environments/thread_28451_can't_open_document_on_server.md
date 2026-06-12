---
title: "can't open document on server"
date: 2005-04-20
forum: Desktop Environments
---

### Post by vermeersch on 2005-04-20
how can I get to a word document on the server through openoffice? When I click on 'open a document' I don't see any icon for the network/or server. 
Of course I can surf the network with nautilus, but when I double click the document, there appears a message in openoffice that the document cannot be found. The only way I can open the document is copying it on my desktop or home directory, open it, change it and re-copy it to the server. Not very user friendly.

Tnx

---

### Post by dataw0lf on 2005-04-20
How exactly are you sharing between you and the server ?  NFS? Samba? What?

---

### Post by vermeersch on 2005-04-20
samba, I guess. When I type smb://cmt-wk2/ in firefox, I get access to network and server.

---

### Post by vermeersch on 2005-04-26
tried accessing files through mandriva and kubuntu (smb4k), and this worked without problems. 
Could the prob have sthing to do with nautilus?

---

### Post by jcooper on 2005-04-26
I'm not sure if OpenOffice.org supports Gnome VFS (which permits the seamless use of remote files systems).

Unfortunately you may have to work on a local copy, then use nautilus to copy your updated document to the server.

---

### Post by vermeersch on 2005-04-26
Worked with gnome in mandriva and it opened remote word files without problems. So gnome can't be the problem I guess.

---

### Post by vermeersch on 2005-04-27
???

---

### Post by vermeersch on 2005-04-28
???

---

### Post by nocturn on 2005-04-28
Are you running ubuntu Warty or Hoary?

---

### Post by vermeersch on 2005-04-28
Hoary Hedgehog

---

### Post by jonorr267 on 2005-04-28
dont know if this is any use for u but it worked for me.open firefox and type 'smb://servername/sharename'  press enter should give list of documents in that share click on doc to open and choose default this opens doc with openoffice for me.

---

