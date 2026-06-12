---
title: "Minecraft blank screen when in browser"
date: 2010-10-27
forum: Gaming &amp; Leisure
---

### Post by Foxheadz on 2010-10-27
Ive been trying to play minecraft on my laptop but everytime i go to play I just get a blank screen. anyone know a fix?

---

### Post by Shazzner on 2010-10-28
Make sure you install the official JRE packages, on Ubuntu 10.10 they're in Software Center -> Canonical Partners -> Sun Java Platform Standard Edition Runtime Environment. Install sun-java6-jre, sun-java6-bin, sun-java6-plugins.

Restart your browser and try again.

Failing that, remove the icedtea-plugin package.

Failing that, try a different browser. I didn't have much luck with Opera, but Chrome and Firefox should work.

Failing that, try the standalone client. Download the Minecraft.jar to your home folder, right-click -> Open with Sun Java 6 Runtime. If it runs fine then you know it isn't a graphics driver issue. Perhaps remove OpenJDK and log off and then log back in.

Failing that, try the ubuntu hardware support forum as it could be a graphics driver issue.

Failing that, um err...if you did all that and still didn't have any luck or answers post here again and we can try a different approach.

---

### Post by donkyhotay on 2010-10-28
as with every other minecraft related support question we need to know:
version of ubuntu you're using
version on java you're using (most important)
system specs (especially graphics card)
playing in browser or out of browser

---

### Post by korn101 on 2010-10-28
Here we go:

[http://timashley.me/node/596](http://timashley.me/node/596)

This worked for me 100%

---

### Post by Foxheadz on 2010-10-28
> **Shazzner said:**
> Make sure you install the official JRE packages, on Ubuntu 10.10 they're in Software Center -> Canonical Partners -> Sun Java Platform Standard Edition Runtime Environment. Install sun-java6-jre, sun-java6-bin, sun-java6-plugins.

Restart your browser and try again.

Failing that, remove the icedtea-plugin package.

Failing that, try a different browser. I didn't have much luck with Opera, but Chrome and Firefox should work.

Failing that, try the standalone client. Download the Minecraft.jar to your home folder, right-click -> Open with Sun Java 6 Runtime. If it runs fine then you know it isn't a graphics driver issue. Perhaps remove OpenJDK and log off and then log back in.

Failing that, try the ubuntu hardware support forum as it could be a graphics driver issue.

Failing that, um err...if you did all that and still didn't have any luck or answers post here again and we can try a different approach.

I don't havse Sun Java Platform Standard Edition Runtime Environment under Canonical partners...

---

### Post by Shazzner on 2010-10-28
> **Foxheadz said:**
> I don't havse Sun Java Platform Standard Edition Runtime Environment under Canonical partners...

You might have to enable Partner repositories. In Software Center -> Edit -> Software Sources -> <enter pw> -> Other Software Tab -> Check Canonical Partners (should be the first one), then Close.

It should reload the sources and after a few seconds, Java and others will appear under Canonical Partners.

---

### Post by Foxheadz on 2010-11-01
After a bunch of different things i got java sun removed icedtea and used firefox and it worked

---

### Post by tru infini on 2012-02-28
> **korn101 said:**
> Here we go:

[http://timashley.me/node/596](http://timashley.me/node/596)

This worked for me 100%

That works just fine if you want to play offline mode
I think he is talking about playing online multi player minecraft at the website itself.

For some reason when I did a system update (I'm still on 10.04)
it did something to my java plugins and made so I couldn't play online anymore.

---

