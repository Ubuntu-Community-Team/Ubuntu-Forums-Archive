---
title: "transfer packages from cd to ubuntu sources.list"
date: 2007-05-23
forum: Desktop Environments
---

### Post by systimax on 2007-05-23
Hello I have a ubuntu box in a remote location. Is it possible to transfer the contents of the cd to the local drive and point sources.list to the harddrive instead of the cd.

that way Ubuntu will stop asking me for the cd all the time.

I dont want to just comment it out because i want to save bandwidth on the wan i just want it to point locally.

thanks

---

### Post by angryfirelord on 2007-05-23
I know you can add one through Synaptic. Here's the code that was pasted when I added it:
```
deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted
```

Edit: Oh sry I didn't see the "add to a local drive" part. Try dumping the "pool" part of the cd-rom to a folder and then link apt to it.

Perhaps something like this:
```
deb file:/*location_of_folder*/ feisty main restricted
```

---

