---
title: "Installing teTeX using dpkg?"
date: 2005-10-21
forum: Desktop Environments
---

### Post by erik-the-red on 2005-10-21
I tried unsuccessfully under Hoary to get teTeX working through source compilation.

Instead, since I'm typing this on a T3 server, I'm planning to burn the *.deb files for tetex-base, tetex-bin, and tetex-extra.

Is there anyway I can install these using dpkg but also get the dependencies using aptitude if any are required?

---

### Post by neutro on 2005-10-21
I probably missed why you wouldn't use apt-get or Synaptic directly...

---

### Post by erik-the-red on 2005-10-21
I'm on 56K :D

---

### Post by funkenstein on 2005-10-21
well, being a total noob this is probably the by-way-of-africa bodge way, but *if* you have the breezy cd you could tell your sources-list to only look there for the software *hoping* that it's there. update synaptic or "sudo apt-get update" (would that be necessary?) and install it that way... or else just get tetex.deb (whatever :razz: ) from online in office/tinternet caffe or summat and burn a cd or use your usb key, if you have such things....

did that help or did I just say the blindingly obvious? feels like the latter :rolleyes:

---

### Post by mvandeg on 2005-11-08
I would not know how to have dpkg automatically install all dependencies. You can however have a look at packages.ubuntu.com, to see which dependencies are required by tetex-base, tetex-extra, etc, download them all to one directory 'blabla' and do

```
dpkg -i *.deb
```

---

### Post by Miguel on 2005-11-08
Hi Erik,

Forget about compiling from source. I did it once, when I was a (total) noob and didn't even know about package management, and I don't remember it as a very constructive experience. 

Installing from packages is easyer... and synaptic keeps track of the packages, in case you want to update (teTeX 3 will probably make it into Dapper Drake).

I've made a few dependency checks, by no means exhaustive, but it should work. First, download:
[list][*]texinfo 4.7 (ver. 4.7-2.2ubuntu2) ~2mb
[*] tetex-base  (ver. 2.0.2c8 ) ~54mb installed
[*] tetex-bin  (ver.2.0.2-30ubuntu3) ~9mb installed
[*] tetex-extras  (2.0.2c8 ) ~ 40mb installed
[/list]
Alright. Now we have to install these in the right order... and it happens to be the same as above. You should sudo dpkg -i texinfo*.deb, and then tetex-base followed by tetex-bin and then tetex-extras.

NOTE: I am 99.99% sure that neither texinfo nor tetex-base will require you more packages. But, on the other hand, tetex-bin WILL ask for things like libkpathsea3 and libxaw7. And I don't know if these are installed by default. However, these are much smaller packages.

NOTE 2: Just checked: libkpathsea3 and libxaw7 are dependencies of ubuntu-desktop (i.e. installed by default). This does not mean, however, that tetex-bin will not require more packages. Hopefully, if there are more needed packages, these will be small, so you can grab them using synaptic.

NOTE 3: Package versions are for Ubuntu 5.10.

There is probably one more step. That is installing support for UTF-8 encoding (ubuntu's default), which is not natively supported by LaTeX. I use the package latex-ucs. The version is a cryptic number: 20041017-1. It should not have unsolved dependencies.

Just before I forget!!! The documentation is not included if you install teTeX this way. You can install the docs with the package tetex-doc (2.0.2-c8 ).

Hope this helps,

Miguel

PS: Don't forget to select your processor (x86, amd64 or ppc) for tetex-bin and probably texinfo!!!

---

