---
title: "Pan in Gutsy, viewing images is broken"
date: 2007-10-20
forum: Desktop Environments
---

### Post by samwyse on 2007-10-20
Most images get cropped in half. I found also found a description of the bug here: [http://bugzilla.gnome.org/show_bug.cgi?id=477860](http://bugzilla.gnome.org/show_bug.cgi?id=477860)

I'm not knowledgable about patching packages, but I guess someone could make a working package using the information in the bugzilla thread :|

---

### Post by Zeroedout on 2007-10-22
hrmm, I havn't done this myself with pan, but as long as the patch is for the version in the repos, the generic way should work. First, you need the pan source, so switch to a directry ( cd directory ) and then grab the pan source.
```
sudo apt-get source pan
``` Then, you need to uncompress the tar.gz file (probably pan.orig.tar.gz or something to that effect) ```
tar xvzf  file.tar.gz 
```
then download the patch to the newly created directory and patch! (file.patch being the patch you downloaded)
```
patch < file.patch 
```
 After it finishes patching, build that deb ```
dpkg-buildpackage -rfakeroot
```
If that gives you errors (it was for me when I tried to build in gutsy, just do a " sudo -s -H " then run the above command). If you get any errors, post back and i'll see if I can guide you along, be warned though that i'm no master patcher.

---

### Post by samwyse on 2007-10-23
Thanks, it worked. But I guess I need to change the version number someway, because apt wants to update the package now.

---

### Post by bluebyt on 2007-10-23
The patch file extension is '.diff ', Do I have to change for '.patch'

---

### Post by samwyse on 2007-10-24
> **bluebyt said:**
> The patch file extension is '.diff ', Do I have to change for '.patch'
I think it can be named anything, just replace file.patch with whatever it's named. I actually didn't get the original filename, because my browser opens the file straight in a text editor, so I saved it from there.

I still need to fix the version number, any help with that?

---

### Post by bluebyt on 2007-10-24
When I do  "patch < pan.patch"
that asking "File to patch:"         

what name I put there?

I will look at the version number after!

---

### Post by KAding on 2007-10-24
I think you need to go into the pan/gui directory to apply the patch.

However, I have no idea how to run this command exactly:
```

dpkg-buildpackage -rfakeroot

```

It just gives me the following error:
```

dpkg-parsechangelog: error: cannot open debian/changelog to find format: No such file or directory
dpkg-buildpackage: unable to determine source package is

```

---

### Post by Billquinn1 on 2007-10-24
I had the same trouble but when I grabbed the deb from [http://darrenalbers.com/Pan/](http://darrenalbers.com/Pan/) it fixed the problem. I don't know if he already patched it or what, but it worked.

---

### Post by samwyse on 2007-10-25
> **Billquinn1 said:**
> I had the same trouble but when I grabbed the deb from [http://darrenalbers.com/Pan/](http://darrenalbers.com/Pan/) it fixed the problem. I don't know if he already patched it or what, but it worked.
I'm pretty sure I tried that exact same package before I went and compiled my own and it didn't fix the problem, but now it seems to work.

---

### Post by bluebyt on 2007-10-25
Thank you! it is working well now with that deb!

---

### Post by AlenlorDRot on 2007-11-04
Thanks for the link, the deb fixed it for me also.  It was that way on both of my Ubuntu machines.

---

