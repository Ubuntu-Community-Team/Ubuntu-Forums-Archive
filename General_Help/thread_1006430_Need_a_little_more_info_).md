---
title: "Need a little more info :)"
date: 2008-12-09
forum: General Help
---

### Post by jcagle on 2008-12-09
First off, thanks for a great product!! :popcorn:


I have a couple of questions though, some about the WuBi environment and a few about Ubuntu in general.

Here is a little background on my project.

I work for Texas Womans University, and we are installing a lab of 20 PC's. I was asked to make these systems dual-boot with Windows XP and Ubuntu, Authenticate/Join Active Directory, and be able to keep an image of it all using Ghost.

Ive got the first two parts done, I used WuBi to install the virtual disk, and used Likewise to auth/join AD. 

Since this is on an NTFS partition, my question is wether or not this will ghost properly. 

Symantec told me a few things, but i need to know what kind of bootloader is being used and what not, and also, since Ubuntu is joind to AD, would i need to recreate any SIDs or UUIDs like in windows after a restore?

Hopefully yall can help me out!

---

### Post by Jammanuser on 2008-12-09
> **jcagle said:**
> 

[COLOR="Red"]Since this is on an NTFS partition, my question is wether or not this will ghost properly.[/COLOR] 

Symantec told me a few things, but i [COLOR="Red"]need to know what kind of bootloader is being used[/COLOR] and what not, and also, since Ubuntu is joind to AD, would i need to recreate any SIDs or UUIDs like in windows after a restore?

Hopefully yall can help me out!

it uses the Windows bootloader...and it installs Ubuntu inside a **file** on the Windows partition, specifically a virtual disk, which acts like an ext3 partition so that it will work on **top** of Windows! so the answer to that question, then...is YES! :p

For more info on how Wubi works, see: [http://www.wubi-installer.org/](http://www.wubi-installer.org/)

Hope this helps! ;)

Cheers! :D

-jammauser

:guitar:

---

### Post by jcagle on 2008-12-09
Thanks Jamman, do you know about the SID question?

Whenever you restore a windows image, you need to change the SID so AD recognizes it as a new PC on the domain, do you know if this holds true for Linux as well?

Thanks for the reply!

---

### Post by Jammanuser on 2008-12-09
> **jcagle said:**
> [COLOR="Red"]Thanks Jamman, do you know about the SID question?[/COLOR]

Whenever you restore a windows image, you need to change the SID so AD recognizes it as a new PC on the domain, do you know if this holds true for Linux as well?

Thanks for the reply!

Nope...sorry! that's out of my line of know-how!

Hopefully someone else will come who can answer that question... ;)

Cheers! ):P

-jammanuser

:guitar:

---

### Post by Yownanymous on 2008-12-11
> **jcagle said:**
> Symantec told me a few things

Wow, they said something other than "you appear to have 3 million viruses. Ignore that all your other anti-viruses say you've only got one or two. Just send us the money..."

---

