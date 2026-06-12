---
title: "modprobe ndiswrapper error"
date: 2005-10-17
forum: Desktop Environments
---

### Post by dizbah on 2005-10-17
Need help with the following issue as I am trying to setup my wireless:  Getting the following when running the sudo modprobe ndiswrapper command in terminal:

FATAL: Error inserting ndiswrapper (/lib/modules/2.6.10-5-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Operation not permitted

---

### Post by Dr. Nick on 2005-10-17
How did you install it? Synaptic? I recieved that error as well so I just downloaded it and compiled if I recall, Dont know why it does that, maybe this will bump it enough so someone else can see it :)

---

### Post by dizbah on 2005-10-17
I did it from Termal based on advise from the forums.

---

### Post by Dr. Nick on 2005-10-18
you may try to compile from source using the instructions provided here [https://wiki.ubuntu.com//SetupNdiswrapperHowto](https://wiki.ubuntu.com//SetupNdiswrapperHowto) before you do that though search for the file ndiswrapper.ko and make sure its where it says its at, If you use the search for files dialog make sure to search file system and not just home. If you find the file in another directory copy it over to where its trying to load from

---

