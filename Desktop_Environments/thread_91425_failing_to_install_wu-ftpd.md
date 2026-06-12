---
title: "failing to install wu-ftpd"
date: 2005-11-17
forum: Desktop Environments
---

### Post by pabc on 2005-11-17
I have a problem. I'm trying to set up a wu-ftpd on a lan with no external web access.

The only repo I have access to is the breezy CD which doesnt have the .deb on.

I've got the src and tried to install it that way but it fails on Make with missing yacc. The faq states replacing yacc with bison -y in the Makefile will solve the problem but I cant find reference to yacc in the Makefile and I dont have bison anyway.

Neither bison nor yacc are on the breezy cd.

is it possible to download the .deb from universe/multiverse/anywhere and install it via dpkg -i ?

Any other suggestions?

life is so much harder without a live net connection!

P

---

### Post by matthewv on 2005-11-17
download from here [http://packages.ubuntu.com/breezy/net/wu-ftpd](http://packages.ubuntu.com/breezy/net/wu-ftpd) and then install via ```
sudo dpkg -i <package-name.deb>
```

---

### Post by pabc on 2005-11-17
Cheers,

if only I'd know about packages.ubuntu.com a week ago!

I've done too many compiles from src recently which I could have just grabbed the debs for.

As it happens I got wu-ftpd on by grabbing the source for byacc, compiling/ installing that then the compile of wuftpd went like a dream.

Thanks for your help.

P

---

