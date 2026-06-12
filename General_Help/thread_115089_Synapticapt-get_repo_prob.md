---
title: "Synaptic/apt-get repo prob"
date: 2006-01-09
forum: General Help
---

### Post by Redeyes_Gambit on 2006-01-09
}{ey, I've been getting this error recently when starting Synaptic:

W: Couldn't stat source package list [http://public.planetmirror.com](http://public.planetmirror.com) breezy/free Packages (/var/lib/apt/lists/public.planetmirror.com_pub_plf_ubuntu_plf_dists_breezy_free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://public.planetmirror.com](http://public.planetmirror.com) breezy/non-free Packages (/var/lib/apt/lists/public.planetmirror.com_pub_plf_ubuntu_plf_dists_breezy_non-free_binary-i386_Packages) - stat (2 No such file or directory)

and these when hitting the "reload" button:


[http://public.planetmirror.com/pub/plf/ubuntu/plf/dists/breezy/free/binary-i386/Packages.gz:](http://public.planetmirror.com/pub/plf/ubuntu/plf/dists/breezy/free/binary-i386/Packages.gz:) Sub-process bzip2 returned an error code (2)
[http://public.planetmirror.com/pub/plf/ubuntu/plf/dists/breezy/non-free/binary-i386/Packages.gz:](http://public.planetmirror.com/pub/plf/ubuntu/plf/dists/breezy/non-free/binary-i386/Packages.gz:) Sub-process bzip2 returned an error code (2)

(I hit close on that error and then this one pops up:)

W: GPG error: [http://public.planetmirror.com](http://public.planetmirror.com) breezy Release: Unknown error executing gpgv

Whats wrong? I'm guessing it has something to do with some of the repositories being configured wrong or something but I'm not sure and wouldn't know what to do to fix it even if I was sure lol. Lil' help?

---

### Post by jasay on 2006-01-09
That repo doesn't exist anymore.  Remove it from /etc/apt/sources.list.  Assuming your using gnome ```
sudo gedit /etc/apt/sources.list
```  If you use kde you can use kate instead of gedit. [Here]("http://wiki.ubuntu-fr.org/doc/plf") are the new plf repos.
```
## http 100mbit/s mirror provided thanks to OVH http://ovh.com
deb http://packages.freecontrib.org/ubuntu/plf/ breezy free non-free
deb-src http://packages.freecontrib.org/ubuntu/plf/ breezy free non-free
```

---

### Post by Redeyes_Gambit on 2006-01-10
Ahh, thanks! That and a little improv got it all working again. Muchas gracias.

---

