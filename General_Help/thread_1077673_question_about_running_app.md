---
title: "question about running app"
date: 2009-02-22
forum: General Help
---

### Post by ElCanguroEstepario on 2009-02-22
Hi!

I am using kubuntu gutsy, I've installed a set of tools for fMRI analysis named FSL. Although I'am able to run most apps includad by just typing the name in the console, for some this doesn't seem to know. More precisely, I have to run an app named "fsl2ascii", whose executable file is in /usr/lib/fsl, but just clicking on it doesn't work (wine opens) and neither dos typing the name on the terminal (it says the file doesn't exist).

Does anybody know how I might be able to run this app?

thanks!

Enzo.

---

### Post by yther on 2009-02-22
According to [FSLView's home page]("http://fsl.fmrib.ox.ac.uk/fsl/fslview/"), the app you need to run is "fslview".  Looks like it's a QT app, so there's probably a menu item in KDE somewhere.  Did you try typing "fsl" in the Search bar on the menu?

Also, normally you don't find executables living in /usr/lib; that's for shared libraries and such.  If you open Synaptic, find the package and hit Properties, you can get a list of all files it installed.  I do see "fslview" in the repositories, so did you install it that way or manually?

Bear in mind I know nothing about this package, so this is just general advice.  :)

---

