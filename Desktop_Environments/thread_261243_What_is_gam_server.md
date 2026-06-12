---
title: "What is gam_server?"
date: 2006-09-20
forum: Desktop Environments
---

### Post by QwUo173Hy on 2006-09-20
when I run 'top', I see that the process 'gam_server' is using 24% of my CPU. This happens fairly frequently. Do I need this process? Also, why does it demand so much CPU at certain times?

Thanks for reading,
Jarlath

---

### Post by Wolki on 2006-09-20
gam_server watches your file-system for changes. It's in the "gamin" package, you should find some more information there.

---

### Post by Cygnus on 2007-01-16
That is the usual answer, but who is using the info that gam_server provides ? What do I gain for having it running ? Or more importantly what do I lose if I disable it ?

I see many that have problems with it, and my 1.7 Ghz centrino is constantly using around 7-10 % cpu on gam_server.

It seems bo some gnome package so why would I want it on Kubuntu ?

---

### Post by Wolki on 2007-01-16
```
wolki@navi:~$ apt-cache rdepends gamin
gamin
Reverse Depends:
 |libgnomevfs2-0
 |libgnomevfs2-0
  apachetop
 |libgnomevfs2-0
  libgamin0
wolki@navi:~$ apt-cache rdepends libgamin0
libgamin0
Reverse Depends:
 |libgnomevfs2-0
 |libgnomevfs2-0
  kxmame
  kmediafactory
  swscanner
  styleclock
  showimg
  score-reading-trainer
  rkward
  pureadmin
  potracegui
  okle
  kzenexplorer
  kxstitch
  kwin-style-suse2
  kwin-baghira
  kuake
  ktemperature
  ktechlab
  ksocrat
  ksociograma
  kreetingkard
  kradio
  kpsk
  kpicosim
  koverartist
  kopete-meanwhile
  konserve
  koctave
  knet
  kerry
  kdar
  kat
  kalcul
  hotswap-gui
  guarddog
  dekorator
  datakiosk
  basket
 |apt-watch-backend
 |xfburn
 |python2.4-gamin
 |libthunar-vfs-1-2
 |libgnomevfs2-0
  libgamin-dev
  gamin
```

As you can see, quite a lot of KDE programs seem to need it. I'm not too familiar with it, so I don't know if any of these are default programs.

What you gain for having it running? Programs using gamin are notified if your filesystem changes, and can react to that. What you lose from not having it? At least the stuff in the second output.
You could try to remove it and look at the stuff that would disappear as well by doing "apt-get --simulate remove gamin" (it will look like it's removing them, but it's just simulating it).

I think it shouldn't take that much CPU though, so there is likely something wrong. I also remember having some problem with gam_server in the beginning of the dapper cycle, but haven't seen that in a long time

---

### Post by Cygnus on 2007-01-16
Yes I also noted that alot of programs would be uninstalled if I removed it. What I thought about was really to rename/move it such that it would not be found, as I have seen others doing that to get rid of the cpu problem.

And yes something is probably wrong, I see the problem on my laptop where as I mentioned it's constantly using 7-10%, but on my desktop machine I do not have this problem. They are both running dapper and similar applications.

However I did reduce the problem by reducing the poll frequency of gam_server to 10 seconds as mentioned in another thread, the cpu of gam_server then went down to 1% and I can live with that. Strange that it behaves so differently on my two machines though.

---

