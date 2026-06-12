---
title: "Unwanted &quot;Internet&quot; Icon on Desktop"
date: 2007-12-12
forum: Desktop Environments
---

### Post by CrystalStarI on 2007-12-12
I have a "Internet" icon locked on the Desktop.  Cannot move it or trash it.  The properties box shows under the permission tab: "ftp:internet".   The basic tab shows MIME type: "application/octet stream" and all the other lines show unknown.  Don't know how/when it arrived, haven't been on the computer for a while.  Anyone know what this is?  Should I worry?

---

### Post by Keith Hedger on 2007-12-12
Ive never seen this sounds like a misbehaving app but to get rid of it in the terminal type:
sudo rm /PATH/TO/THE/FILE

---

### Post by CrystalStarI on 2007-12-14
Hi Keith, thanks for the reply post.  The sudo rm didn't work, so I thought I'd try "unmount volume" which showed above "properties" on the right-click list.  That worked.  :KS

---

### Post by Keith Hedger on 2007-12-14
Sorry from your original post I just assumed it was a regular file (hence sudo rm) but it was obviously a mounted disk:(

---

