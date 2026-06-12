---
title: "Control D on Boot Up Problem"
date: 2005-05-06
forum: Desktop Environments
---

### Post by qa1433 on 2005-05-06
Hi all,
When booting  the process stops with an fsck error. the proceedure recommends doing a Control D wich works. How can I repair this?
Thank you,
Paul

---

### Post by arnieboy on 2005-05-06
if it throws u into a shell try doing a "e2fsck /dev/hdaX" where X is the root directory for ubuntu. DONT type X. Type the actual number.  
Ctrl D is for exiting.

---

### Post by qa1433 on 2005-05-06
arnieboy,
Thanks for your help! That seem to do it.

paul

---

### Post by vince-ubuntu on 2005-05-28
Hi,
have you really tried to run e2fsck at statup? The partition which seems to cause the problem for me is /. And when I run e2fsck on it, it says that it is not recommended to run it on a mounted partition. I am not sure it is really wise to do that in my case...

Was it your / partition that had "unrecognized feature"?
Vince

---

### Post by N17R0 on 2005-05-28
[QUOTE=vince-ubuntu]Hi,
have you really tried to run e2fsck at statup? The partition which seems to cause the problem for me is /. And when I run e2fsck on it, it says that it is not recommended to run it on a mounted partition. I am not sure it is really wise to do that in my case...

Was it your / partition that had "unrecognized feature"?
Vince[/QUOTE]

Hi I also got a boot error, but I could fix it to boot the ubuntu cd in rescue mode (typ "rescue" at boot prompt)
and then once you are in your /root shell typ: 
```
umount /dev/hdaX
```
*Note where X is behind /dev/hda there you must add your root partition number.

Now you can do a **fsck** without that scary message  ;-)

---

### Post by vince-ubuntu on 2005-06-12
Hi,

here is how I fixed my problem:

[http://www.mail-archive.com/trilug@trilug.org/msg26479.html](http://www.mail-archive.com/trilug@trilug.org/msg26479.html)

thanks for your help!
Vince

---

