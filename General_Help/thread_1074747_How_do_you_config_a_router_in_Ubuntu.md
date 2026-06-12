---
title: "How do you config a router in Ubuntu?"
date: 2009-02-19
forum: General Help
---

### Post by jras20 on 2009-02-19
How do you see your IP is gateway to get to the router in Ubuntu?  I'm sure theres a easy way to do it, we do it in XP a lot.  But would like to learn how in Ubuntu.
Thanks.

---

### Post by lindsay7 on 2009-02-19
do a google search "ipconfig in linux".  look for linux 101 hit.  It gives you all the details.

---

### Post by makisupa123 on 2009-02-19
Based on the last post, I'd assume there is some page that compares the windows 'ipconfig' command with the linux 'ifconfig' command?  I may be misunderstanding the post -- but I think that is what the poster is saying.

I'd just go 'route -v' and find the gateway for the interface your concerned about there.

--Mak

---

### Post by Yashiro on 2009-02-19
route -v | grep default

---

### Post by damis648 on 2009-02-19
> **Yashiro said:**
> route -v | grep default

Sure, that is a good option, as well as good 'ol
```
ifconfig
```
If you want a GUI way, just right click the network icon by your clock and click "Connection Details".

---

