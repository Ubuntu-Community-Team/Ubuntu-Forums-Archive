---
title: "OpenOffice 2.4/3.0 crashes on opening"
date: 2009-01-10
forum: General Help
---

### Post by Cryle on 2009-01-10
Hello,
Whenever I open the OpenOffice.org suite on my laptop, it loads, shows for a fraction of a second, then crashes.  The terminal output is as follows:

```
chris@chris-laptop:~$ Inconsistency detected by ld.so: dl-open.c: 260: dl_open_worker: Assertion `_dl_debug_initialize (0, args->nsid)->r_state == RT_CONSISTENT' failed!

```

Ran as root, it displays a message for a fraction of a second and closes.

I have tried this on two completely different laptops (moved hard drive), with the same result.

I have used Ubuntu for three years without this problem showing up before.  On my Dell Optiplex GX240 this problem does not appear.  I have tried installing packages straight from Sun with no luck.

Reinstalling would not be pleasant but doable.

Thanks,
Chris

P.S. The laptops I used were Acer TravelMate 2420 and a Dell Latitude C600.  The Acer had a bad 2GB RAM stick.  The Dell is fine.

---

### Post by abn91c on 2009-01-10
> **Cryle said:**
> Hello,
Whenever I open the OpenOffice.org suite on my laptop, it loads, shows for a fraction of a second, then crashes.  The terminal output is as follows:

```
chris@chris-laptop:~$ Inconsistency detected by ld.so: dl-open.c: 260: dl_open_worker: Assertion `_dl_debug_initialize (0, args->nsid)->r_state == RT_CONSISTENT' failed!

```

Ran as root, it displays a message for a fraction of a second and closes.

I have tried this on two completely different laptops (moved hard drive), with the same result.

I have used Ubuntu for three years without this problem showing up before.  On my Dell Optiplex GX240 this problem does not appear.  I have tried installing packages straight from Sun with no luck.

Reinstalling would not be pleasant but doable.

Thanks,
Chris

P.S. The laptops I used were Acer TravelMate 2420 and a Dell Latitude C600.  The Acer had a bad 2GB RAM stick.  The Dell is fine.
try removing just the **[COLOR="Red"]openoffice.org-gnome [/COLOR]**file

---

### Post by Cryle on 2009-01-10
Nope, still having the error.  Any other suggestions?

Thanks,
Chris

---

### Post by domoso on 2009-01-10
Did you try purging it from your system. dpkg --purge will typically rid your system of the package and all conf files. *shrugs*

---

### Post by abn91c on 2009-01-11
try this solution [http://ubuntuforums.org/showthread.php?p=6528404#post6528404](http://ubuntuforums.org/showthread.php?p=6528404#post6528404)

---

### Post by Cryle on 2009-01-12
Neither solution worked.  Maybe it has something to do with ld.so?  If so, how would I go about reinstalling it?

---

### Post by abn91c on 2009-01-12
> **Cryle said:**
> Neither solution worked.  Maybe it has something to do with ld.so?  If so, how would I go about reinstalling it?
in synaptic select the **purge **option, then reinstall, use the softpedia guide to upgrade to 3.0 [http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml](http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml)

---

