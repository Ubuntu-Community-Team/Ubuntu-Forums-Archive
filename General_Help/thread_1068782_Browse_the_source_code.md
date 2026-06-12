---
title: "Browse the source code"
date: 2009-02-13
forum: General Help
---

### Post by pierref on 2009-02-13
Hello

Since "source is  the best documentation", I wonder if it is possible to browse the source code without having to download huge files to install or tarballs to extract. 

I would be very happy to surf through the (highlighted) code with a browser, clinking on links. Are there CVS repositories with a http interface that can do that for Ubuntu and variants?

Thanks for your advice. :)

---

### Post by jespdj on 2009-02-13
Ubuntu consists of the Linux kernel plus thousands of small and big programs, developed by thousands of different programmers, companies and other groups. The software of which of those programs do you want to see?

You can use the **apt-src** command to download the source code of Ubuntu packages.

---

### Post by jchiar on 2009-02-13
Yes there is.
[http://manpages.ubuntu.com/](http://manpages.ubuntu.com/)
There are 8 sections there, they can all be downloaded, and should be for any with such interests.

---

### Post by pierref on 2009-02-13
> **jespdj said:**
> Ubuntu consists of the Linux kernel plus thousands of small and big programs, developed by thousands of different programmers, companies and other groups. The software of which of those programs do you want to see?

You can use the **apt-src** command to download the source code of Ubuntu packages.

I want to see only the source of **netstat**.

Thanks to your answer, I could dive into the source of netstat. 

Just in case anybody else reads this: to use **apt-src**, you first have to install it with:

```
 sudo apt-get install apt-src
```

After that, you have to change to some directory of yours and issue:

```
apt-src install net-tools
```

This forum is great!

---

### Post by ViRMiN on 2009-02-13
Isn't viewing the source online via your browser also downloading it?

---

### Post by pierref on 2009-02-13
> **jchiar said:**
> Yes there is.
[http://manpages.ubuntu.com/](http://manpages.ubuntu.com/)
There are 8 sections there, they can all be downloaded, and should be for any with such interests.

Sorry **jchiar**, but I don't want to browse the docs, but the source code itself. **jespdj** gave me the answer. 

Thanks anyway.

---

### Post by pierref on 2009-02-13
> **ViRMiN said:**
> Isn't viewing the source online via your browser also downloading it?

It is not exactly the same to download only the pages you want to see and to download the whole package. I also prefer to click on links than to grep the whole structure for finding v.gr. the place where a function is defined. I once knew that this feature existed for some repositories, but now I would be very pleased to know if it exists for Ubuntu.

---

### Post by ViRMiN on 2009-02-13
> **pierref said:**
> It is not exactly the same to download only the pages you want to see and to download the whole package. I also prefer to click on links than to grep the whole structure for finding v.gr. the place where a function is defined. I once knew that this feature existed for some repositories, but now I would be very pleased to know if it exists for Ubuntu.

Fair point! :)

---

### Post by mc4man on 2009-02-13
This (apt-src install <whatever>) doesn't seem to be any different that 'apt-get source <whatever>' except that 'apt-src install' will install the build deps after downloading the source. diff,and dsc.
apt-get source will just get the source files, apply the diff

---

