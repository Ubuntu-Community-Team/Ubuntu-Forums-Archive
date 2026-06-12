---
title: "Can't install with configure, make..."
date: 2009-02-22
forum: General Help
---

### Post by PFRules on 2009-02-22
**Hi everyone.**

**1)** I'm trying to install compizconfig-settings-manager which requires python-defaults-2.5.2.
Thing is this package only has the following files:

[FONT="Courier New"]changelog
compat
control
control.in
copyright
debian_defaults
idle.1
idle.desktop
idle.menu
idle.py
idle.sh
python.desktop
python.doc-base.python-policy
python-policy.sgml
python.postinst.in
python.postrm.in
python.preinst.in
python.prerm.in
pyversions
pyversions.1
pyversions.py
README.Debian
rules
stamp-build
valgrind-python.supp[/FONT]

How do I install it? No 'configure' nor 'make'.
I don't have Internet access in my PC, so I can't use Synaptic or aptitude/apt-get.
When I need a package I download it in my work's PC and bring it home in my USB stick.

------------------------------------------------------------------------

**2)** I'm also trying to install Midnight Commander which requires glibc (also needed by compizconfig).
When I 'configure' I get:

[FONT="Courier New"]...
running configure fragment for sysdeps/unix/sysv/linux
checking for grep that handles long lines and -e... (cached) /bin/grep
checking for egrep... (cached) /bin/grep -E
checking installed Linux kernel header files... 2.0.10 or later
*** On GNU/Linux systems the GNU C Library should not be installed into
*** /usr/local since this might make your system totally unusable.
*** We strongly advise to use a different prefix.  For details read the 
FAQ.
*** If you really mean to do this, run configure again using the extra
*** parameter `--disable-sanity-checks'.[/FONT]

**So I run 'configure --disable-sanity-checks' (no error message with this sentence) but when I 'make' I get:**

[FONT="Courier New"]mawk: scripts/gen-sorted.awk: line 19: syntax error at or near ]
mawk: scripts/gen-sorted.awk: line 19: runaway regular expression /, "", 
subd ...
rm -f /build/glibc-2.8/build/stamp.o; > /build/glibc-2.8/build/stamp.o
rm -f /build/glibc-2.8/build/stamp.os; > /build/glibc-2.8/build/stamp.os
rm -f /build/glibc-2.8/build/stamp.oS; > /build/glibc-2.8/build/stamp.oS
cd /build/glibc-2.8/build && ar cruv libc.a `cat stamp.o`
: /build/glibc-2.8/build/libc.a
cd /build/glibc-2.8/build && ar cruv libc_pic.a `cat stamp.os`
: /build/glibc-2.8/build/libc_pic.a
cd /build/glibc-2.8/build && ar cruv libc_nonshared.a `cat stamp.oS`
: /build/glibc-2.8/build/libc_nonshared.a
make[1]: *** No rule to make target 
`/build/glibc-2.8/build/Versions.all', required for 
`/build/glibc-2.8/build/abi-versions.h'.  Stop.
make[1]: leaving directory `/build/glibc-2.8/glibc'
make: *** [all] Error 2[/FONT]

What's wrong??? Help please! Thanx in advance.

**Mario.**

---

### Post by geirha on 2009-02-22
It's much easier and better to install .deb-packages, so I suggest you do that. [https://help.ubuntu.com/community/Synaptic/PackageDownloadScript](https://help.ubuntu.com/community/Synaptic/PackageDownloadScript)

---

### Post by cariboo on 2009-02-22
Wouldn't

```
sudo apt-get install compizconfig-settings-manager
```

be way easier.

You can install most packages using Add/Remove Programs, or Synaptic Package Manager.

Jim

---

### Post by m_duck on 2009-02-22
And for midnight commander, you can install it from the terminal with```
sudo apt-get install mc
```Check out [this psychocats link](http://www.psychocats.net/ubuntu/installingsoftware) for other info on installing software, plus a load of other stuff on the site too.

---

### Post by oldos2er on 2009-02-22
> **cariboo907 said:**
> Wouldn't

```
sudo apt-get install compizconfig-settings-manager
```be way easier.
  Jim

 Not when you don't have internet.

---

### Post by jocko on 2009-02-22
> **oldos2er said:**
> Not when you don't have internet.
But the op has to have access to internet from another computer?
Then just [download the packages]("http://packages.ubuntu.com/") (.deb files) you need and install them using gdebi, or:
```
sudo dpkg -i [COLOR=Red]filename[/COLOR].deb
```

---

### Post by WatchingThePain on 2009-02-22
Yeah what is that download?..there's supposed to be a 'readme' file in there.

---

### Post by geirha on 2009-02-22
> **jocko said:**
> But the op has to have access to internet from another computer?
Then just [download the packages]("http://packages.ubuntu.com/") (.deb files) you need and install them using gdebi, or:
```
sudo dpkg -i [COLOR=Red]filename[/COLOR].deb
```

Downloading from packages.ubuntu.com manually like that is likely to not work, as many packages require other packages to be installed first, and then you'll be running back and forth between the two to get one and one package. The link I provided in my previous post has instructions on how to use synaptic to create a download script that will download the packages with all its dependencies.

---

