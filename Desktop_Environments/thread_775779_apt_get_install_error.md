---
title: "apt get install error"
date: 2008-04-30
forum: Desktop Environments
---

### Post by figgles on 2008-04-30
I am getting an error when I try to install zsh-lovers:

```
The following NEW packages will be installed:
  zsh-lovers
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.

Need to get 511kB of archives.
After this operation, 918kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com hardy/universe zsh-lovers 0.5-0ubuntu3 [511kB]
Fetched 511kB in 2s (207kB/s)
(Reading database ... 121837 files and directories currently installed.)
Unpacking zsh-lovers (from .../zsh-lovers_0.5-0ubuntu3_all.deb) ...
dpkg-divert: error checking `/usr/share/vim/syntax/zsh.vim.original': No such file or directory
dpkg: error processing /var/cache/apt/archives/zsh-lovers_0.5-0ubuntu3_all.deb (--unpack):
 subprocess pre-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/zsh-lovers_0.5-0ubuntu3_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```I will dearly appreciate any help on the matter.

---

### Post by warp99 on 2008-04-30
> **figgles said:**
> I am getting an error when I try to install zsh-lovers:

```
The following NEW packages will be installed:
  zsh-lovers
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.

Need to get 511kB of archives.
After this operation, 918kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com hardy/universe zsh-lovers 0.5-0ubuntu3 [511kB]
Fetched 511kB in 2s (207kB/s)
(Reading database ... 121837 files and directories currently installed.)
Unpacking zsh-lovers (from .../zsh-lovers_0.5-0ubuntu3_all.deb) ...
dpkg-divert: error checking `/usr/share/vim/syntax/zsh.vim.original': No such file or directory
dpkg: error processing /var/cache/apt/archives/zsh-lovers_0.5-0ubuntu3_all.deb (--unpack):
 subprocess pre-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/zsh-lovers_0.5-0ubuntu3_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```I will dearly appreciate any help on the matter.

There is a problem with the package. So first I would do the following:
```
sudo apt-get -f install
```
to flush out the failed package then:
```
sudo apt-get clean autoclean
```
to remove any packages in cache, then:
```
 sudo apt-get install zsh-lovers
```
to install the package again. If it fails then something is wrong with the package and you need to speak with the maintainer so run:
```
sudo apt-cache show zsh-lovers
```
to get the maintainer information.

---

### Post by figgles on 2008-04-30
Didn't work and I've contacted the maintainer. Thanks!

---

### Post by warp99 on 2008-04-30
> **figgles said:**
> Didn't work and I've contacted the maintainer. Thanks!
After reviewing this a little closer here's the problem:
> dpkg-divert: error checking `/usr/share/vim/syntax/zsh.vim.original': No such file or directory
The package itself is missing a file, so it exits with an error status 2. This is definitely a maintainer issue.

---

