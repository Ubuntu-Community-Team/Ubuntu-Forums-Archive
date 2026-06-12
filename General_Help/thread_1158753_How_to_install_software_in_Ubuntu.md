---
title: "How to install software in Ubuntu"
date: 2009-05-14
forum: General Help
---

### Post by jnd_ce on 2009-05-14
[FONT=Comic Sans MS][SIZE=3]Hello, I am a new user of Ubuntu 8.10, I don't know how to install software in Ubuntu. In Windows any software can install by double click in .exe file. But in Ubuntu how can I install any software, please help me.[/SIZE][/FONT]

---

### Post by KhurramM on 2009-05-14
Goto:

[https://help.ubuntu.com/community](https://help.ubuntu.com/community)

Try to google a problem, if not solved then come to the forum.

Also u might find articles on this on:

Tutorials & Tips section.

---

### Post by pbpersson on 2009-05-14
Assuming you are on a newer version, you would go to System-->Administration-->Synaptic Package Manager OR you could use Add/Remove software from the main menu.

In one place you have access to over 26,000 packages created by companies and individuals all over the planet.  You can add any of them with a simple click of your mouse, it will automatically download and install any dependencies you need, and THEY ARE ALL FREE.

Oh, and you will also get automatic updates for any packages you install.

You also don't need to tell the program where to install, Ubuntu takes care of all that for you.

This functionality leaves Windows in the dust (in my opinion)

---

### Post by _Purple_ on 2009-05-14
Hi,
Go to System > Administration > Synaptic Package Manager. After entering your password, select the packages you want to install from the list and install them. Are you looking for any particular application?
You can also use the terminal(Applications > Accessories > Terminal) to install packages. Open terminal and type this command :
```
sudo apt-get install *packagename*
```

---

### Post by Hamchan on 2009-05-14
Lots of ways. Synaptic, Add-Remove Programs, apt-get from the terminal or double-clicking a .deb. There are more ways, but those are the easiest.

---

### Post by glotz on 2009-05-14
In Ubuntu you can compile any program from source.

---

### Post by petrus4 on 2009-05-14
> **glotz said:**
> In Ubuntu you can compile any program from source.

Not straight from a tarball, you can't, unless you want whole oceans of intense pain and suffering.  Library subpackaging means that you only try and compile anything from a tarball outside of the package manager if you have sadomasochistic tendencies.

Nothing against the OP, but they're also at least 3-6 months away from source compilation in any form.

OP, stick to Synaptic for now.  Most of the applications you want are fairly likely to be in the default Ubuntu install anyway.

---

### Post by kostkon on 2009-05-14
Check [this nice guide here]("http://www.psychocats.net/ubuntu/installingsoftware") if you want.

---

### Post by lovinglinux on 2009-05-14
You will find most information about installation in Ubuntu at [https://help.ubuntu.com/8.10/add-applications/C/index.html](https://help.ubuntu.com/8.10/add-applications/C/index.html)

If you are trying to install exe files, then they won't work. Windows applications are not designed to work on Linux. Nevertheless, some applications can be installed and run using Wine, which is basically an interpreter between Windows applications and Linux OS. If you install Wine, you will be able to double-click exe files and install them. Please notice that not all programs will work as expected or work at all. The best approach is to use alternatives designed specifically for Linux.

---

### Post by CatKiller on 2009-05-14
OT:

> **petrus4 said:**
> Not straight from a tarball, you can't, unless you want whole oceans of intense pain and suffering.  Library subpackaging means that you only try and compile anything from a tarball outside of the package manager if you have sadomasochistic tendencies.

You can compile from source with the package management system. You can get source packages easily enough through the package management system, but even if you get some newer version of the source you can use build-dep to automatically get all the dependencies that the package needs, and then use checkinstall to install your compiled program like any other packaged software.

The OP should definitely stick to Synaptic or Add/Remove Programs though.

---

### Post by hobo14 on 2009-05-14
> **glotz said:**
> In Ubuntu you can compile any program from source.

Come on!  I know you're trying to be helpful, but do you really think this answer is suitable for this guy?

@OP: for .deb files, if the program doesn't show up in the menu, you can probably find the file you need to click to run it in /usr/bin/
You can then use your middle mouse button to drag it to your desktop or somewhere else and make a link (like a windows shortcut).
Or (a little harder), right click on your menu, edit menus, new item, give it a name and browse for the file in /usr/bin/

---

### Post by jnd_ce on 2009-05-14
Thanks guys,thank you very much.

---

