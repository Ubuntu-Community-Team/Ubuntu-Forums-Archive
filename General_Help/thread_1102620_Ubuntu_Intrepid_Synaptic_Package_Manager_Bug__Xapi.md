---
title: "Ubuntu Intrepid Synaptic Package Manager Bug / Xapian Indexing fix?"
date: 2009-03-21
forum: General Help
---

### Post by ouija on 2009-03-21
Just curious if there is a patch or a fix for the Synaptic Package manager under Ubuntu Intrepid that address the fact that newly added or installed packages do not show up in the Manager until you actually run "sudo update-apt-xapian-index" from the terminal.. 

Kinda getting sick of having to run that command all the time when I add new software sources :p

---

### Post by zvacet on 2009-03-22
> Kinda getting sick of having to run that command all the time when I add new software sources

Do you mean when you add new repo to your source list or when you installed from source?If itis the first one then 

```
sudo apt-get update
```

is enough.If it is second you will not see compiled packages in synaptic.If you want to see them use checkinstall.

---

