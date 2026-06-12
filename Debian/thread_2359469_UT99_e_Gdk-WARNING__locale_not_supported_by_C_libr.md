---
title: "UT99 e Gdk-WARNING **: locale not supported by C library"
date: 2017-04-24
forum: Debian
---

### Post by palopdsthsa on 2017-04-24
Hi there, I am new in this forum, but I am not using Ubuntu as OS, but I am using a pure debian distro (Xfce4). I hope that there aren't any problem for that reason.
The question is that I wish to install UT99 on my pc and after following the instruction red [here]("https://help.ubuntu.com/community/Games/Native/UnrealTournament") I have got one problem like this:

```
Verifying archive integrity... All good.
Uncompressing Unreal Tournament 436-multilanguage Installer...................................................................................

Gdk-WARNING **: locale not supported by C library


```

giving the comand "locale" I get:
```
LANG=it_IT.utf8
LANGUAGE=
LC_CTYPE="it_IT.utf8"
LC_NUMERIC="it_IT.utf8"
LC_TIME="it_IT.utf8"
LC_COLLATE="it_IT.utf8"
LC_MONETARY="it_IT.utf8"
LC_MESSAGES="it_IT.utf8"
LC_PAPER="it_IT.utf8"
LC_NAME="it_IT.utf8"
LC_ADDRESS="it_IT.utf8"
LC_TELEPHONE="it_IT.utf8"
LC_MEASUREMENT="it_IT.utf8"
LC_IDENTIFICATION="it_IT.utf8"
LC_ALL=

```

And "locale -a"
```
C
C.UTF-8
it_IT.utf8
POSIX

```

Everytime I try to install "sudo sh unreal.tournament_436-multilanguage.run" the UT99's splash screen appear but is impossible to install.

Any advice?

Thank for reading it

---

### Post by Perfect Storm on 2017-04-24
Moved to Debian forum.

Have you tried this: [https://askubuntu.com/questions/359753/gtk-warning-locale-not-supported-by-c-library-when-starting-apps-from-th](https://askubuntu.com/questions/359753/gtk-warning-locale-not-supported-by-c-library-when-starting-apps-from-th)

---

### Post by palopdsthsa on 2017-04-24
Is here a debian forum?
But Thank for your suggestion that I had seen just few minutes ago. It doesn't solve my issue.

---

### Post by Perfect Storm on 2017-04-24
> **palopdsthsa said:**
> Is here a debian forum?
But Thank for your suggestion that I had seen just few minutes ago. It doesn't solve my issue.

Aye ^_^
We a have subforums for numerous of distros here.

---

