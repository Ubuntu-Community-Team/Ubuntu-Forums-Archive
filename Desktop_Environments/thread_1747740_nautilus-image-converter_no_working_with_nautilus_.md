---
title: "nautilus-image-converter no working with nautilus 3"
date: 2011-05-03
forum: Desktop Environments
---

### Post by opodaniel on 2011-05-03
Hello
I just installed Gnome 3 ( which I found quite nice ) that came with Nautilus 3. One of the problems is that the plug-in nautilus-image-converter is no longer working with the new Nautilus.  What can be done about this, is there a workarround? :confused:

---

### Post by steelsteel! on 2011-05-30
> **opodaniel said:**
> Hello
I just installed Gnome 3 ( which I found quite nice ) that came with Nautilus 3. One of the problems is that the plug-in nautilus-image-converter is no longer working with the new Nautilus.  What can be done about this, is there a workarround? :confused:

same problem here.

---

### Post by emelce on 2011-07-04
same problem ;-(

---

### Post by omne on 2011-07-24
Same here :( Please help… I’ve tried to wrote to the autors few month ago with no result :(

---

### Post by aeronutt on 2011-07-25
Ditto, would love to find a solution for this!

---

### Post by glococo on 2011-07-31
Same issue. What a nightmare is to resize a bunch of images without NAUTILUS-IMAGE-CONVERTER.

Please, try someone fix it ! :KS

---

### Post by coffeecat on 2011-07-31
As far as I can find out, nautilus-image-converter hasn't been updated since 2007, so it looks as though the original devs have lost interest. Unless someone else picks this up, this is going to die with gnome 3.

All is not lost, though. There are other ways of doing batch resize jobs on images. Try Gthumb - it's in the repos. It can batch resize and rename, but not both together (unless I'm missing something), so it's a 2-stage process to batch resize and rename some images.

---

### Post by opodaniel on 2011-07-31
I changed back to Gnome 2 ...  I use it quite often, and don't want to start my virtual Windows XP each time I need to resize my photos.

---

### Post by omne on 2011-08-01
> **coffeecat said:**
> As far as I can find out, nautilus-image-converter hasn't been updated since 2007, so it looks as though the original devs have lost interest. Unless someone else picks this up, this is going to die with gnome 3.

Is-it so hard to port it from gnome2 to gnome3 ?

Where can we ask for this ?

---

### Post by ulm05 on 2011-09-05
I work with ubuntu 11.04 (Natty Narwhal) and gnome 3.
I had the same problem with this quite usefull nautilus plugin. :cry:
My solution, maybe not the nicest one but easy and it works, is :

Download the fedora 15 rpm :
[http://rpm.pbone.net/index.php3/stat/4/idpl/15920600/dir/fedora_15/com/nautilus-image-converter-0.3.1-0.1.git430afce31.fc15.x86_64.rpm.html](http://rpm.pbone.net/index.php3/stat/4/idpl/15920600/dir/fedora_15/com/nautilus-image-converter-0.3.1-0.1.git430afce31.fc15.x86_64.rpm.html)

Install the deb packagage "alien" that is already present in ubuntu main repository (this package converts between Red Hat rpm, Debian deb, Stampede slp, Slackware tgz, and Solaris pkg file formats).

Go in the directory where you downloaded nautilus-image-converter and type :
sudo alien -d nautilus-image-converter-.3.1-0.1.git430afce31.fc15.x86_64.rpm
This will generate a deb package named "nautilus-image-converter_0.3.1-1.1_amd64.deb".

Now, just install it with a dpkg -i nautilus-image-converter_0.3.1-1.1_amd64.deb, close all instances of nautilus and restart it.

There you are, you now should have a right menu called something like "image resize" !!! :)

---

### Post by aeronutt on 2011-09-06
> **ulm05 said:**
> I work with ubuntu 11.04 (Natty Narwhal) and gnome 3.
I had the same problem with this quite usefull nautilus plugin. :cry:
My solution, maybe not the nicest one but easy and it works, is :

Download the fedora 15 rpm :
[http://rpm.pbone.net/index.php3/stat/4/idpl/15920600/dir/fedora_15/com/nautilus-image-converter-0.3.1-0.1.git430afce31.fc15.x86_64.rpm.html](http://rpm.pbone.net/index.php3/stat/4/idpl/15920600/dir/fedora_15/com/nautilus-image-converter-0.3.1-0.1.git430afce31.fc15.x86_64.rpm.html)

Install the deb packagage "alien" that is already present in ubuntu main repository (this package converts between Red Hat rpm, Debian deb, Stampede slp, Slackware tgz, and Solaris pkg file formats).

Go in the directory where you downloaded nautilus-image-converter and type :
sudo alien -d nautilus-image-converter-.3.1-0.1.git430afce31.fc15.x86_64.rpm
This will generate a deb package named "nautilus-image-converter_0.3.1-1.1_amd64.deb".

Now, just install it with a dpkg -i nautilus-image-converter_0.3.1-1.1_amd64.deb, close all instances of nautilus and restart it.

There you are, you now should have a right menu called something like "image resize" !!! :)

Dang, I had hopes...but nope. This didn't work for me.

---

### Post by aeronutt on 2011-12-24
FYI, I found 'nautilus-image-manipulator' in the repositories recently. Seems to work like nautilus-image-converter used to, but is being supported.

---

### Post by Jorell00 on 2012-01-13
Thanks aeronutt, I've spent hours trying to get nautilus image converter to work. You saved me loads more hours- Good find

---

### Post by bcarlowise on 2012-01-13
I sometimes use gThumb for mass resizing (if less than say 20 files) and renaming but it is not as useful as just running irfanview (requires Wine). The thing I like about irfanview is that you can set what size you want to long side of any image to be and all images regardless of portrait or landscape orientation will have those dimensions (i.e. 1024x768 for landscape and 768x1024 for portrait). gThumb is that flexible so you can only resize images with the same orientation at once.

---

