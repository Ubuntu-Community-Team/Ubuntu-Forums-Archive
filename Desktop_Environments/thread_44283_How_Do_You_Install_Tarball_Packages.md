---
title: "How Do You Install Tarball Packages?"
date: 2005-06-25
forum: Desktop Environments
---

### Post by tstrickland on 2005-06-25
As a newbie, I learned yesterday how to install programs using kynoptic/synaptic. However, I've found some mathematics programs that I'd  like to install that aren't available in kynoptic/synaptic (at least, I can't find them).  :-?   I've downloaded their tarballs, but that's as far as I can go. These packages are:

it++3.8.1.tar.gz
mcsim-v.5.0.0.tar.gz
numexp-core-0.10.0a2.tar.gz
octave-2.1.71.tar.gz

I'd appreciate any help you can give. 

Thank you.

---

### Post by Leif on 2005-06-25
The usual procedure is to extract the package ("tar xzf pack_name"), then cd to the source directory ("cd pack_name/src") where you just unzipped to, then "./configure", "./make", "./make-install". This can be different, so you should read the instructions given with the package, usually in a file called README or INSTALL when extracted.

---

### Post by spookylukey on 2005-06-25
First, I think some of those packages are available in 'universe' or 'multiverse'. I can find octave anyway.  (To use 'universe', you need to edit your /etc/apt/sources.list, either manually using an editor, which you'll have to launch as root user to edit that file, or using the synaptic frontend in 'Settings/Repositories').

That will get you octave, but not the others.

The second thing you should do is look for a .deb file instead of the tarball, which you can then install using dpkg.
For numexp-core, for example, see 
[http://sourceforge.net/project/showfiles.php?group_id=333&package_id=42494](http://sourceforge.net/project/showfiles.php?group_id=333&package_id=42494)
and you notice a .deb.  You probably want the i386, unless you are running AMD64 Ubuntu.
Also, look here:
[http://numexp.sourceforge.net/downs.html](http://numexp.sourceforge.net/downs.html)

If these fail, you'll need to extract the tarball and build from source.  This will require using a console/terminal and some command line skill, and as I can't cover everything you should really google for more information (keywords to search for include Linux, shell, beginners, bash).  To get you going:

tar -xvzf it++3.8.1.tar.gz

will extract the first tarball for you.

Then read the instructions in 'INSTALL' and 'README' in the resulting directory.

---

### Post by wdso on 2005-06-25
If you can't find the package you are looking for (make sure to check universe and backports), another option is to *create* a package. Check out "checkinstall". You execute it instead of "make install".

---

### Post by manicka on 2005-06-25
After extracting the package I always run these commands in the extracted folder

./configure
make
sudo checkinstall

checkinstall is a superior option to make install because it will install the tarball as a deb package, make  copy of the package  and is easily removed later through apt or synaptic.

normally to remove a package you have to use "make clean" within the folder you used to prepare the tarball. I've often struck problems with 'make clean' not removing everything properly.

You'll need to install checkinstall first.  

good luck

---

### Post by Firetech on 2005-06-25
[QUOTE=manicka]
normally to remove a package you have to use "make clean" within the folder you used to prepare the tarball. I've often struck problems with 'make clean' not removing everything properly.
[/QUOTE]

"make clean" is in most cases ("business" standard) the command to remove compiled binaries from the source directory. Tu uninstall a package that wasn't installed with checkinstall the "business" standard is "make uninstall". Not all packages come with an uninstall feature though, so I would recommend checkinstall if you're not sure of what you are doing, it is much easier to start learning with.

---

### Post by wdso on 2005-06-25
.. but don't forget, checkinstall is nothing more than a handy hack. Always prefer packages from Ubuntu (via apt-get).

---

