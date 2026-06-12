---
title: "From ubuntu to vista"
date: 2008-12-06
forum: General Help
---

### Post by lbcrew on 2008-12-06
I got a vista cd from my friend and im currently using Ubuntu as my OS and when i go to download it it wont let me upgrade only do it customly and then it wont let me select a partion disk how do i fix this?

---

### Post by tjwoosta on 2008-12-06
?
are you trying to dual boot you mean?

to shrink your existing ubuntu partition you could use the ubuntu live cd

on the live cd go to "system-administration-partition editor"


if you want to you can probably just leave the newly made partition unallocated, then when you go to choose which partition to install vista to it will give you an option to use unallocated space


after installing vista it will write over your master boot record (replacing grub boot loader with the default windows boot loader)

to fix this you can use this link after installing vista
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

(just follow the first section where it says quick start)



if you are not trying to dual boot and you just want to install vista instead of ubuntu you should just be able to choose use entire disk when installing vista

---

### Post by mdurham on 2008-12-06
> **lbcrew said:**
> I got a vista cd from my friend and im currently using Ubuntu as my OS and when i go to download it it wont let me upgrade only do it customly and then it wont let me select a partion disk how do i fix this?
It's not clear what you mean. 
What is "download it"? 
"upgrade" what?
"it wont let me select a partion" what won't?

It's better to be a bit clearer, you will get more replies that way.
Cheers, Mike

---

