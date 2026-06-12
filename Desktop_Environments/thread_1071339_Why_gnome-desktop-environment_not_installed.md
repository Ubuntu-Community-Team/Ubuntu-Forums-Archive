---
title: "Why gnome-desktop-environment not installed"
date: 2009-02-16
forum: Desktop Environments
---

### Post by BlackMask on 2009-02-16
Hi all,

First of all I have to say I'm new to linux. These days I'm trying to catchup linux concepts. This is my question. As I know GNOME is the default desktop enviromnent for Ubuntu. But Synaptic Package Manager shows me that following packages as not installed(I searched for different versions also). 
[LIST]
[*]gnome
[*]gnome-desktop-environment
[*]gnome-bin
[*]gnome-core
[/LIST]
But it says that some of these components are essential for GNOME (eg. gnome-core). Then how Ubuntu (GNOME) is working?? Are there any other packages which helps to run GNOME without these packages? Pleas explain. Thanks in advance.

Best Regards
BlackMask

---

### Post by utnubuuser on 2009-02-16
The desktop is called Ubuntu-desktop ( I think).

---

### Post by BlackMask on 2009-02-16
ubuntu-desktop package is not a seperate desktop environment. Is it? I think it is an all-in-one package which we can use to install all required items easily. Ubuntu's default desktop environment is GNOME. So there should be a installed package for GNOME (Which I still couldn't find??:().

---

### Post by utnubuuser on 2009-02-26
Yes, Gnome is in synaptic.

---

### Post by snova on 2009-02-26
> **BlackMask said:**
> But it says that some of these components are essential for GNOME (eg. gnome-core). Then how Ubuntu (GNOME) is working?? Are there any other packages which helps to run GNOME without these packages? Pleas explain. Thanks in advance.

They are metapackages. Take a look at how small they are- they don't actually contain anything. Like ubuntu-desktop, they merely depend on several other packages.

None of them are installed on my system either- yet, when I go to install one, it requires no additional dependencies but itself. So it's essentially installed already.

---

