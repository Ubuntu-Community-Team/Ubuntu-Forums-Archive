---
title: "Folder Sharing Question..."
date: 2009-05-06
forum: General Help
---

### Post by Steven45 on 2009-05-06
Hi Fellow Ubuntu-ers:)

My friend and myself both run Ubuntu v9.04. He runs his on a 64-bit machine and I run mine on a 32-bit machine. Both machines are very modern and run just fine with Ubuntu on them.

So there's what we have so far. What we would like to do is be able share folders within the same house and between his computer and mine (no WAN or internet protocols, router addressing, typing tons of commands into a terminal, etc). Just simple folder sharing via a GUI.

We initially tried nautilus-share and that seemed to work (off and on) for awhile - although the permissions we set or the checkboxes we checked never seemed to get saved and eventually it quit working altogether. We fiddled around endlessly with the Samba config and Nautilus-Share config files to no avail. We always made sure to do everything by the book, follow the instructions, etc. We also made it a point to turn the server on before we turned the other machine on so the network could be "detected" and the folder(s) served. No joy whatsoever.

Then we tried share-admin and samba-config and even a program called "Giver". Still no luck. Prior to this we had tried a program similar to PC Anywhere (built into Ubuntu) and of course, we checked to make sure that the Samba service was running and all the packages and dependencies were properly installed.

Anyway, I have spent a lot of time (I mean a LOT of time) trying to get my friend interested in Ubuntu and so far everything has been just peachy but this issue with folder sharing is super important to him and without that ability, it's a real deal-breaker so if anyone can help us out here, we would really appreciate it a LOT as we are just pulling our hair out at this point.

Thanks in advance for any help!!

- Regards, Steve

---

### Post by Ocxic on 2009-05-06
use NFS and webmin to manage the shares. 
NFS can be installed from the repos, webin will have to be downloaded from there website.

---

### Post by Steven45 on 2009-05-06
> **Ocxic said:**
> use NFS and webmin to manage the shares. 
NFS can be installed from the repos, webin will have to be downloaded from there website.

Thanks for the quick reply!. I've looked at WebMin and even kicked the tires a little bit from time to time and it's a bit more techy than I want and much to techy for my friend who is pretty new to Ubuntu. Thanks for the suggestion just the same though.

I've heard of NFS. What does that stand for though and is there a user-friendly GUI for it?.

Thanks again.

- Regards, Steve

---

### Post by Steven45 on 2009-05-06
Anyone please?...

---

### Post by comorbid on 2009-05-06
Being relatively new to Linux myself, I'm only guessing it stands for Network File Server. I searched the Package Manager for NFS, and it looks like jftp is apparently "the" GUI.

---

