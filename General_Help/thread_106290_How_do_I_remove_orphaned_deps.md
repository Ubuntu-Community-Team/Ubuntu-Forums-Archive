---
title: "How do I remove orphaned deps?"
date: 2005-12-20
forum: General Help
---

### Post by mad_phoenix on 2005-12-20
Howdy all,
  I've been playing with a lot of new software lately.  Naturally, the new packages I've installed have all had some dependencies associated with them, and when I've uninstalled those packages with apt-get the dependencies remain.
  Is there a way to check the system package tree and remove unneeded dependencies?  When I used to use gentoo I would do

emerge --update --newuse world (update all packages)
emerge --depclean (remove any orphaned deps)
revdep-rebuild (walk the package tree and make sure all deps are satisfied)

What would be an equivalent method with apt-get?  I'd really like to get the ~350MB of KDE packages I just installed removed without having to do it one by one.  Thanks!

---

### Post by rcerreto on 2005-12-20
deborphan will allow you to identify unneeded dependencies

There's also a graphical front end to it:  gtkorphan

---

### Post by mad_phoenix on 2005-12-20
So, perhaps my question goes a little deeper than I thought...

I installed KDE on top of Ubuntu by doing
```
sudo apt-get install kubuntu-desktop
```

Now, I want to remove it.  I removed the kubuntu-desktop meta-package using apt-get remove, but when I run deborphan it doesn't report any of the 350MB of deps that Kubuntu-desktop installed.  Is there another way to do this?

Thanks
--mad_phoenix

---

### Post by DarkAngel88 on 2005-12-20
Hi mad_phoenix,

I recently came across this thread and I think you should take a look...

[http://www.ubuntuforums.org/showthread.php?t=96048&highlight=apt-get+remove+kubuntu-desktop]("http://www.ubuntuforums.org/showthread.php?t=96048&highlight=apt-get+remove+kubuntu-desktop")

Hope it helps !!

DA

---

