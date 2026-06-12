---
title: "Change kubuntu 9.04 bootloader"
date: 2009-05-09
forum: General Help
---

### Post by LMH1 on 2009-05-09
Hi

I want to change bootloader image.

From some like

[IMG]http://www.dedoimedo.com/images/computers/dual_boot_boot_loader.jpg[/IMG]

with back image:
[IMG]http://www.nobadwords.com/downloads/kubuntu_wallpaper.png[/IMG]

I have tryed to install 
[B]usplash artwork but it dont work.

Please help me..

I like mandriva bootloader image:
[IMG]http://1.bp.blogspot.com/_UqUwVPikChs/SPBpAO9Wd0I/AAAAAAAAFa4/sJ45tytGDmQ/s400/mandriva2.jpg[/IMG]
[/B]

---

### Post by hw-tph on 2009-05-09
How about reading the docs?
[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

---

### Post by LMH1 on 2009-05-14
> **hw-tph said:**
> How about reading the docs?
[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

[quote=GrubHowto]
**Boot splash images**

 
[LIST]
[*]Grub allows an image to be displayed behind the menu. You can obtain a set of images with the package "grub-splashimages", or you can make your own. The images must be 640x480 pixels, contain no more than 16 colors (but a smaller number like 12 works better to allow some different colors for the menu text), and be in gzipped xpm format. The GIMP can be used to resize (Image -> Scale Image...), reduce colors (Image -> Mode -> Indexed...), and can save to .xpm.gz files. 
[/LIST]
 
**Manual configuration**

 After creating a splash image, add a line like splashimage=(hd0,4)/boot/grub/splash.xpm.gzto your menu.lst file.  A useful trick is to make a symlink to the actual image named splash.xpm.gz. cd /boot/grub
sudo ln -s my_image.xpm.gz splash.xpm.gz[/quote]

How can i select a image on bootloader?

---

### Post by PJSingh5000 on 2009-05-18
Note that grub only supports images of 640x480 pixels in size.  Your image must use less than 14 colors, must be in xpm format, and must be gzipped.  The Kubuntu image you attached in this post will need to be converted, or you can look here for some grub boot splash images: [http://www.kde-look.org/index.php?xcontentmode=66](http://www.kde-look.org/index.php?xcontentmode=66)

Once you have your image ready, follow these steps...

(1) Make a copy of menu.lst in case something goes wrong...
```
$ sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.original
```

(2) Edit the menu.list file using a text editor...
KUBUNTU:
```
$ kdesudo kate /boot/grub/menu.lst
```
UBUNTU:
```
$ gksudo gedit /boot/grub/menu.lst
```

(3) In this example the bootloader is located at (hd0,5).  Your's may be different, so be sure to use the correct value.  Also, in this example, the boot image is called splash.xpm.gz.

Add the following lines, adjusting "(hd0, 5)" and "splash.xpm.gz" for your situation.
```
# Appearance
splashimage=(hd0,5)/boot/grub/images/splash.xpm.gz
foreground fffafa
background 4169e1
shade 0
viewport 6 3 76 23
```

Note that you can adjust the view port values to suit your display, after step 5, in case the text is not positioned correctly on your screen after you reboot.  You can also change foreground and background colors to suit your taste.

Change following to give yourself 30 seconds to make a selection, or adjust to your preference.
```
timeout		30
```

Comment-out the following line, if you have not done so already, so that the boot options are displayed.
```
# hiddenmenu
```

Save menu.lst and exit your editor.

(4) Then execute the following to move your splash image to the right location and to set its permissions correctly.  In this example, the boot image is called splash.xpm.gz, and a copy must be placed in your home directory before you execute these commands.
```
$ sudo mkdir /boot/grub/images
$ sudo cp ~/splash.xpm.gz /boot/grub/images
$ sudo chmod -R a+r /boot/grub/images
```

(5) Reboot

---

### Post by LMH1 on 2009-05-24
[quote=PJSingh5000]
Once you have your image ready, follow these steps...

[/quote]

Nice guide.

But please tell me how to show line: (in terminal command)
(hd0,5) 

When i try it, will it not work, maybe usplash artwork deny me to change it?[B]

On reboot/shootdown computer get i:[/B]usplash: can not find /boot/grub/images/splash.xpm.gz images [OK]

---

### Post by PJSingh5000 on 2009-05-26
LMH1,

In step 3, use the following to find out where your boot loader is at...

```
$ sudo grub
$ grub> find /boot/grub/stage1
```

It will give an output like "(hd0,5)".

Then quit grub...
```
$ grub> quit
```

This value should be placed in the following section of menu.lst
```
# Appearance
splashimage=(hd0,5)/boot/grub/images/splash.xpm.gz
foreground fffafa
background 4169e1
shade 0
viewport 6 3 76 23
```


Make sure the permissions are set correctly using
```
$ sudo chmod -R a+r /boot/grub/images
```

If that does not work, you can paste the contents of your menu.lst file and the output of the following command here, and I'll check it over for you.

```
$ ls -Rl /boot/grub
```

---

