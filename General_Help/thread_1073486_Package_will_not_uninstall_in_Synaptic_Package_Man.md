---
title: "Package will not uninstall in Synaptic Package Manager"
date: 2009-02-18
forum: General Help
---

### Post by blakescello on 2009-02-18
Hello all,

I am new to Ubuntu and the forums, so please be patient with me. I LOVE Ubuntu but I have run into my first problem (which took a whole month, a much better record than Windows). 

I have a broken printer driver installed. It never worked in the first place. At this point I just want to get rid of it, since it happens to be the wrong driver anyways.

When I re-install I get this error message:

Removing mfc9940dlpr ...
/var/lib/dpkg/info/mfc8840dlpr.postrm: 3: /etc/init.d/lpd: Permission denied
dpkg: error processing mfc8840dlpr (--remove):
  subprocess post-removal script returned error exit status 126
Errors were encountered while processing:
  mfc8840dlpr
gdebi-gtk: Fatal IO error 9 (Bad file descriptor) on X server :0.0

And when I try to uninstall the package I get this error message:

Removing mfc8840dlpr ...
/var/lib/dpkg/info/mfc8840dlpr.postrm : 3: /etc/init.d/lpd: Permission denied
dpkg: error processing mfc8840dlpr (--remove):
  subprocess post-removal script returned error exit status 126
Errors were encountered while processing:
  mfc8840dlpr
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install. Trying to recover:

I am not experienced with Linux commands, so please be detailed in your answer. 

Thanks!

---

### Post by drs305 on 2009-02-18
blakescello,

Welcome to the ubuntu forums.

First try to remove it via the command line:
```

sudo apt-get remove mfc8840dlpr

```

If you can't remove it because of errors, run:
```

sudo mv /var/lib/dpkg/info/mfc8840dlpr.postrm /var/lib/dpkg/info/mfc8840dlpr.postrm.old
sudo apt-get remove mfc8840dlpr

```

---

### Post by blakescello on 2009-02-18
Thanks! Linux also wins in customer support. :D

---

