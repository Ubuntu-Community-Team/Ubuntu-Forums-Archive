---
title: "Can No Longer Update or Install"
date: 2005-12-13
forum: Desktop Environments
---

### Post by sfdfireman on 2005-12-13
After using all the various desktop installers and the updater several times, I find I can no longer update or install.  No error message, the packages are caching, but they don't update or install.

I tried installing from the command line using apt-get and find the same problem, but do get an error message after the files are fetched:

Preconfiguring packages ...
Could not exec dpkg!
E: Sub-process /usr/bin/dpkg returned an error code (100)

I've read man pages and googled for days, but can't find anything of use.  Any suggestions?  Thanks!

---

### Post by ranf on 2005-12-13
[QUOTE=sfdfireman]
Preconfiguring packages ...
Could not exec dpkg!
E: Sub-process /usr/bin/dpkg returned an error code (100)
[/QUOTE]
Can you run dpkg?
```
dpkg --help
```

---

### Post by sfdfireman on 2005-12-13
[QUOTE=ranf]Can you run dpkg?
[/QUOTE]

Can't seem to run dpkg either.

```

dpkg --help
bash: /usr/bin/dpkg: Permission denied

sudo dpkg --help
Password:
sudo: dpkg: command not found

```

---

### Post by ranf on 2005-12-13
[QUOTE=sfdfireman]Can't seem to run dpkg either.

```

dpkg --help
bash: /usr/bin/dpkg: Permission denied

sudo dpkg --help
Password:
sudo: dpkg: command not found

```[/QUOTE]
That looks like dpkg is broken somehow.
Do you have your install CD handy?

Edit: we can unpack it by hand.

---

### Post by leech on 2005-12-13
[http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fd%2Fdpkg%2Fdpkg_1.13.10ubuntu4_i386.deb&md5sum=11731d6ce959095d48292083d5645c58&arch=i386&type=main](http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fd%2Fdpkg%2Fdpkg_1.13.10ubuntu4_i386.deb&md5sum=11731d6ce959095d48292083d5645c58&arch=i386&type=main)

Go there, Download the package from a mirror.  Open it with the archive manager, (you can right click on it under Nautilus) and then just extract it to a temporary directory.  Then you should be able to go into that directory in a terminal and do 'sudo cp -r * /' and you should have dpkg re-installed.

That's got to be one of the worse things that you could have happen.  After doing this, I would do a 'dpkg -l|grep dpkg' to make sure that dpkg is actually installed, and if it isn't, then 'sudo dpkg -i <dpkg package name>'

Hope this fixes your problem, good luck.

Leech

---

### Post by sfdfireman on 2005-12-13
downloaded the .deb from the pointers, thanks Leech.  (Should I have found a tar instead?)

Archive Manager gave me this:
```

Could not open "dpkg_1.13.10ubuntu4_i386.deb"

Archive type not supported.

```

Ugh!  I have my install CD handy, how does one unpack it by hand?

Just curious, how could I have broken dpkg from the GUI, anyway?

---

### Post by Sokraates on 2005-12-14
[QUOTE=sfdfireman]downloaded the .deb from the pointers, thanks Leech.  (Should I have found a tar instead?)

Archive Manager gave me this:
```

Could not open "dpkg_1.13.10ubuntu4_i386.deb"

Archive type not supported.

```

Ugh!  I have my install CD handy, how does one unpack it by hand, anyway?

Just curious, how could I have broken dpkg from the GUI, anyway?[/QUOTE]

Right, you need a tarball. debs are opened with dpkg. ;) 

Go [here](http://archive.ubuntu.com/ubuntu/pool/main/d/dpkg/) and select the latest version. Don't know if your running on x86 or x64.

---

### Post by ranf on 2005-12-14
[QUOTE=sfdfireman]
Ugh!  I have my install CD handy, how does one unpack it by hand, anyway?
[/QUOTE]
First see if you have `ar' installed:
```
ar --help
```

If not then try if `dpkg-deb' is ok:
```
dpkg-deb --help
```

---

### Post by sfdfireman on 2005-12-14
Many thanks to you guys for the continuing help!
With your assistance, I'll fix this problem, learn a great deal about the system and enjoy the process.  :) 
```

ar --help
bash: ar: command not found

```


"dpgk-deb --help" brings up the help properly
```

dpkg-deb --help
Command:
  -b|--build <directory> [<deb>]    build an archive.
  -c|--contents <deb>               list contents.
  ...
<snip>
  ...
Use `dpkg' to install and remove packages from your system, or
`dselect' or `aptitude' for user-friendly package management.  Packages
unpacked using `dpkg-deb --extract' will be incorrectly installed !

```

So, it seems ar is not installed, but dpkg-deb is there.  Rather than reinstalling dpkg using dpkg-deb, would it be better for me to reinstall dpkg from source?  Am I likely to break anything reinstalling dpkg?

Thanks again for all the help.

---

### Post by ranf on 2005-12-14
[QUOTE=sfdfireman]
So, it seems ar is not installed, but dpkg-deb is there.  
[/QUOTE]
Ok we do it with dpkg-deb then:
```

mkdir dpkg
cd dpkg
cp ~/Desktop/dpkg<Tab>
dpkg-deb --extract dpkg<Tab>
cd usr/bin
sudo cp dpkg /usr/bin

```
[QUOTE=sfdfireman]Rather than reinstalling dpkg using dpkg-deb, would it be better for me to reinstall dpkg from source?  Am I likely to break anything reinstalling dpkg?
[/QUOTE]
I guess you don't have the build-essential package installed. And because of a broken dpkg you can't install it.

---

