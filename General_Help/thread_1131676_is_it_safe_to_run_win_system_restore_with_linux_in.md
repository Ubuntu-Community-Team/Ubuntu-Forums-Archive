---
title: "is it safe to run win system restore with linux installed?"
date: 2009-04-21
forum: General Help
---

### Post by alan ford on 2009-04-21
hi everyone, just joined the community.
problem: installed kubuntu via wubi dual boot with vista.
i had to do system restore to fix a driver problem in vista and some kubuntu files went havoc and i could not boot linux anymore.
i am going to install ubuntu in its own partition now.
question: will it be safe to do system restore in vista or will ubuntu be affected by it?
i hope to be soon in a position where i will not need windows anymore, but for the time being...
thanks

---

### Post by anaconda on 2009-04-21
No!

It isn't completely safe.
With my HP laptop windows restore overwrote grub (linux bootloader) but luckily not ubuntu, 
BUT I have heard, that with some manufacturers the system restore will restore the system to the original state, ie. destroy ubuntu completely. 

You just have to try. then you will know. Just make sure that you can restore grub before you try..

---

### Post by mikewhatever on 2009-04-21
If Grub bootloader was the only thing affected, the problem is easily fixed. [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by lisati on 2009-04-21
As noticed by others, when I've used a recovery partition on one machine, and a recovery DVD on another, I noticed the tendency of Windows to overwrite GRUB. That's easily fixed if Ubuntu survives the exercise, but this is not guaranteed, particularly if you installed Ubuntu via wubi.

It's probably safest to assume that the restore/recovery process will hurt at least part of your Ubuntu installation: ***make a backup of your important data "just in case".*** If you're lucky, the system restore process for your machine will have some kind of option for a non-destructive restore option, which will help reduce time getting Ubuntu up and running again.

---

### Post by alan ford on 2009-04-21
thanks guys,with wubi it happened for sure, hope i won't have to do it again

---

