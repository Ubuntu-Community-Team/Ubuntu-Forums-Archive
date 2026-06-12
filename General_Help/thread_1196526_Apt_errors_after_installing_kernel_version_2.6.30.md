---
title: "Apt errors after installing kernel version 2.6.30"
date: 2009-06-25
forum: General Help
---

### Post by codemyster on 2009-06-25
G'day, people of the Ubuntu forums. I come to you with a problem.

I compiled v2.6.30 of the Linux kernel and made a deb package with make-kpkg. Everything went as planned, and the kernel installed and runs fine, but there seems to be a bit of an issue. 

Every time I use Apt, I receive errors related to the package linux-image-2.6.30 (the one I compiled). Like if I'm using apt-get, it will install the packages I choose, but it ends up trying to configure the kernel image again, and it throws errors.

Perhaps I'm not being clear, so I'll just give you a log of what happens when I use apt-get, in this case, it is with Epiphany (but this happens with any package I try to install with apt-get).

[http://asdfasdf.ath.cx/aptgeterror.txt](http://asdfasdf.ath.cx/aptgeterror.txt)

Does anyone know what is causing this? It makes the update manager act odd and throw errors whenever an update is available. It's just generally an inconvenience.

---

### Post by codemyster on 2009-06-25
Nobody can help me out?

---

### Post by codemyster on 2009-06-25
I tried running the script that is returning the error (/etc/kernel/postinst.d/nvidia-common), but it seems to return fine. Is there a way to bypass running that? I don't have any nvidia devices, so should it make a difference?

---

### Post by sdennie on 2009-06-25
The problem is that dpkg doesn't think your nvidia drivers are installed correctly because part of the post installation script is returning an error.  That probably means that some feature that /etc/kernel/postinst.d/nvidia-common uses isn't available in your kernel (or the opposite, like if you compiled your kernel with Xen support).

---

### Post by codemyster on 2009-06-25
I see.

Would there be any consequences if I modified the script that is failing to just return successfully as soon as it's executed? Again, I don't have any Nvidia devices.

EDIT: I basically said "screw it" and tried it anyways, and it seems to have worked. I changed the script to just echo a little joke, and it worked fine afterwards. I understand this is probably the "brain-damaged MacGyver" workaround, but it worked nonetheless. Thanks for the help.

---

### Post by loomsen on 2009-06-25
You probably missed to compile the kernel-headers fitting your image...

make-kpkg kernel_image kernel_headers
would've built both. You need the headers to be able to compile modules against your kernel...

---

