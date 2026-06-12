---
title: "gtk warning when using vmware on command line"
date: 2011-12-14
forum: Desktop Environments
---

### Post by jamesbon on 2011-12-14
I use vmware and when via command line I do

```
sudo vmware-fuseUI
```

I get following warning


```
(vmware-fuseUI:4188): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

```

upon doing some search I found package
```

 sudo aptitude search gtk | grep murrine
p   gtk2-engines-murrine            - cairo-based gtk+-2.0 theme engine   

```
but when I try to install it 

```
 sudo aptitude install gt2k-engines-murrine
Couldn't find any package whose name or description matched "gt2k-engines-murrine"
Couldn't find any package whose name or description matched "gt2k-engines-murrine"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
Need to get 0 B of archives. After unpacking 0 B will be used.

```

So what did I do wrong in above ?

---

### Post by gmargo on 2011-12-15
> **jamesbon said:**
> 
```
 sudo aptitude install gt[COLOR=Red]2k[/COLOR]-engines-murrine
Couldn't find any package whose name or description matched "gt[COLOR=Red]2k[/COLOR]-engines-murrine"

```

It is a simple misspelling.  Should be "gt[COLOR=Red]k2[/COLOR]-engines-murrine"

---

### Post by jamesbon on 2011-12-15
Sorry it was  a type error while posting on forum,had it been an error at my end it would have given no such package with given name.After your message I rechecked and 
did
```

sudo aptitude install gtk2-engines-murrine
```
but the warning still remains the same.

---

### Post by thaelim on 2011-12-16
It's only a low-important warning anyway. Unless the vmware applications looks terrible and un-themed, I wouldn't worry about it.

---

### Post by drmrgd on 2011-12-16
On my VMware installation at work, I get that error a lot as well.  As thaelim says, though, I think it's a low importance warning, and I don't seem to see any negative effects from it.

---

