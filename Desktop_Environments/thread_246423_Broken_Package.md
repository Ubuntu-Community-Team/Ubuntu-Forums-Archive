---
title: "Broken Package"
date: 2006-08-29
forum: Desktop Environments
---

### Post by jonnymccullagh on 2006-08-29
I tried to install lphoto on Kubuntu Breezy from source a few weeks ago and I have now realised that Synaptics is broken. When I open it I get an error message:

E: The package lphoto needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

When trying to search for packages nothing comes backjust a blank screen - even in the Broken category.
Is there anything I can do to manually remove lphoto so I can get back to a normal situation of searching for and installing applications?
Thanks in advance for any help,
jonny

---

### Post by Ramses de Norre on 2006-08-29
Did you install if from the repo or from a third party .deb?
I'd try reinstalling it the way you installed it the first time.

---

### Post by jonnymccullagh on 2006-08-29
I tried reinstalling from the deb file but I get errors i.e. unable to find package python-all
However, I cannot add python-all without synaptics (apt) 
I'm going to guess the next reply is: Install python-all from source:(

---

### Post by ajgreeny on 2006-08-29
Have you tried uninstalling it rather than reinstalling?  It may remove the offending package and then you can try again if you have the nerve.

---

### Post by jonnymccullagh on 2006-08-29
how do I go about uninstalling it if it doesn't show up in Synaptic. Can I use dpkg and if so what should I type?
Thanks,
jonny

---

### Post by Ramses de Norre on 2006-08-29
```
sudo dpkg -r package_name
```

---

### Post by jonnymccullagh on 2006-08-30
Thanks but:
dpkg: error processing lphoto (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 lphoto


I would like to manually remove all references to lphoto but I do not know how to do this. I would prefer not to have to reinstall.
thanks,
jonny

---

### Post by ajgreeny on 2006-08-31
Just out of interest, have you tried reinstalling synaptic with 
sudo apt-get install synaptic
just to see if that gets that package up and running again? I suspect it may not help as it sounds as if lphoto has borked it rather than synaptic itself being bad.  Worth trying?

---

