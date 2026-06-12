---
title: "Installing wine offline? Is it possible?"
date: 2009-03-22
forum: Dell Ubuntu Support (CLOSED)
---

### Post by nhat on 2009-03-22
Hi everyone, I noticed that linux is developed with installing apps online. Which unfortunately isn't friendly for people who only have 56k or no internet.

Currently I downloaded wine-1.0.1.tar.bz2 and win_1.1.17.deb version. I'm logged in as su.

I extracted the package and do the ./configure command in the CLI for tar.bz2 package. I get an error message: configure: error: C compiler cannot create executable. Even the make command won't work after that.

After that I tried the .deb package. I get an error message: dependency is not satisfiable: linasound2. I checked synaptic package manager and it is already installed.

I'm sorry if I sound frustrating and annoyed but to install an application is taking so long and after doing research and printing out pages of helpfiles from ubuntu site. I haven't really gotten anywhere.

Any suggestions to my dilemma?

---

### Post by ugm6hr on 2009-03-22
What version of Ubuntu are you running?

i.e. 32- vs 64-bit and Hardy vs Intrepid

wine only requires 3 files to be downloaded, which can obviously be managed manually from [http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=wine](http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=wine)

Dependencies in Hardy: binfmt-support winbind wine

---

### Post by nhat on 2009-03-22
O sorry, it's a dell mini 9. I forgot that dell installed ubuntu's on other systems. I'll try your solution.

---

### Post by ugm6hr on 2009-03-23
You need these files then:
[http://dell-mini.archive.canonical.com/pool/universe/b/binfmt-support/binfmt-support_1.2.10_all.deb](http://dell-mini.archive.canonical.com/pool/universe/b/binfmt-support/binfmt-support_1.2.10_all.deb)
[http://dell-mini.archive.canonical.com/pool/main/s/samba/winbind_3.0.28a-1ubuntu4.4_lpia.deb](http://dell-mini.archive.canonical.com/pool/main/s/samba/winbind_3.0.28a-1ubuntu4.4_lpia.deb)
[http://dell-mini.archive.canonical.com/pool/universe/w/wine/wine_1.0.0-1ubuntu4~hardy1_lpia.deb](http://dell-mini.archive.canonical.com/pool/universe/w/wine/wine_1.0.0-1ubuntu4~hardy1_lpia.deb)

Just double-click them (in order - or try a different order if necessary).

---

