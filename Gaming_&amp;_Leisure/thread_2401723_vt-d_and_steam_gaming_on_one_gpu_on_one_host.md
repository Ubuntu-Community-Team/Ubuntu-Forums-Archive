---
title: "vt-d and steam gaming on one gpu on one host?"
date: 2018-09-21
forum: Gaming &amp; Leisure
---

### Post by alex346 on 2018-09-21
I am interested in gaming some Windows games which I am collecting in Steam account.


I have read some great news about Wine-powered Steam but... Microsoft Flight Simulator (FS X) will not appear on the list. So I suppose that is specially hidden by MS.


Few months ago I have tried to do vt-d GPU passing to the kvm VM.
And due to lot of problems I have thought about totally losing that kind of thinking .That was after only reading the Steam on Linux news. Without knowledge about partial availability.


And my question is - is that possible to have GPU available to use in the Linux -  and, in special case - if needed - redirect it's power to the VM through VT-d technology ?


I am thinking abt somethinkg like:


1. working with mobo-integrated GPU
2. when needed starting the additional GPU, gaming on Linux
3. after that disabling the additional GPU, coming back to the integrated one.
4 After few houts starting the VM with redirected GPU and gaming on windows inside the VM.


I know that this could be hard to do but I would like to gain it without restarting linux-host :)


Is that any adding or removing kernel modules maybe?


regards

---

### Post by mastablasta on 2018-09-24
> **alex346 said:**
> 

[COLOR=#000000]And my question is - is that possible to have GPU available to use in the Linux[/COLOR] ...



What GPU?

nvidia, AMD, ARM and intel (most chips) are supported in linux. S3 (only some chips), other manufacturers (smaller ones) are not as i know.

for gaming it is still best to use windows (native OS). some games will work in wine. virtualisation is not good for gaming particularly not for GPU intensive games. some games have linux version (native) or are made to work with linux (wine or emulators...). many of commercial ones are available on GOG and Steam.

---

