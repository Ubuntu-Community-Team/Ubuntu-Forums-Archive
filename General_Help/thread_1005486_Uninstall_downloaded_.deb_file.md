---
title: "Uninstall downloaded .deb file?"
date: 2008-12-08
forum: General Help
---

### Post by blakjesus on 2008-12-08
How would one go about uninstalling something that they installed using a .deb package from somewhere like getdeb.com? I know you can uninstall software from the repos easily but i haven't found a way to get rid of programs that i got from 3rd party websites.

---

### Post by 4th guy on 2008-12-08
> **blakjesus said:**
> How would one go about uninstalling something that they installed using a .deb package from somewhere like getdeb.com? I know you can uninstall software from the repos easily but i haven't found a way to get rid of programs that i got from 3rd party websites.

You can do it via command line, but I don't know how to do that :(

You can also use synaptic. Launch synaptic package manager and search for the program from there. Right click and select one of the removal options and click on the apply button.

---

### Post by vishzilla on 2008-12-08
From the CLI
```
dpkg -P <PackageName>
```

---

### Post by Sealbhach on 2008-12-08
If you don't know the package name, do 
```

sudo dpkg -l
```

and look through the list.

Or if you can guess part of the packagname do

```
sudo dpkg -l | grep xxxxx  
```

(where xxxxx = the string of characters you want to search for).



.

---

### Post by blakjesus on 2008-12-08
Wow, thanks alot!

I learn more and more about Ubuntu everyday. :D

---

### Post by lykwydchykyn on 2008-12-08
Locally installed debs show up in synaptic under the "local and obsolete" section (click the "status" button at the bottom left).

---

### Post by mocoloco on 2008-12-08
Yup, any .deb files show up in Synaptic, doesn't matter if they're from online repos or installed locally.  The local filter will help you find them faster.
It'd be nice is there was a local filter in Add/Remove.

---

