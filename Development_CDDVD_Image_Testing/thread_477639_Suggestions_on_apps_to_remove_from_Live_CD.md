---
title: "Suggestions on apps to remove from Live CD"
date: 2007-06-18
forum: Development CD/DVD Image Testing
---

### Post by inanutshellus on 2007-06-18
I'm making a custom Live Cd to which I've added several large apps. Now I need to remove others to make the ISO fit back on a CD. I've removed several larger apps, but I don't want to completely strip down the live cd. 

The idea is to make a cd that my fellow software engineers here at work can boot into and see what it's like in the linux world. With that in mind, I've installed the apps they would need in order to be productive immediately as a programmer, but I'm also hoping to keep as many bells and whistles as I can so the experience doesn't lose its "oo, ahh.." factor, and look for more sub-surface apps and libraries to uninstall that aren't likely to be used.

Problem is, I'm still a relative linux noob myself and am having trouble coming up with things to remove.

The only thing I'd really consider an accomplishment of that goal (getting something for nothing) so far is removing the alternate language packs. Which got rid of about 30MB, IIRC. Not too shabby, but the tip of the iceberg, really.

Are there other libraries or utilities you guys can think of to remove that fit the "something for nothing" criteria? If I can't come up with enough of them, I'll start removing more of the "fluff" apps that come on the live cd, certainly, but I thought I'd ask you guys first.

---

### Post by smartboyathome on 2007-06-18
I would suggest replacing OpenOffice with Abiword and Gnumeric. Also, try substituting some Gnome stuff for XFCE stuff (ie, games, tools, etc). This will gain you a lot of space because XFCE programs are lighter than Gnome programs.

---

### Post by nirelan on 2007-06-18
I think you could safely remove the photo editing stuff like Gimp.

I would suggest putting Wine on the CD if you plan to show this to Windows developers though.

---

### Post by P_Badger on 2007-06-18
Yeah, removing the open office suite would give you a ton of space, and removing Gimp might be best for you, too. Both are good apps to show off with, though, so it really depends what you want to wow them with.

---

### Post by inanutshellus on 2007-06-19
It looks like I may have added too much to the CD. Eclipse (200MB), Java SDK (150MB), Oracle instant client (100MB), and even several more things on top of that (that aren't really that large, like Tomcat at 15MB, but it adds up)!

It looks like I'll be doing some serious slashing. Blarg. Perhaps starting with a more light-weight distro would be a better route.

---

### Post by inanutshellus on 2007-06-20
Ooooo... Just found [http://cdimage.ubuntu.com/](http://cdimage.ubuntu.com/), which contains ISOs for the Ubuntu Live DVD... 

Now I just need enough hard drive space ;-)

I wonder if UCK has been tested with the DVD ISO...

---

### Post by smartboyathome on 2007-06-20
> **inanutshellus said:**
> Ooooo... Just found [http://cdimage.ubuntu.com/](http://cdimage.ubuntu.com/), which contains ISOs for the Ubuntu Live DVD... 

Now I just need enough hard drive space ;-)

I wonder if UCK has been tested with the DVD ISO...

UCK should work with the DVD ISO. It is built in a similar way to the CD ISO, except with more packages. ;) I would probably not use it though, as it would probably have everything I need and then some. :p

---

### Post by inanutshellus on 2007-06-20
Oh. Heh. Ehh.. Actually, I found the manifest files for the [live cd]("http://releases.ubuntu.com/7.04/ubuntu-7.04-desktop-i386.manifest") and compared them to the [live dvd]("http://cdimage.ubuntu.com/releases/7.04/release/ubuntu-7.04-dvd-i386.manifest") manifest and... they're the same. 

So I guess the dvd is just an uncompressed version of the cd? doesn't seem right though since the cd expands into 2.2g and the dvd is 4 gigs. hm... weird.

---

### Post by smartboyathome on 2007-06-20
> **inanutshellus said:**
> Oh. Heh. Ehh.. Actually, I found the manifest files for the [live cd]("http://releases.ubuntu.com/7.04/ubuntu-7.04-desktop-i386.manifest") and compared them to the [live dvd]("http://cdimage.ubuntu.com/releases/7.04/release/ubuntu-7.04-dvd-i386.manifest") manifest and... they're the same. 

So I guess the dvd is just an uncompressed version of the cd? doesn't seem right though since the cd expands into 2.2g and the dvd is 4 gigs. hm... weird.

The DVD has extra software, themes, etc. that the CD doesn't have because of space. That is the only difference.

---

### Post by inanutshellus on 2007-06-20
> **smartboyathome said:**
> The DVD has extra software, themes, etc. that the CD doesn't have because of space. That is the only difference.

But wouldn't that extra software be in the manifest? 

Hm. Ah, well I found this post elsewhere on the forums:

> **aysiu said:**
> The DVD has everything in the main and restricted repositories--that means it includes Xubuntu, Ubuntu, Kubuntu, and Edubuntu.

The CDs have only one desktop environment each (Xubuntu with XFCE, Kubuntu with KDE, or Ubuntu with Gnome).

**EDIT**: I was able to get the DVD to boot on my laptop so I thought I'd give an update. At least from the boot menu there doesn't seem to be Xubuntu or Kubuntu on the DVD. The boot menu though has several extra options, including: 

text-based install
text-based install for manufacturers
install a server

If you boot into the Ubuntu desktop from the DVD menu it's exactly the same as the CD. Same themes, same software packages, etc.

---

### Post by inanutshellus on 2007-06-20
Well. I guess I won't find out anyway. The live DVD dies on boot saying "kernel panic. No init found." And really, how can you argue with a readonly file system? ;)

Back to the CD!

*grr*

---

