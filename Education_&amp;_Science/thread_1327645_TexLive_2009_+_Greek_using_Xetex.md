---
title: "TexLive 2009 + Greek using Xetex"
date: 2009-11-15
forum: Education &amp; Science
---

### Post by eumetaxas on 2009-11-15
This is in fact an update of this thread:

[http://ubuntuforums.org/showthread.php?p=6954563#post6954563](http://ubuntuforums.org/showthread.php?p=6954563#post6954563)

Synaptic has texlive 2007 which is working great.
If you like to have TexLive 2009 follow this:

**A: TexLive 2009 **

1: Download the install script here ([http://mirror.ctan.org/systems/texlive/tlnet/install-tl-unx.tar.gz](http://mirror.ctan.org/systems/texlive/tlnet/install-tl-unx.tar.gz))

2:extract it and open it in terminal

3:

```
sudo aptitude install perl-tk
```
to use the gui installation
4: make the /usr/local dir writeable for normal user (gksudo nautilus, right click, permissions) or create a folder /usr/local/texlive writable from normal user

5.in terminal

```
./install-tl -gui
```
and choose what you want to install (choose the greek language pack for greektex and xetex)

in the .profile file located in home folder add these lines

PATH=/usr/local/texlive/2009/bin/i386-linux:$PATH; export PATH
MANPATH=/usr/local/texlive/2009/texmf/doc/man:$MANPATH; export MANPATH
INFOPATH=/usr/local/texlive/2009/texmf/doc/info:$INFOPATH; export INFOPATH

logout and log in again

Using

```
tlmgr -gui
```

you can add-remove packages or update the database.

Using xetex and appropriate modifications in texmaker (utf8 interface & adding shortcuts for xelatex you can easily write unicode greek)

The only thing that is not working out of the box is **hyphenation in mixed Greek & English phrases**. I have found these 2 workarounds but only tested the first one.

1: [http://forum.hellug.gr/index.php?topic=1837.0](http://forum.hellug.gr/index.php?topic=1837.0)
2:[http://www.corelab.ntua.gr/~philaris/grlatex/hintelenhyphtexlive](http://www.corelab.ntua.gr/~philaris/grlatex/hintelenhyphtexlive)

Any addition/corrections/comments are helpful and welcome

Thank you

---

### Post by pmav99 on 2009-12-16
Thank you mate!

---

### Post by eumetaxas on 2009-12-16
You are welcome!

---

### Post by myle on 2009-12-16
The TexLive 2009 has been uploaded to Debian unstable. Will it be backported in Ubuntu soon?

Thanks for the guide!

---

### Post by eumetaxas on 2009-12-17
> Will it be backported in Ubuntu soon?
I have no idea. I am just an ordinary Ubuntu user. 

> Thanks for the guide!
My pleasure -  this is the opensource world all about:)

---

### Post by mindcircus on 2010-04-30
> The only thing that is not working out of the box is **hyphenation in  mixed Greek & English phrases**. I have found these 2 workarounds  but only tested the first one.

1: [http://forum.hellug.gr/index.php?topic=1837.0](http://forum.hellug.gr/index.php?topic=1837.0)
2:[http://www.corelab.ntua.gr/~philaris...lenhyphtexlive]("http://www.corelab.ntua.gr/%7Ephilaris/grlatex/hintelenhyphtexlive")

It does work out of the box. Take a look at polyglossia package. I find it much easier than the methods in the links.

[http://www.ctan.org/tex-archive/macros/xetex/latex/polyglossia/polyglossia.pdf](http://www.ctan.org/tex-archive/macros/xetex/latex/polyglossia/polyglossia.pdf)

---

### Post by eumetaxas on 2010-05-03
Thank you for the link!
I'll give it a try!

---

### Post by simosx on 2010-05-06
There is also a book (in Greek) on XeLaTeX and digital DTP,
[http://www.epikentro.gr/Book.php?id=698](http://www.epikentro.gr/Book.php?id=698)

The author is one of the guys who make all these things happen (see [http://obelix.ee.duth.gr/~apostolo/](http://obelix.ee.duth.gr/~apostolo/))

---

### Post by eumetaxas on 2010-05-07
Thank you Simos for the links. I follow your blog posts!
Why don't you also post them in the greek Ubuntu forum? [http://forum.ubuntu-gr.org/viewtopic.php?f=9&t=8479]("http://forum.ubuntu-gr.org/viewtopic.php?f=9&t=8479")
Eugenios

---

### Post by simosx on 2010-05-07
> **eumetaxas said:**
> Thank you Simos for the links. I follow your blog posts!
Why don't you also post them in the greek Ubuntu forum? [http://forum.ubuntu-gr.org/viewtopic.php?f=9&t=8479]("http://forum.ubuntu-gr.org/viewtopic.php?f=9&t=8479")

Thanks!
Feel free to post the links. It is very important to take the initiative to help others yourself when you learn something new! :-)

---

### Post by eumetaxas on 2010-05-08
[QUOTE=simosx;9257667It is very important to take the initiative to help others yourself when you learn something new! :-)[/QUOTE]

I totally agree!But i do not like to take credit for the work that somebody else has done - even if that is posting a weblink!

---

### Post by simosx on 2010-05-11
> **eumetaxas said:**
> I totally agree!But i do not like to take credit for the work that somebody else has done - even if that is posting a weblink!

This goes a bit off-topic :-). The way this thing works, whether it is the academia, journalism or an Internet posting, is that you simply reference where you got the information. That is, you mention where you learned something.

In my case I learnt about the XeLaTeX by reading the website [http://planet.ellak.gr](http://planet.ellak.gr)
On [http://planet.ellak.gr/](http://planet.ellak.gr/), the e-typon blog is aggregated, [http://eutypon.gr/e-blog/](http://eutypon.gr/e-blog/) where they announced the new book.

For open-source to grow it is critical for everyone to take initiatives and pass important information around. For the XeLaTex book, if you really want to help this effort, I recommend to help with promoting it. Such initiatives with a tech book in the Greek language are rare, without help they'll die out. Go for it.

---

