---
title: "Help me fix this Dust Nodoka gtk theme bug"
date: 2009-04-03
forum: General Help
---

### Post by wersdaluv on 2009-04-03
I'm starting to tinker with gtk themes and my favorite one to play with are Dust and Dust-based themes. I believe that the [Dust Nodoka theme]("http://www.gnome-look.org/content/show.php?content=98574&forumpage=1") is the best derivative but it is not getting a lot of attention and its development stopped. 

I managed to fix a number of annoying bugs and I'm left with one bug, the drop down menus on Abiword. [[img]http://www.ubuntu-pics.de/thumb/11924/screenshot_06_xdvEwg.png[/img]](http://www.ubuntu-pics.de/bild/11924/screenshot_06_xdvEwg.png)
Notice the color? How do I make them lighter? So far, I haven't noticed any other application with that issue.

Thanks in advance :)

---

### Post by Vaun on 2009-04-08
I'll try to help you with a few of the bugs you're having.

Are you sure you are using the version from the git repository.  This theme uses the MODERN look.  I'm not seeing the issue on my end.

---

### Post by wersdaluv on 2009-04-08
This is odd. I think, I don't have the one from the git repository. I think, I got my nodoka engine from a PPA. I remember not being able to install from git because of compatibility issues.

---

### Post by Bastanteroma on 2009-06-03
I'm having no luck compiling Nodoka from git either.

rorty@rorty:~/nodoka$ ./configure --prefix=/usr --enable-animation
bash: ./configure: No such file or directory
rorty@rorty:~/nodoka$ 

Any ideas what I'm doing wrong?

---

### Post by MikeDK on 2009-07-04
yep no go for Jaunty 64bit either. same results, on autoreconf --install

also tryed the ./configure --prefix=/usr --enable-animation, same error

Kind Regards MikeDK

---

### Post by ibutho on 2009-07-05
> **Bastanteroma said:**
> I'm having no luck compiling Nodoka from git either.

rorty@rorty:~/nodoka$ ./configure --prefix=/usr --enable-animation
bash: ./configure: No such file or directory
rorty@rorty:~/nodoka$ 

Any ideas what I'm doing wrong?

If you are trying to install the git version, try
```
cd nodoka/gtk-nodoka-engine
mkdir m4
autoreconf -iv
./configure --prefix=/usr --enable-animation
make
sudo make install

```

---

