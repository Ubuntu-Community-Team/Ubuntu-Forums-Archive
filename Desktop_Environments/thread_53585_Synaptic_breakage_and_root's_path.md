---
title: "Synaptic breakage and root's path"
date: 2005-08-01
forum: Desktop Environments
---

### Post by mannheim on 2005-08-01
I am a new user of Ubuntu, and got bitten by the following problem. If you do
```
sudo -i
echo $PATH

```
then you find that root's path is the following:
```
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11

```
I don't know enough about linux or Debian to know how standard this is; but having /usr/local/bin in front of /usr/sbin in the path caused me problems. Wanting the most recent version of "teTeX", I downloaded the source, compiled it myself and installed it manually. As a result, I had a symlink in /usr/local/bin to teTeX's version of "install-info". The result was that package installation (using Synaptic, for example) got broken. The problem is that teTeX's version of "install-info" conflicts with the Debian version that is installed in /usr/sbin.

Anyway, my question is -- how standard is it, to have /usr/local/bin in root's path? Would anything break if I removed it? It seems to me that Ubuntu packages don't put any binaries there.

Thanks,
Peter

---

### Post by Xian on 2005-08-01
It's a Debian thing for sure.
Posted below is my path for Debian and then for Gentoo.

Debian: /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11
Gentoo: /sbin:/bin:/usr/sbin:/usr/bin:/usr/bin/X11:/usr/local/sbin:/usr/local/bin

I think you stated the problem correctly.
There is a conflict using the source file.

If you extract the spec file from a Debain packaged version
you might find how to properly configure the installation.

But that is just a guess....

---

