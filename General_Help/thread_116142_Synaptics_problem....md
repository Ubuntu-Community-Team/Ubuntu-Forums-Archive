---
title: "Synaptics problem..."
date: 2006-01-12
forum: General Help
---

### Post by wham on 2006-01-12
When I open Synaptic Package Manager this pops up:

"W: Couldn't stat source package list [http://public.planetmirror.com](http://public.planetmirror.com) breezy/free Packages (/var/lib/apt/lists/public.planetmirror.com_pub_plf_ubuntu_plf_dists_breezy_free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://public.planetmirror.com](http://public.planetmirror.com) breezy/non-free Packages (/var/lib/apt/lists/public.planetmirror.com_pub_plf_ubuntu_plf_dists_breezy_non-free_binary-i386_Packages) - stat (2 No such file or directory)"

What does this mean?

---

### Post by ajgreeny on 2006-01-12
Try reloading all you repos by hitting the reload button top left

---

### Post by wham on 2006-01-12
This pops up when I do that:

[http://public.planetmirror.com/pub/plf/ubuntu/plf/dists/breezy/free/binary-i386/Packages.gz:](http://public.planetmirror.com/pub/plf/ubuntu/plf/dists/breezy/free/binary-i386/Packages.gz:) 302 Found [IP: 203.16.234.91 80]
[http://public.planetmirror.com/pub/plf/ubuntu/plf/dists/breezy/non-free/binary-i386/Packages.gz:](http://public.planetmirror.com/pub/plf/ubuntu/plf/dists/breezy/non-free/binary-i386/Packages.gz:) 302 Found [IP: 203.16.234.91 80]

---

### Post by lamego on 2006-01-12
Thats a problem with the planetmirror APT repos you are trying to use...

---

### Post by wham on 2006-01-12
Is there something I can do?

---

### Post by dcstar on 2006-01-12
[QUOTE=wham]Is there something I can do?[/QUOTE]
Select one of the other mirror sites from the available list.

---

### Post by wham on 2006-01-12
How exactly do I do that?

---

