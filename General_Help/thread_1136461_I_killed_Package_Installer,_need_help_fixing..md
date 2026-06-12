---
title: "I killed Package Installer, need help fixing."
date: 2009-04-25
forum: General Help
---

### Post by rmjohnson144 on 2009-04-25
I just aborted the installation of a program and now I can't install anything at all.  Is there a way to either continue where I left off or to reset it?

Thanks
-=Mark=-
it says in the lower left hand corner of the Package Installer menu that it is, "Installing Package File..."

---

### Post by zvacet on 2009-04-25
Try to uninstall that package with 

```
sudo apt-get --purge remove package_name
```

---

### Post by rmjohnson144 on 2009-04-25
> **zvacet said:**
> Try to uninstall that package with 

```
sudo apt-get --purge remove package_name
```

Thanks, that helped tremendously.

After running that command I got an error:
```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
```

Then when I tried to rerun the above it said there was a broken link.

I then went to Synaptic Package Manager and searched for the offending install program and it said I needed to fix the broken link. I found the option under the Edit tab and selected Fix Broken Packages.

Now all seems well again.

Thanks again
-=Mark=-

---

