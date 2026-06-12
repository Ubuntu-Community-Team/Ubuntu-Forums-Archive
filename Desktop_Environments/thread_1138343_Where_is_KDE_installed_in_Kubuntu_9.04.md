---
title: "Where is KDE installed in Kubuntu 9.04?"
date: 2009-04-26
forum: Desktop Environments
---

### Post by kajman on 2009-04-26
I'm trying to compile KSmoothDock (i have problems using kooldock and compiz related problems with cairodock), but ./configure command gives me this error message:

checking for KDE... configure: error:
in the prefix, you've chosen, are no KDE libraries installed. This will fail.
So, check this please and use another prefix!

I've installed kde-devel and kde-dev and all dependencies and still no luck. 

I know I'll have to run the command like this: ./configure --prefix=/path/to/kde but I can't figure out a good path for it to work. Any suggestions? (even on another type of Mac OSX dock-like application, but for kde)

---

### Post by Monsieur Gonzalez on 2009-04-26
I might be wrong, but I think it will only work with KDE 3.x. Have you tried AWN (avant window navigator)?

---

### Post by mcduck on 2009-04-26
> **Monsieur Gonzalez said:**
> I might be wrong, but I think it will only work with KDE 3.x. Have you tried AWN (avant window navigator)?

Even if it does work with KDE4, compiling stuff usually requires having the development packages (not the actual working binaries).

So in this case when the configure script tells that it can't find KDE it means that it can't find the dev packages for KDE.

---

### Post by kajman on 2009-04-26
Is trying AWN really a good idea? I have Kubuntu installed, so it would mean a LOT of new packages to download, and also might slow my system down, isn't it right?

---

### Post by kajman on 2009-04-26
And to mcduck: I've installed KDE-devel and KDE-dev packages. What else should I install? Also what other dock-related KDE choices do I have?

---

### Post by megamouthbolt on 2009-05-12
I am so happy I found this thread. I have pretty much the same problem. So... is it that ksmoothdock is not compatible with KDE 4.x? That is what I understand.

If it is... :(

I really want a dock, and ksmooth looks pretty good.

---

### Post by kajman on 2009-05-13
I've also wanted a dock very much, but as fas as I can see, the choice is limited, and the docks out there aren't being developed any more. There's AWN but it's written for Gnome...

---

