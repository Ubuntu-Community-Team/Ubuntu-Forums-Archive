---
title: "getting dvdrip edgy source on Dapper"
date: 2006-11-19
forum: Desktop Environments
---

### Post by foxy123 on 2006-11-19
I have a strange problem with getting an Edgy dvdrip source on Dapper. You know that you can include an Edgy of Feisty source in the sources.list and get the source of the applications to backport them either manually or with excellent programme called prevu. 

For example I have an Edgy source repo in my sources.list:
```
##EDGY SOURCE
deb-src http://archive.ubuntu.com/ubuntu edgy main restricted universe multiverse

```

If I run for example if I need a source of abs-guide I run
```
~$ apt-get source abs-guide
Reading package lists... Done
Building dependency tree... Done
Need to get 824kB of source archives.
Get: 1 http://archive.ubuntu.com edgy/multiverse abs-guide 4.0-1 (dsc) [573B]
Get: 2 http://archive.ubuntu.com edgy/multiverse abs-guide 4.0-1 (tar) [819kB]
Get: 3 http://archive.ubuntu.com edgy/multiverse abs-guide 4.0-1 (diff) [5209B]
Fetched 824kB in 25s (31.9kB/s)
dpkg-source: extracting abs-guide in abs-guide-4.0
dpkg-source: unpacking abs-guide_4.0.orig.tar.gz
dpkg-source: applying ./abs-guide_4.0-1.diff.gz

```

As you can see apt-get fetches the source from Edgy as it have a newer version.

However if I run it for dvd::rip:
```
~$ apt-get source dvdrip
Reading package lists... Done
Building dependency tree... Done
Need to get 526kB of source archives.
Get: 1 http://gb.archive.ubuntu.com dapper/multiverse video-dvdrip 1:0.52.5-0.0 (dsc) [591B]
Get: 2 http://gb.archive.ubuntu.com dapper/multiverse video-dvdrip 1:0.52.5-0.0 (tar) [520kB]
Get: 3 http://gb.archive.ubuntu.com dapper/multiverse video-dvdrip 1:0.52.5-0.0 (diff) [5555B]
Fetched 526kB in 8s (60.5kB/s)
dpkg-source: extracting video-dvdrip in video-dvdrip-0.52.5
dpkg-source: unpacking video-dvdrip_0.52.5.orig.tar.gz
dpkg-source: applying ./video-dvdrip_0.52.5-0.0.diff.gz

```

As you can see it uses a Dapper repository, though a higher version of dvdrip is in Edgy (0.98). It is a mystery for me. Maybe dvdrip package is called differently in Edgy and Feisty? Has anyone have a slightest idea why it is happening?

---

