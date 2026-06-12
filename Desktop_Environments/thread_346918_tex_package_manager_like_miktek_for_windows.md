---
title: "tex package manager like miktek for windows?"
date: 2007-01-26
forum: Desktop Environments
---

### Post by akvik on 2007-01-26
Hi,

Does anyone know if there's a package manager for tex in linux in the same way as miktek have one for windows? 

With the package manager for miktek you can browse and update all installed packages for tex, and it's supereasy and painless. Now, the packages are in synaptic instead, and it's difficult to get the "full" picture  of which packages are available to tex. 

:)

---

### Post by fdimmling on 2007-01-27
> **akvik said:**
> Hi,

Does anyone know if there's a package manager for tex in linux in the same way as miktek have one for windows? 

With the package manager for miktek you can browse and update all installed packages for tex, and it's supereasy and painless. Now, the packages are in synaptic instead, and it's difficult to get the "full" picture  of which packages are available to tex. 
:)

I am rather shure there is no package manager besides synaptic (or apt) for the tex packages and there should be no software manager bypassing apt (synaptic) otherwise the next security update might create a mess of your tex installation. 
However, what is the real problem? If you are missing a package you can easily add it from the CTAN repos. It is true that you cannot easily upgrade the tex (latex) system itself. If you want to do this you should uninstall the whole tex system using synaptic and install a different tex system from another source. I'm not up to date but some time ago the TeX-Live system was favored by some people complaining about the tetex system used by most Linux dictributions.

Friedrich

---

### Post by venik212 on 2007-02-01
Where should the Latex packages be installed? 
 I am having a hard time finding where they live.  For some reason, when I click SEARCH in Nautilus type the name of something I am looking for, it almost NEVER finds it, even when I know it exists.

---

### Post by akvik on 2007-02-02
I suppose that synaptic kind of _is_ the package manager for tex, but it's hard to get an overview of which packages to install, since they reside with all other packages in the repository. I seem to remember that miktex has packages that is not possible to find in synaptic, but that might be because it's already install, I don't know.

:)

---

### Post by fdimmling on 2007-02-02
> **akvik said:**
> I suppose that synaptic kind of _is_ the package manager for tex, but it's hard to get an overview of which packages to install, since they reside with all other packages in the repository. I seem to remember that miktex has packages that is not possible to find in synaptic, but that might be because it's already install, I don't know.
:)

The tex/latex packages can be found in /usr/share/texmf-tetex for the basic system and /usr/share/texmf for additional packages like musixtex or CJK. The usual latex packages you find starting from these directories in tex/latex.

BTW What packages are you missing? tetex should be rather complete. You find extra packages for some special needs like Chinese in cjk-latex or support for unicode input in latex-ucs, but the rest should already be there. Special styles you do not find in the default system you have to install from the CTAN server.

TeX is a system widely used in the Linux community much more than among Windows users. Thus you can expect a rather complete system here.

Friedrich

---

### Post by venik212 on 2007-02-03
Thanks.  I was using texlive, and discovered the needed packaes.  My problem was that I trusted Synaptic to not only install the packages, but also to configure the Latex system, which it did not.  So the packages were there, but TexLive and Lyx could not find them.  Once I ran texconfig all is well.

---

### Post by fdimmling on 2007-02-03
> **venik212 said:**
> Thanks.  I was using texlive, and discovered the needed packaes.  My problem was that I trusted Synaptic to not only install the packages, but also to configure the Latex system, which it did not.  So the packages were there, but TexLive and Lyx could not find them.  Once I ran texconfig all is well.

Now I see. Packages you are installing via Synaptic are configured for use with tetex which is the default Ubuntu TeX system and for use with Lyx too if it is using tetex. Packages you have installed manually in tetex also require running texconfig. The same holds if you are using another TeX system like TexLive. Is TexLive really better compared to tetex and in what respect?

Friedrich

---

### Post by venik212 on 2007-02-03
I installed TexLive only because TeTex is no longer supported.  The developer has switched his support to TexLive, which seems to work fine, althoguh I loved the MkTex package manager that I used to use under Windows.  Apparently, there is a way to use the same package manager under Linux as well.

---

### Post by fdimmling on 2007-02-03
> **venik212 said:**
> I installed TexLive only because TeTex is no longer supported.  The developer has switched his support to TexLive, which seems to work fine, althoguh I loved the MkTex package manager that I used to use under Windows.  Apparently, there is a way to use the same package manager under Linux as well.
I have heard rumours about that and I'm wondering what brand of Tex we will see in forthcoming Ubuntu versions. I like the convenience of using the distro package management which cares for all configuration tasks;-)  A few missing styles I have taken from CTAN. What is the practical advantage of using TexLive?

Friedrich

---

### Post by venik212 on 2007-02-03
I have no idea why Texlive is better or different from tetex, but since the developer of tetex (Thomas Esser, hence TeTeX) now supports texlive, I guess I'll follow him.  I always figure that live is better than dead.  I am really a fan of Miktex, but mostly because of their package and upgrade management, and Miktex is only available for Windows.

---

### Post by kakao on 2007-10-05
> **venik212 said:**
> ...and Miktex is only available for Windows.

No, it's not ;)
[A very short MPM introduction for Un*x users]("http://dojo.miktex.org/blogs/christian_schenk/articles/mpmunix.aspx"). There is a discussion about mpm vs. lindistro package management.

Installation:
[LIST=1]
[*][download MiKTeX tools]("http://sourceforge.net/project/showfiles.php?group_id=10783&package_id=160151")
[*]extract archive
[*]```
sudo aptitude install libcurl3-dev
```
[*]compile mpm
[/LIST]

Although I haven't used it. To be honest, I was really happy with the TeXnicCenter/MiKTeX combination and in particular with the autoinstall of packages/styles during compile time. Because I have to say I know little about packages and styles in tex and even less about installing/maintaining a tex system manually! I haven't found my way around all the texlive packages. I guess the next time I run into a "style not found" error it will be apt-cache search style/packagename.

Hence I really would lave to have it working with auto-apt for example. Does anyone know how to do it?

Cheers.

---

### Post by Maratonda on 2008-05-14
> **kakao said:**
> 
[download MiKTeX tools]("http://sourceforge.net/project/showfiles.php?group_id=10783&package_id=160151")


Hi, why is this link not working anymore?
Thanks

---

