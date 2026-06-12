---
title: "MP3 player support - Lime Wire"
date: 2006-10-07
forum: Desktop Environments
---

### Post by hodad on 2006-10-07
I have just installed Ubuntu, and am trying to get access to an MP3 website (just bought my first player yesterday, so am now to MP3 players as well).

I joined the download service, but I need to install Lime Wire, and the download is in .rpm format, which Ubuntu cannot unpackage.   I tried the command:

sudo alien LimeWireLinux.rpm

on the file I downloaded, but the terminal doesn't recognize "alien" command.  Incidentally, I don't know what the "sudo" is either.   I see no references to "alien" anywhere else in my Ubuntu operating system.

How can I install LimeWireLinux?  Do I need to log in as "root"?  By the way, when I installed Ubuntu, their was no "root" setup, so I think I have full administrative rights, but not even sure about that - Man am I dumb!

Thanks in advance for your help.

---

### Post by taurus on 2006-10-07
```
sudo aptitude update
sudo aptitude install alien
alian LimeWireLinux.rpm
sudo dpkg -i LimeWireLinux.deb

```

For more info regarding sudo,

```
man sudo
```

---

### Post by hodad on 2006-10-07
Thanks for you response!

Worked well thru "sudo aptitude install alien"

"Alien LimeWireLinux.rpm" gives me the following error message in the terminal:

dave@dave-desktop:~$ alien LimeWireLinux.rpm
Must run as root to convert to deb format (or you may use fakeroot).
dave@dave-desktop:~$ sudo alien LimeWireLinux.rpm
File "LimeWireLinux.rpm" not found.
dave@dave-desktop:~$ cd Desktop
dave@dave-desktop:~/Desktop$ ls
gnome-terminal.desktop  LimeWireLinux.rpm  nautilus-home.desktop
dave@dave-desktop:~/Desktop$ sudo alien LimeWireLinux.rpm
Package build failed. Here's the log:
dh_testdir
dh_testdir
dh_testroot
dh_clean -k -d
dh_installdirs
dh_installdocs
dh_installchangelogs
find . -maxdepth 1 -mindepth 1 -not -name debian -print0 | \
                xargs -0 -r -i cp -a {} debian/limewire-free
dh_compress
dh_makeshlibs
dh_installdeb
dh_shlibdeps
dpkg-shlibdeps: warning: unable to find dependency information for shared library libXt (soname 6, path /usr/lib32/libXt.so.6, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libX11 (soname 6, path /usr/lib32/libX11.so.6, dependency field Depends)
dh_gencontrol
dpkg-gencontrol: error: current build architecture amd64 does not appear in package's list (i386)
dh_gencontrol: command returned error code 65280
make: *** [binary-arch] Error 1
find: LimeWire-free-4.12.6: No such file or directory

****

Do I need to somehow load those libraries it refers to?

---

### Post by taurus on 2006-10-07
Instead of installing LimeWire, why not use Frostwire since it's the same as LimeWire except it's open source and you don't get that annoying message about upgrading to the Pro version...

[http://www.frostwire.com/](http://www.frostwire.com/)

Click on the Ubuntu/Debian icon to download and install it with

```
sudo dpkg -i FrostWire-4.10.9-2.i586.deb
```

---

### Post by hodad on 2006-10-07
Thanks, I'll give it a try.  However, I don't know if it'll work with the MP3 download website (?!).

---

### Post by hodad on 2006-10-07
I installed FrostWire, but it doesn't do anything as far as I can tell.  I get a FrostWire icon, and when I click it, it say's "Package Installer - Frostwire" with a choice button "Reinstall Package".   After clicking around for a while, a folder showed up on the desktop called FrostWire-4.9.10-2.i586.deb_FILES.  I assume that this has to be decompressed somehow, but I'm afraid to do anything now that I've gotten so far with this house of cards.  Any advice how to proceed?  
THanks again.

---

### Post by taurus on 2006-10-07
Open a terminal and run it from the prompt to see exactly what the error message is, Applications -> Accessories -> Terminal.

```
frostwire
```

---

### Post by hodad on 2006-10-07
Here's what I get:

dave@dave-desktop:~$ frostwire
Starting FrostWire...
Java exec found in PATH. Verifying...
OOPS, you don't seem to have a valid JRE. FrostWire works best with Sun JRE available at [http://www.java.com](http://www.java.com)
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)
ls: /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)
ls: /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)
dave@dave-desktop:~$


I installed jre-1_5_0_09-linux-amd64.bin in the usr/lib/frostwire directory (as I was told when reading notes on installing frostwire), but don't know if this is the right file.

---

