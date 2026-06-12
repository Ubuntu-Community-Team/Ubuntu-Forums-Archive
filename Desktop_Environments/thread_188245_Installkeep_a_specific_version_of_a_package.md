---
title: "Install/keep a specific version of a package?"
date: 2006-06-03
forum: Desktop Environments
---

### Post by BoneKracker on 2006-06-03
I'm installing an application that requires postresql 7.4 or 8.01 (and specifically will not run with anything higher, yet).

postgresql 7.4 is still in the repositories, but I'm concerned when I go to install it that it will be automatically upgraded when I do a routine apt-get upgrade.  (And that it tells me that 7.4 is "obsolete".)

How do I tell the system that I want to keep 7.4 and not upgrade it?  I did try to search these forums but I couldn't find it.

Meanwhile, I'll start digging more deeply through the apt and dpkg documentation.

Thanks.  :)

---

### Post by meng on 2006-06-03
Easiest way is to install the version you want. Then go to synaptic, highlight that package and then go to the menu Packages > Lock Version.

---

### Post by BoneKracker on 2006-06-03
Beautiful!

Thanks.

---

### Post by el3ktro on 2006-12-20
> **meng said:**
> Easiest way is to install the version you want. Then go to synaptic, highlight that package and then go to the menu Packages > Lock Version.

Hello, I have a similar problem. I'm using Amanda, which is incompatible with the version of tar that I have installed. How can I see what other versions of tar are available in the repos - and how can I downgrade it? (On the command line, it's a GUI-less server).

Would be thankful for your help.

Tom

---

