---
title: "Opera download manager"
date: 2009-04-02
forum: General Help
---

### Post by WitchCraft on 2009-04-02
Question:

I've wanted to download a 3 gb iso image from a server.

The exact same image is available form several ftp servers.


Now I've started my download, it downloaded 2 GB, but now the server is down.
The other servers are still up.

How can I change the source of the download, to resume the download and continue from another server?

---

### Post by WitchCraft on 2009-04-02
OK, I managed to find the unfinished iso file, size 2.1 GB.

Now, I've created a backup copy. 
Try to resume the download with wget.

How can I get wget to resume the iso download from a particular location?

---

### Post by WitchCraft on 2009-04-02
Never mind. Found it out myself.

Open a terminal.
**Change to the directory where the partial download is located in.**

type: wget -c URL

---

