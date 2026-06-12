---
title: "Drive mapping in Ubuntu"
date: 2005-10-12
forum: Desktop Environments
---

### Post by Shun on 2005-10-12
Hi All,

   I try to do a drive mapping like Windows in Ubuntu. But i cannot make it. Do anyone know how to do drive mapping in Ubuntu? In my PC is using Ubuntu and my server is using Redhat. So i want to try to do the mapping drive between these 2. For example, i want to map a folder from my server to my PC, how can i make it? Please advice.

Thank you!

---

### Post by HermanAB on 2005-10-12
In UNIX you have a single directory tree and drives are simply grafted onto the tree wherever some space is needed.  You have a couple of ways to solve your problem, the UNIX way and the Windows way.  The UNIX way is to use NFS - the network file system.  The Windows way is to use a Samba server.

Another way is to forego mounting distant drives altogether and simply use the fish (sftp) protocol and the Konqueror browser of Kubuntu to drag and drop files around.  If Konqueror is set up right, then you can browse a distant drive, double click a file and it will open in a local application, without having to bother with mounting.

If you need help with Samba, have a look here:
[http://www.aerospacesoftware.com/samba-debug-howto.html](http://www.aerospacesoftware.com/samba-debug-howto.html)

Cheers,

Herman

---

