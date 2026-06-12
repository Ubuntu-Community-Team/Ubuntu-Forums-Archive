---
title: "Wubi - Vista - Compaq 6720s"
date: 2008-12-03
forum: General Help
---

### Post by stuv on 2008-12-03
Getting fed up of MS-Vill with Vista and it's buggy IE8, and all the cr@p of Office 2007, I have decided to install Ubuntu via Wubi on my notebook.

I had an extra partition, which I formatted, and instructed Wubi to install here.

Installation completed, and I rebooted. I chose Ubuntu at install menu, and no matter which option I try, it brings me to a prompt which says (initramfs)

Is there anyway that I can troubleshoot this?

./stuv &

---

### Post by Jammanuser on 2008-12-03
> **stuv said:**
> 
I had an extra partition, which I formatted, and instructed Wubi to install here.


uhh...i think the purpose of wubi is to install ubuntu on TOP of Windows like a normal Windows app...**not** on a separate partition! maybe that could be part of the problem...;)

Good luck!

-jammanuser

P.S. i would just install ubuntu on the extra partiton, regular, WITHOUT using wubi...for a number of reasons, if i were u! Cheers! :D

---

### Post by magmon on 2008-12-03
Yes, burn the iso to a disk and you can install ubuntu right into that fancy new partition!

---

### Post by Jammanuser on 2008-12-03
> **magmon said:**
> Yes, burn the iso to a disk and you can install ubuntu right into that fancy new partition!

yeah...good imput, magmon! i think that would be the **best** option... xD

Cheers! ;)

-jammanuser

:D

EDIT: stuv: u can burn the iso to a CD, using a program like [InfraRecorder]("http://infrarecorder.org/"), which burns it as an "image", and not as simple data! once u have, u will have ur Ubuntu Desktop CD, which u can then use to install ubuntu to the said partition!

---

### Post by magmon on 2008-12-03
Id have to agree, messing with partitions after wubi is dangerous lol.

---

### Post by Jammanuser on 2008-12-03
if u would like for me to help u create a Ubuntu Desktop CD, and then use it to install ubuntu to ur extra partition...u have but to ask! xD ;)

Cheers! :D

-jammanuser

P.S. first make sure, though, that u have the **right** ISO to burn to CD, lol! if u want to burn a ubuntu 8.10 Desktop CD, then the latest ISO will be called "ubuntu-8.10-desktop-i386"! Good luck!

---

### Post by stuv on 2008-12-03
Hi there

For some reason, it downloaded ubuntu-8.10-desktop-amd64 as the ISO, which as far as I can tell, wont work on my notebook. Perhaps this is why Wubi wont work either?

./stuv &

---

### Post by Jammanuser on 2008-12-03
> **stuv said:**
> Hi there

For some reason, it downloaded ubuntu-8.10-desktop-amd64 as the ISO, which as far as I can tell, wont work on my notebook. Perhaps this is why Wubi wont work either?

./stuv &

if its amd64, then that means that the ISO is for 64-bit systems! perhaps urs is only a 32-bit...? ;)

-jammanuser

P.S. i would still recommend doing a conventional install of ubuntu, instead of using wubi! 

EDIT: if u need one for 32-bit systems, u can download one from [here]("http://releases.ubuntu.com/8.10/")! i would recommend scrolling down the page, and choosing the  ubuntu-8.10-desktop-i386.iso.torrent one, although you'll need a BitTorrent client to download it! xD

---

### Post by stuv on 2008-12-03
I agree, but why would Wubi download that ISO.  Perhaps it detected my system incorrectly?

./stuv

---

### Post by Jammanuser on 2008-12-03
> **stuv said:**
> I agree, but why would Wubi download that ISO.  Perhaps it detected my system incorrectly?

./stuv

perhaps...but in my opinion, the reason that Wubi downloaded the wrong ISO is not important...what's important, is that u go ahead and download the **correct** ISO from the link i gave u! xD ;)

-jammanuser :D

---

### Post by ago on 2008-12-03
Press esc at boot after "Ubuntu" and try the other boot options, in case post the most descriptive output of the verbose mode.

Note that raid arrays and encrypted disks are NOT supported and some external disks might not work.

---

### Post by stuv on 2008-12-04
Hi there

I tried Wubi on another PC and it worked fine.  I have installed ubuntu on the spare partition that I have, and so far am happy. Thanks

./stuv &

---

### Post by Jammanuser on 2008-12-05
> **stuv said:**
> Hi there

I tried Wubi on another PC and it worked fine.  I have installed ubuntu on the spare partition that I have, and so far am happy. Thanks

./stuv &

ok...cool! :) glad u got it working...lol! ;)

-jammanuser

:D

---

