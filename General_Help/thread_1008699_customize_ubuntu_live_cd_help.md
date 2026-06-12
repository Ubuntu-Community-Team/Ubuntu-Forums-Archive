---
title: "customize ubuntu live cd help"
date: 2008-12-11
forum: General Help
---

### Post by agdurrette on 2008-12-11
Ive look at this [https://help.ubuntu.com/community/LiveCDCustomization]("https://help.ubuntu.com/community/LiveCDCustomization") but i did not know if it changes the packages that it install also. I want to build Ubuntu Mini Edition (UME for short) kinda like dsl.

Thanks for any help
Andrew

---

### Post by Sorivenul on 2008-12-12
Unless you add or remove packages, I don't think the methods described in the link you provided will change anything by default.  If you add a program or programs, and dependencies, they will be included in your image during the install.  If you remove something, it will not be present during the install.  

For example, if you remove OpenOffice and replace it with Abiword and Gnumeric, OpenOffice will not be installed when the user runs Ubiquity.

I've never remastered Ubuntu in this way, as I personally use [Remastersys]("http://www.remastersys.klikit-linux.com/"), which is a very straightforward graphical tool.

---

