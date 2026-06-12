---
title: "opendicom + mono"
date: 2009-04-27
forum: General Help
---

### Post by eumetaxas on 2009-04-27
Hi all!!
i am trying to install **opendicom** [http://opendicom.sourceforge.net/](http://opendicom.sourceforge.net/)
As in a previous post i get this error 

```
opendicom-navigator: Depends: mono (>= 1.1.17.1) but it is not installable
  opendicom-sharp: Depends: mono (>= 1.1.17.1) but it is not installable
  opendicom-utils: Depends: mono (>= 1.1.17.1) but it is not installable

```

**Mono is installed by default**. I have also tried to install mono from mono webside but i get an error about a missing library "libglitz.so.1" that i could not find, but i think this is for devel.

Since a newer version of mono is installed (mono-common 1.9) is there a way to "point", maybe make a link to the already installed mono to solve this?

Thank you!

---

### Post by directhex on 2009-04-27
> **eumetaxas said:**
> Hi all!!
i am trying to install **opendicom** [http://opendicom.sourceforge.net/](http://opendicom.sourceforge.net/)
As in a previous post i get this error 

```
opendicom-navigator: Depends: mono (>= 1.1.17.1) but it is not installable
  opendicom-sharp: Depends: mono (>= 1.1.17.1) but it is not installable
  opendicom-utils: Depends: mono (>= 1.1.17.1) but it is not installable

```

**Mono is installed by default**. I have also tried to install mono from mono webside but i get an error about a missing library "libglitz.so.1" that i could not find, but i think this is for devel.

Since a newer version of mono is installed (mono-common 1.9) is there a way to "point", maybe make a link to the already installed mono to solve this?

Thank you!

opendicom's dependencies are broken. Understand that this is their fault, not yours.

As a workaround, look at the "equivs" package, which can generate false packages to satisfy dependencies

---

### Post by eumetaxas on 2009-04-28
thanx for answering!
i had suspected that and this is why i looking for a workaround to bypass the error message. i'll give it a try and let you know.
Thank you!

---

### Post by eumetaxas on 2009-05-04
The package is created usin equivs but dpkg does not install the virtual mono-common package because "a later version is already installed".
Found a freeware stand alone viewer for dicom and i am ok for now.
Thank you!

---

