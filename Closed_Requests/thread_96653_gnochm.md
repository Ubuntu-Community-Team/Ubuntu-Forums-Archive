---
title: "gnochm"
date: 2005-11-29
forum: Closed Requests
---

### Post by duffman25 on 2005-11-29
[http://packages.ubuntu.com/dapper/gnome/gnochm](http://packages.ubuntu.com/dapper/gnome/gnochm)

originally requested here:
[http://ubuntuforums.org/showthread.php?t=95075](http://ubuntuforums.org/showthread.php?t=95075)

but since there was no answer from the backport team I'm re-requesting it. Feel free to delete this thread if it considered unnecesary.

Thanxs

---

### Post by strikeforce on 2005-11-29
builds fine.

However install generates  unmet deps.

The following packages have unmet dependencies:
  gnochm: Depends: gconf2 (>= 2.6.2-1) but it is not installed
          Depends: python-gtk2 (>= 2.2.0) but it is not installed
          Depends: python-glade2 (>= 2.2.0) but it is not installed
          Depends: python-gnome2 but it is not installed
          Depends: python-gnome2-extras but it is not installed
          Depends: python-chm (>= 0.8.2-2) but it is not installable
          Depends: shared-mime-info but it is not installed

---

### Post by jdong on 2005-11-29
Discussion in progress about this on the mailing list, cannot be installed without newer python chm backend.

---

### Post by duffman25 on 2005-11-29
[QUOTE=jdong]Discussion in progress about this on the mailing list, cannot be installed without newer python chm backend.[/QUOTE]

Is there any inconvenience in backporting those dependencies as well?

---

### Post by jdong on 2005-11-29
Right now, we're investigating if backporting the dependencies has any side effects (i.e. introducing incompatibilities with existing packages)

---

### Post by duffman25 on 2005-11-29
[QUOTE=jdong]Right now, we're investigating if backporting the dependencies has any side effects (i.e. introducing incompatibilities with existing packages)[/QUOTE]

ok, thanxs for the information.

---

### Post by strikeforce on 2005-11-29
Sorry jdong for doing half a job.  I was running late to work :(

The problems of working and living on the opposite side of the globe :)

---

### Post by jdong on 2005-11-29
gnochm is now clear for backporting.

---

### Post by duffman25 on 2005-11-30
[QUOTE=jdong]gnochm is now clear for backporting.[/QUOTE]
thanxs.

---

### Post by duffman25 on 2005-12-02
[QUOTE=duffman25]thanxs.[/QUOTE]

it's taking a bit long the population of backports in the archive. Is there any problems?

---

