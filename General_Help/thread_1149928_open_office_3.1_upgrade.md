---
title: "open office 3.1 upgrade"
date: 2009-05-05
forum: General Help
---

### Post by KegHead on 2009-05-05
Hi!

I am using calc and writer only 3.0.

I'd like to upgrade to 3.10 only for these packages.

Any ideas for the fastest and easiest way?

Thanks in advance.

KegHead

---

### Post by slumbergod on 2009-05-05
I'm interested too. I am sure that the updated version won't be added to the official repos and I don't want to download a separate installer because I don't want two installations. 

Maybe the built-in update feature will work? Or perhaps someone knows of a PPA with the latest version.

---

### Post by timmans on 2009-05-05
I downloaded OOo_3.1.0_LinuxIntel_install_en-US_deb.tar.gz and ran the following commands after unpacking:

sudo dpkg -i ~/Desktop/OOO310_m11_native_packed-4_en-US.9399/DEBS/*.deb
sudo dpkg -i ~/Desktop/OOO310_m11_native_packed-4_en-US.9399/DEBS/desktop-integration/*.deb

The only problem I had after upgrading was OpenOffice kept crashing when trying to open Spreadsheet. Not sure if was just an issue with my installation.

---

### Post by tubegeek on 2009-05-07
Thanks, timmans, that was a big help. I dl'ed the archive but I didn't know the dpkg command.

---

### Post by cmost on 2009-05-07
Just right-click on the tarball and select 'extract here'.  There's no need to drop to the command line.

---

### Post by nilarimogard on 2009-05-07
There is also a repository for this: [http://webupd8.blogspot.com/2009/05/install-openoffice-31-in-ubuntu-jaunty.html](http://webupd8.blogspot.com/2009/05/install-openoffice-31-in-ubuntu-jaunty.html)

---

### Post by frank83 on 2009-05-07
@timmans: 
Here it didnt crash any more after i deleted the .openoffice.org folder in my home directory

---

