---
title: "Nautilus Upset"
date: 2009-05-02
forum: General Help
---

### Post by Chamillionaire2 on 2009-05-02
Whats up?

OK, After updating to the latest version of ubuntu, i cant right click on my desktop [to create new file or change background Nor can i see any files or folders on my desktop, i also cant open a file browsers windows via the gnome menu.

The only way to view files is Terminal or i usually use konquer. After some discussions on #ubuntuhelp IRC it appears that my pc is using a nautilus that isent available for jaunty. here are some commands that produce some errors.

Code:

```
zack@zack-desktop:~$ nautilus
nautilus: error while loading shared libraries: libgnome-desktop-2.so.7: cannot open shared object file: No such file or directory
zack@zack-desktop:~$
```

```
zack@zack-desktop:~$ sudo apt-get install libgnome-desktop-2-7
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libgnome-desktop-2-7 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libgnome-desktop-2-7 has no installation candidate
```

Thats one of the packages nautilus said its having problems with and when ni try to install it i get that.


Anyone know how i can fix this?

See ya.

---

### Post by dcstar on 2009-05-02
> **Chamillionaire2 said:**
> Whats up?

OK, After updating to the latest version of ubuntu, i cant right click on my desktop [to create new file or change background Nor can i see any files or folders on my desktop, i also cant open a file browsers windows via the gnome menu.

The only way to view files is Terminal or i usually use konquer. After some discussions on #ubuntuhelp IRC it appears that my pc is using a nautilus that isent available for jaunty. here are some commands that produce some errors.

Code:

```
zack@zack-desktop:~$ nautilus
nautilus: error while loading shared libraries: libgnome-desktop-2.so.7: cannot open shared object file: No such file or directory
zack@zack-desktop:~$
```

```
zack@zack-desktop:~$ sudo apt-get install libgnome-desktop-2-7
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libgnome-desktop-2-7 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libgnome-desktop-2-7 has no installation candidate
```

Thats one of the packages nautilus said its having problems with and when ni try to install it i get that.


Anyone know how i can fix this?

See ya.

Check that your /etc/apt/sources.list has **no** references to old repositories and only the jaunty ones.

Then upgrade the nautilus package you have to the current (9.04) version.

---

