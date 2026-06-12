---
title: "Uninstalling an application"
date: 2009-06-02
forum: General Help
---

### Post by chippanfat on 2009-06-02
[FONT=Tahoma][SIZE=4]Hi all.

I know this is a very basic question. But I'm a complete beginner with ubuntu.

So my question is, how do I un-install an application through the terminal?

Cheers[/SIZE][/FONT]

---

### Post by TheForumTroll on 2009-06-02
With apt-get:

sudo apt-get remove appName

Like: sudo apt-get remove firefox

There s a good how to here:
[http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html](http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html)

---

### Post by chippanfat on 2009-06-02
The application I want to remove is called KeePassX

That is the way it is in the application menu. But when I try this:
```

sudo apt-get remove KeePassX

```It tells me it cant find the application.

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package KeePassX

```

---

### Post by 3rdalbum on 2009-06-02
You type the name of the package that the program came from into apt-get remove, you don't type the name that appears in the Applications menu.

So you'd actually type:

```
sudo apt-get remove keepassx
```

You can also use Synaptic Package Manager to remove it in the same way.

Also note that using "apt-get" to remove a program only works if the program was installed from a Debian package or from the repositories. If you've compiled it yourself or installed it from a binary installer (.run, .sh, .bin etc) then Apt doesn't know about it.

---

### Post by chippanfat on 2009-06-02
Thats worked :)

Thankyou :D

---

