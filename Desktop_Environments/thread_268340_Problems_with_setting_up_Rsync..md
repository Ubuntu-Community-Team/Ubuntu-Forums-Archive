---
title: "Problems with setting up Rsync."
date: 2006-09-30
forum: Desktop Environments
---

### Post by Orbit45244 on 2006-09-30
I am trying to set up Rsync on my regular Ubuntu Dapper Desktop so my site's users can easily download and update files from my site.  The only problem is that I can't seem to get it working.  I have tried multiple guides, all to no avail.  I tried Rsync in Windows also, because my website is on a Windows server, but it was impossible.  So now I'm trying to get it working on Ubuntu, but I can't.  I need some help, please.

---

### Post by Orbit45244 on 2006-09-30
*Bump* 
Please help, I'm still having this issue!

---

### Post by pwrstick on 2006-10-01
So you want a multitude of users to be able to connect to your ubuntu machine and download files from it?

What have you done so far?  Have you set up a rsyncd.conf file in /etc ?

Have you run 'sudo rsync --daemon' to get the ubuntu system to start accepting connections?

Here's a reference: [http://everythinglinux.org/rsync/]("http://everythinglinux.org/rsync/")

---

