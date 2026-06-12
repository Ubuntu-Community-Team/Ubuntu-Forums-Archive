---
title: "Installing X-plane 9 Natty"
date: 2011-01-08
forum: Gaming &amp; Leisure
---

### Post by Omegaham on 2011-01-08
Hello, I've been browsing the forums for a while, and I still can't figure out what I'm doing wrong.

When I try to run the installer, here's what I get:
```
$ ./"X-Plane DVD Installer Linux"
./X-Plane DVD Installer Linux: error while loading shared libraries: libopenal.so.0: cannot open shared object file: No such file or directory
```

Following the instructions [here]("http://wiki.x-plane.com/Linux_Installation_Walkthrough"), (skip down to the 32-bit Ubuntu) I did the following:
Downloaded the newest installer, put on desktop.
libopenal1 was already installed.
Next, I followed the command to symblink libopenal.so.1 to libopenal.so.0.

```
$ sudo ln &#8211;s /usr/lib/libopenal.so.1 /usr/lib/libopenal.so.0
ln: target `/usr/lib/libopenal.so.0' is not a directory
```I've tried a couple other things, but it's not working. I'm definitely using a 32-bit version, so I don't have to do the 64-bit stuff.

```
$ uname -a
Linux bottini-HP-G61-Notebook-PC 2.6.35-24-generic #42-Ubuntu SMP Thu Dec 2 01:41:57 UTC 2010 i686 GNU/Linux
```Thanks in advance!

---

### Post by Omegaham on 2011-01-08
Never mind, I figured it out.

The instructions didn't tell me to change my directory to /usr/lib. I feel smart.

---

