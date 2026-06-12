---
title: "Installing Compiz (NOT xgl)"
date: 2006-09-15
forum: Desktop Environments
---

### Post by srunni on 2006-09-15
Hi,

I was able to successfully install XGL using the guide at help.ubuntu.com. As my graphics card (the ATi Radeon X300) is specifically listed at the site as compatible, it should just work. The problem is that I am using KDE. The three packages listed at [https://help.ubuntu.com/community/CompositeManager/InstallingCompiz](https://help.ubuntu.com/community/CompositeManager/InstallingCompiz) that GNOME users should install are "compiz," "compiz-gnome," and "csm." So I tried to install "compiz," "compiz-kde," and "csm." The only problem is that when I'm install "compiz-kde," I get the following error message: ```
compiz-kde: Depends: compiz (= 0.0.2-4ubuntu2) but 0.0.13.52-0ubuntu1 is to be installed
```

Has anyone seen this type of problem? And if so, how can I fix it?

Thanks

---

### Post by ayoli on 2006-09-15
try :

```
sudo apt-get install compiz compiz-core compiz-plugins csm cgwd cgwd-themes compiz-manager
```

then start compiz by running compiz-manager

instructions for kde here: [http://wiki.compiz.net/index.php/Aiglx/compiz_on_an_Intel_i915_video_card#KDE_start-up_script](http://wiki.compiz.net/index.php/Aiglx/compiz_on_an_Intel_i915_video_card#KDE_start-up_script)

---

### Post by srunni on 2006-09-15
I've tried doing that, but KDE just runs really slow. I know that my hardware is enough to run Xgl correctly because it works just fine from the Kororaa Xgl Live CD. I think I'll just try rotating the cube or something and see what happens.

---

