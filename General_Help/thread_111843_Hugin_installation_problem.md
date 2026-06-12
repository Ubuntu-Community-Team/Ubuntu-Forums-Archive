---
title: "Hugin installation problem"
date: 2006-01-03
forum: General Help
---

### Post by cotcot on 2006-01-03
Installing hugin (0.5-1) seems problematic.
It asks for libwxgtk2.4.3 which is not available in the Breezy repositories. I found the debian package for this and installed it with dpkg.
I then tried to install hugin 0.5-1 (debian package) also with dpkg. This asks for libwxgtk2.4.3-contrib. I cannot find this package neither on the Ubuntu repositories (Dapper included), nor on other formats (deb, rpm).
On the web site of hugin it is advised for debian users to install libwxgtk-2.6, but this does not work either. I stopped installing hugin in Ubuntu and have it running on FC4 (I installed FC4 on another partition) and XP.
Has anyone installed hugin 0.5-1 successfully in Ubuntu ? If yes , how ?

Thanks

---

### Post by shakespeare on 2006-04-22
Deb packages for both libwxgtk2.4-2.4.3.1 and libwxgtk2.4-contrib-2.4.3.1 are listed at packages.debian.org, with links to many download sites. I was able to install hugin 0.5 after installing these. I also installed libpano12 and libpano12-bin using apt-get.

[http://packages.debian.org/stable/libs/libwxgtk2.4](http://packages.debian.org/stable/libs/libwxgtk2.4)
[http://packages.debian.org/stable/libs/libwxgtk2.4-contrib](http://packages.debian.org/stable/libs/libwxgtk2.4-contrib)

- John.

---

### Post by cotcot on 2006-06-03
[QUOTE=shakespeare]Deb packages for both libwxgtk2.4-2.4.3.1 and libwxgtk2.4-contrib-2.4.3.1 are listed at packages.debian.org, with links to many download sites. I was able to install hugin 0.5 after installing these. I also installed libpano12 and libpano12-bin using apt-get.

[http://packages.debian.org/stable/libs/libwxgtk2.4](http://packages.debian.org/stable/libs/libwxgtk2.4)
[http://packages.debian.org/stable/libs/libwxgtk2.4-contrib](http://packages.debian.org/stable/libs/libwxgtk2.4-contrib)

- John.[/QUOTE]

Are you able to run autopano-sift (automatic overlap point selection) and PTStitcher ?
I also have installed hugin but cannot use PTStitcher; i have to use nona but that is not as good as PTStitcher. Meanwhile I installed Gentoo where I got everything working well in a short time.

---

### Post by quik77 on 2006-06-05
I have a slightly different problem I installed all the dependencys through synaptic or apt-get... and tried to install hugin from the .deb file which fails to find libpano12 and libpano12-bin which according to synaptic are installed already

---

### Post by dyssident on 2006-06-14
which deb are you installing? if you are getting it from someones personal site the package may just not be put together correctly.

the packages at debian-multimedia.org (linked from hugins site) worked for me. 

```
sudo echo 'deb http://www.debian-multimedia.org unstable main' >> /etc/apt/sources.list
sudo apt-get update
sudo apt-get install --reinstall hugin
```

---

### Post by chinaski on 2006-08-01
> **dyssident said:**
> which deb are you installing? if you are getting it from someones personal site the package may just not be put together correctly.

the packages at debian-multimedia.org (linked from hugins site) worked for me. 

```
sudo echo 'deb http://www.debian-multimedia.org unstable main' >> /etc/apt/sources.list
sudo apt-get update
sudo apt-get install --reinstall hugin
```

```
shaitan@mobile:~$ sudo apt-get install --reinstall hugin
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  hugin: Depends: libatk1.0-0 (>= 1.12.1) but 1.11.4-0ubuntu1 is to be installed
         Depends: libc6 (>= 2.3.6-6) but 2.3.6-0ubuntu20 is to be installed
         Depends: libcairo2 (>= 1.2.0) but 1.0.4-0ubuntu1 is to be installed
         Depends: libfreetype6 (>= 2.2) but 2.1.10-1ubuntu2.2 is to be installed
         Depends: libgcc1 (>= 1:4.1.0) but 1:4.0.3-1ubuntu5 is to be installed
         Depends: libstdc++6 (>= 4.1.0) but 4.0.3-1ubuntu5 is to be installed
         Depends: libwxbase2.6-0 (>= 2.6.3.2.1.1) but it is not installable
         Depends: libwxgtk2.6-0 (>= 2.6.3.2.1.1) but it is not going to be insta lled
E: Broken packages

```
I'm stuck here... any ideas?

---

### Post by remi71 on 2006-08-22
Hi All!

This work for me in Dapper:

1. Download Hugin for Debian:

   wget [http://itp.tugraz.at/Comp/debian/dists/sarge/desktop/binary-i386/hugin_0.5-2_i386.deb](http://itp.tugraz.at/Comp/debian/dists/sarge/desktop/binary-i386/hugin_0.5-2_i386.deb)


2. Download libpano12 (Do NOT use this from ubuntu repository!):
   
   wget [http://itp.tugraz.at/Comp/debian/dists/sarge/desktop/binary-i386/libpano12_2.8.1-1_i386.deb](http://itp.tugraz.at/Comp/debian/dists/sarge/desktop/binary-i386/libpano12_2.8.1-1_i386.deb)


3. Download libwxgtk2.4 and libwxgtk2.4-contrib (Do NOT use this from ubuntu repository!):

    wget [http://ftp.us.debian.org/debian/pool/main/w/wxwindows2.4/libwxgtk2.4_2.4.3.1_i386.deb](http://ftp.us.debian.org/debian/pool/main/w/wxwindows2.4/libwxgtk2.4_2.4.3.1_i386.deb)
    wget [http://ftp.us.debian.org/debian/pool/main/w/wxwindows2.4/libwxgtk2.4-contrib_2.4.3.1_i386.deb](http://ftp.us.debian.org/debian/pool/main/w/wxwindows2.4/libwxgtk2.4-contrib_2.4.3.1_i386.deb)


4. Install downloaded packages:

    dpkg -i libpano12_2.8.1-1_i386.deb
    dpkg -i libwxgtk2.4_2.4.3.1_i386.deb
    dpkg -i libwxgtk2.4-contrib_2.4.3.1_i386.deb
    dpkg -i hugin_0.5-2_i386.deb

No more dependency problem!;)

---

### Post by cotcot on 2007-04-30
I could install hugin as described in [ [COLOR="RoyalBlue"]**this**[/COLOR]]("http://doc.gwos.org/index.php/Install_Hugin_Panoramic_Tools_and_Enblend") howto.
I am using PTmender (that comes with libpano12) instead of PTStitcher and it works fine. 
(PTStitcher does not work). PTmender is the upcoming opensource alternative for PTStitcher.
I do the correction for colour and brightness separately in terminal with enblend because PTMender is to be used with multiple tiff and nano does not do corrections for colour and brightness. It is possible to produce multiple tiff and use enblend as well.
The enblend command is : ```
enblend -o filename_for_panorama.tif foto0000.tif foto0001.tif ....
```
The "..." is for adding more tif if your panorama is made with more than two photos.

---

