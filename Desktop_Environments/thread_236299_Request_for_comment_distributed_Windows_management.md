---
title: "Request for comment: distributed Windows management"
date: 2006-08-14
forum: Desktop Environments
---

### Post by geuis on 2006-08-14
Ok, I manage multiple Windows XP machines in multiple stores for our realty company, but my main job is a web designer so I while I'm pretty good at keeping everything clean, I really want to make that part of my job brainless so I can concentrate on the fun stuff(the design.)

I know there are other options out there for the setup I am proposing, but I just wanted feedback on this idea, whether its good or bad.

1) Each computer in each store boots with Ubuntu.
2) At startup, a startup script loads VMware or equivalent software, which then boots a virtual copy of Windows XP from an image file. 
3) Windows is then made full-screen, etc, so the employees just work in XP as they normally do to run their MLS, IE-specific websites, and AOL, and otherwise futz up my systems with spyware because they can't use Firefox because of the MLS.
4) Here at HQ, I keep a clean master copy of Windows XP with all the latest updates, etc. When I need to update the remote machines, I simply upload my latest image file to my server.
5) On startup, the startup script in each Ubuntu machine does a remote check in my server for an updated copy of the WinXP image file. If it finds a copy, it downloads the update and replaces the existing image file with the new one. Walla, Windows is instantly updated, no spyware, no viruses, nadda.
6) Each store has a copy of a custom Ubuntu install disk which automatically sets up the entire system. If a computer has to be wiped completely, just reload the disk and wait for it to download the latest Windows image again from the server.

Bandwidth isn't a problem. Our hosting is on a distributed cluster, so no worry about strain, etc.

Caveat: users can't store anything locally without the expectation that it will be erased at least once a week. 
Pro: we have a remote backup system anyway, so they just save the stuff they need to keep to that. Make it automated, even.
Caveat: possible problem with the Windows XP product key. Needs to be unique for each install. Hmm, not sure about this.

Is this a feasible setup? Is there something vitally important here that I'm missing that would sink this entire idea?

I appreciate any comments before I move forward.

---

### Post by lamego on 2006-08-14
Hello,
I already had the idea to do something using a similar approach (distributed vmware player), never had the chance to implement it.

Just some comments on your caveats:
> Caveat: users can't store anything locally without the expectation that it will be erased at least once a week. 
You could overcome this by using samba to provide local storage to the vmware machine.

> Caveat: possible problem with the Windows XP product key. Needs to be unique for each install. Hmm, not sure about this.
It depends on the type of key you are using, anyway a lot of companies do use image based installations which have the same OEM key, you shouldn't get into troubles as long you do own the licenses.

P.S.: My idea was to keep the vmware images on the server, and running them directly from the server (once for each system), but I am not sure this would be usable at all (the vmware disk I/O over the network).

---

### Post by geuis on 2006-08-14
In my specific case, this is going to be done remotely, i.e. over yeh internet.

We have 9 stores, plus our corporate office. Each store has at least 3 different computers. My thoughts were to upload update VMware images to our ftp server and have each Ubuntu station check for updates at startup, or say once a week on Sundays when the updates can be performed with no one there.

---

### Post by lamego on 2006-08-14
If possible you should copy the vmware image files using rsync or a similar tool, rsync is able to identify parts of the file that have changed and will only transfer those. Evenf if you don't have traffic concens, this would make the copy much faster.

---

### Post by geuis on 2006-08-14
Good recommendation.

---

