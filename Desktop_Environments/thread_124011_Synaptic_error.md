---
title: "Synaptic error"
date: 2006-01-31
forum: Desktop Environments
---

### Post by Matt Houston on 2006-01-31
Hi 

Lately when I am trying to install an app with Synaptic I get the following error:

```
W: Couldn't stat source package list http://public.planetmirror.com breezy/free Packages (/var/lib/apt/lists/public.planetmirror.com_pub_plf_ubuntu_plf_dists_breezy_free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://public.planetmirror.com breezy/non-free Packages (/var/lib/apt/lists/public.planetmirror.com_pub_plf_ubuntu_plf_dists_breezy_non-free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://public.planetmirror.com breezy/free Packages (/var/lib/apt/lists/public.planetmirror.com_pub_plf_ubuntu_plf_dists_breezy_free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://public.planetmirror.com breezy/non-free Packages (/var/lib/apt/lists/public.planetmirror.com_pub_plf_ubuntu_plf_dists_breezy_non-free_binary-i386_Packages) - stat (2 No such file or directory)
```

And it does the same when I run the automatic updates. Any ideas how to fix this?

---

### Post by kaamos on 2006-01-31
Try hitting reload in synaptic. Could be that the server is down or something..

---

### Post by carlosqueso on 2006-01-31
comment out the planetmirror sites in your /etc/apt/sources.list and use the official ubuntu ones....if you need them...let me know.

---

### Post by Matt Houston on 2006-01-31
[QUOTE=carlosqueso]comment out the planetmirror sites in your /etc/apt/sources.list and use the official ubuntu ones....if you need them...let me know.[/QUOTE]

Did the trick, thanks!

---

### Post by CrackersKeenan on 2006-02-06
Can anyone tell me what the official site is for the hoary backports?  Preferably in a form along the lines "paste this into sources.list" format  :)

None of the mirrors seem to work anymore...

Thanks!

-- CK

---

### Post by Madpilot on 2006-02-06
[https://wiki.ubuntu.com/UbuntuBackports](https://wiki.ubuntu.com/UbuntuBackports) has this Hoary entry:
```

deb http://archive.ubuntu.com/ubuntu hoary-backports main universe multiverse restricted

```

The Backports project went "official" before Breezy was released, and the unofficial repos closed down, AFAIK.

---

