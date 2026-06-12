---
title: "Eliminating the need for a Server"
date: 2009-03-28
forum: General Help
---

### Post by Centrist on 2009-03-28
Hello All,

I'm an IT consultant for small businesses, and I'm trying to find the ideal environment for a network of about 10 desktops. One of my priorities is to remove the need for a server because of its expense and the 'single point of failure.'

So I'm looking for some kind of software that would allow these desktop computers to be part of a group/domain that would share user accounts and files. If this data was replicated to all computers, then if one computer failed, all other computers would still have complete copies of the data.

I've looked at distributed file systems and syncing programs, but haven't found anything yet that doesn't rely on a client/server approach. If I absolutely had to use a server, I would probably go with a VPS from Slicehost, but would OpenLDAP auth and file shares work well over the internet?

Also, I'm looking for a good management program for networks like this. eBox seems to be the best so far, Landscape was too pricey, and Webmin seemed too disorganized. Would be glad to know what else is out there.


Thanks all for your time!

---

### Post by Centrist on 2009-04-29
If anyone's interested, I eventually went with an OpenLDAP virtual server from mosso. I also set up NFS and FTP servers, and it all works very well over the internet. And it's really cheap.

I tested both eBox and Webmin and neither of them is worth the trouble for a small network. Much better to know the commands ssh into a client.

---

