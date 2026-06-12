---
title: "Weird listing in GRUB"
date: 2008-12-20
forum: General Help
---

### Post by NobleRooster on 2008-12-20
I recently updated my Ubuntu boot to 8.10 and noticed a rather strange occurances in the Grub menu.  There seems to be 2 instances of Ubuntu installed  according to what I'm seeing in Grub.

Ubuntu 8.10, kernel 2.6.27-9-generic
Ubuntu 8.10, kernel 2.6.27-9-generic (recovery)
Ubuntu 8.10, kernel 2.6.24-21-generic
Ubuntu 8.10, kernel 2.6.24-21-generic (recovery)
Ubuntu 8.10. memtest86+


I've been booting up on the first one, and been kind of scared of the other one (2.6.24-21) not sure what it would do if I tried to boot up on it.  Does anybody know what's going on with it?  It doesn't seem to be taking up more of my HDD then it did originally (I'm dual booting with Vista on anotgher partition).

But yea, any help is appreciated.

---

### Post by dnairb on 2008-12-20
Nothing to worry about. You updated recently, and the kernel (core of the OS) has been updated. The entries listed as **kernel 2.6.24-21-generic** are the older kernels. The latest kernel is listed as the **kernel 2.6.27-9-generic**.

The older versions are still listed and accessible just in case updating to the newer version causes problems. As you are booting from the first in the list (2.6.27-9), you are using the updated kernel.

---

### Post by drs305 on 2008-12-20
YOu can choose to leave them, hide them, or remove the extra older kernels entirely from your system. 

Read this tutorial about grub kernel displays and the options for what to do about them:
[StartUp-Manager and Editing menu.lst]("http://ubuntuforums.org/showthread.php?t=818177")

---

### Post by NobleRooster on 2008-12-20
Alright, that's good.  Thanks for the help. :)

---

