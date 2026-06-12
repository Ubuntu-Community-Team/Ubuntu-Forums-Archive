---
title: "How to download and open"
date: 2008-05-03
forum: Dell Ubuntu Support (CLOSED)
---

### Post by turners on 2008-05-03
Hi
can anyone tell me how to download Adobe reader, Java, Flash player as I am new to ubuntu thanks:)

---

### Post by luisromangz on 2008-05-03
You shouldn't need to install Adobe Reader as the distro comes with its own document viewer. Flash and Java should be installable from the software repository or from Firefox itself.

---

### Post by gbrainin on 2008-05-03
The built-in PDF reader should be adequate for most uses, but if you must have Acrobat Reader, the Adobe website does have a *.deb file, though it's a little difficult to find, as I recall.

As for flash and Java, I think they're both part of the ubuntu-restricted-extras package, which you can find in the package manager program (System -> Administration -> Synaptic Package Manager).

---

### Post by niteshifter on 2008-05-03
Hi,

You can get Adobe Reader 8 from the medibuntu.org repositories. If you're using Gutsy (and I presume this applies to Hardy as well) you should already have access to that repo in Synaptic. 

You need these packages:

acroread
acroread-escript
acroread-plugins
mozilla-acroread

---

### Post by mano cazalet on 2008-05-03
For Adobe (skype, goggle earth and other stuff) you will have to add [medibuntu]("https://help.ubuntu.com/community/Medibuntu") repositories.

in hardy:

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list

```

```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

```

---

