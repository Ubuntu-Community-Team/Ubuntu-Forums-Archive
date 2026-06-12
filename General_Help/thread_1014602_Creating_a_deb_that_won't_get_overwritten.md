---
title: "Creating a deb that won't get overwritten"
date: 2008-12-18
forum: General Help
---

### Post by lykwydchykyn on 2008-12-18
Ok, here's my situation:

I grabbed sourcecode for a package using apt-src, made some modifications, and created a deb with debuild.  

Every time I compile the .deb file, the version of the file gets "1ubuntu1" appended to its name.  The problem is, the version that's actually in the repo has "3ubuntu1" or something like that in its name.

So every time I upgrade, my modified version looks like an old version and APT wants to "upgrade" it to the repo version.  

I know I can pin packages, and I know that synaptic allows me to force a version.  I'd really rather *not* pin the package, and in any case I haven't found a way that Synaptic, Adept, and aptitude all mutually recognize (yes, I use all three at different times).

What I'd like to do is figure out how I can control the versioning of the deb file so that my version doesn't get "upgraded".  I tried changing the name of the file, and that didn't work.  I tried grepping through the debian directory in the source to find where I could change the version, but I couldn't find anything.

Anyone have a suggestion?

---

### Post by zvacet on 2008-12-18
In synaptic find your package,click on it>**package tab>lock version**.

---

### Post by jocko on 2008-12-18
Does the method you use create a "real" .deb file using files in a debian directory in the source directory?
Edit: re-read your post and saw that you do...
In that case the version number is set in the debian/changelog file.

---

### Post by lykwydchykyn on 2008-12-18
> **zvacet said:**
> In synaptic find your package,click on it>**package tab>lock version**.

thanks but, if you read my post, you'll see that I also use adept updater and sometime aptitude, and neither of them respect synaptic's "lock version" option.

---

### Post by gTinker on 2008-12-18
[QUOTE=lykwydchykyn]
I know I can pin packages, and I know that synaptic allows me to force a version.  I'd really rather *not* pin the package, and in any case I haven't found a way that Synaptic, Adept, and aptitude all mutually recognize (yes, I use all three at different times).[/QUOTE]

I certainly won't argue with your choice even if I don't understand what you'd have against pinning. 

If you pin in the /etc/apt/preferences file I would expect all frontends to the Advanced Packaging Tool to honour it. That has been my experience, it sounds like you're saying it doesn't work for you.

This won't help with your issue, which I believe you've already had an answer for but just something I thought I'd mention because of our different experiences.

---

