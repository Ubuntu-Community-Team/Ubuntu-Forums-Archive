---
title: "Roccat keyboard, Mouse and PPA's"
date: 2013-09-14
forum: Gaming &amp; Leisure
---

### Post by UltimateCat on 2013-09-14
Hi: Everyone;)

I **_ended up_** installing the ppa's (roccat-kmod-dkms &                  roccat-tools)                for this new Roccat Isku keyboard and Kone XTD mouse using the Ubuntu Software Center.  

Only problem is, the files are showing up in my Dash Home.  When I click on the roccat icon's in Dash Home, they don't launch a GUI application or anything else that I can see or notice. 

I don't understand, how do I access the application so that it will allow me to manipulate the keyboard and mouse settings etc? 

[https://launchpad.net/~berfenger/+archive/roccat](https://launchpad.net/~berfenger/+archive/roccat)

There are multiple pages at this site, (see directly above) but I don't understand how to make this application work at all, this is a confusing mess.:(

Here is the keyboard page on the site, (see below) I tried several times to untar and install the tarbz. and cmake went well but I still could not install it that way in the end and as stated above finally used the Ubuntu Software Center. 

Still it does not work.

[http://sourceforge.net/projects/roccat/?source=directory](http://sourceforge.net/projects/roccat/?source=directory)
[http://roccat.sourceforge.net/general.html#id359618](http://roccat.sourceforge.net/general.html#id359618)
[http://roccat.sourceforge.net/kone.html#kone_basic_setup](http://roccat.sourceforge.net/kone.html#kone_basic_setup)

Is the tar ball on that page the only way to get that application to control the mouse and keyboard?  If so why doesn't the Ubuntu Software Center allow it to be installed?

I had a horrible time trying to install that tar.bz2 with no success in the long run.
```

 mkdir build
  $ cd build
  $ cmake -DCMAKE_INSTALL_PREFIX="/usr" ..
  $ make
  $ sudo make install

I tried this but it did not work--

```

```

root@sifu-MS-7845:/home/sifu/Downloads# mkdir build
root@sifu-MS-7845:/home/sifu/Downloads# cd build
root@sifu-MS-7845:/home/sifu/Downloads/build# cmake -DCMAKE_INSTALL_PREFIX="/usr"
CMake Error: The source directory "/home/sifu/Downloads/build" does not appear to contain CMakeLists.txt.
Specify --help for usage, or press the help button on the CMake GUI.
root@sifu-MS-7845:/home/sifu/Downloads/build# make
make: *** No targets specified and no makefile found.  Stop.
root@sifu-MS-7845:/home/sifu/Downloads/build# sudo make install
make: *** No rule to make target `install'.  Stop.
root@sifu-MS-7845:/home/sifu/Downloads/build#

```

Someone please explain. Help!

---

### Post by UltimateCat on 2013-09-17
I found the developer(Stefan Achatz) @Sourceforge that made the drivers for this Roccat keyboard and mouse: Thank God!
I had been going in circles for about 2 weeks trying to figure this hardware out--
[http://www.kernelhub.org/?p=7&dev=9326&mbox_type=2](http://www.kernelhub.org/?p=7&dev=9326&mbox_type=2)

Upon installing the roccat-tools and the                 roccat-kmod-dkmsI had all of the Roccat Icons but they wouldn't launch no matter what I did-
[https://launchpad.net/~berfenger/+archive/roccat](https://launchpad.net/~berfenger/+archive/roccat)

The developer explained that this cmd has to be issued in order for the 'permission denied' to halt-
```
sudo usermod -a -G roccat $USER

```
And upon doing so; log out and log back in- That then gave me full functionality of the Isku Roccat keyboard and the Kone XTD mouse.
These are actually little libraries that show in the Dash Home as a Icon with the descriptions 'Isku config' and 'Konextd config'

Now I just have to figure out if once I save the profile (new settings that I make) if I have to save that file (or) if deleting it will undo the changes?
And if there is a manual for the Roccat merchandise!?

[http://www.roccat.org/Downloads/Manuals/ROCCAT-Kone-XTD/Kone-XTD-QIG-EU.pdf](http://www.roccat.org/Downloads/Manuals/ROCCAT-Kone-XTD/Kone-XTD-QIG-EU.pdf)
[http://www.roccat.org/Downloads/Manuals/ROCCAT-Isku/ROCCAT-Isku_QIG.pdf](http://www.roccat.org/Downloads/Manuals/ROCCAT-Isku/ROCCAT-Isku_QIG.pdf)

All of the video's online for this merchandise is in German--

---

### Post by UltimateCat on 2013-09-17
I never thought that spending a little extra on a gaming keyboard and mouse would create so much pain and aggravation.:( & :mad:-
The whole reason I purchased the Roccat Gaming Merchandise was because the manufacturer built the Linux drivers for the devices.

I returned the Thermaltake Gaming keyboard and mouse because the only OS that seems to recognize it is Windows.
I was not about to put Windows on my brand new computer that I just finished building last week--

Over time I realized that installing from source was not the answer. Just installing the roccat-tools and the roccat-kmod for the kernel was.
Installing a few other packages helped as well but that was not spelled out in the documentation.

I thanked the developer (Stefan Achatz) for his help and time-
[http://www.kernelhub.org/?p=7&dev=9326&mbox_type=2](http://www.kernelhub.org/?p=7&dev=9326&mbox_type=2)

---

