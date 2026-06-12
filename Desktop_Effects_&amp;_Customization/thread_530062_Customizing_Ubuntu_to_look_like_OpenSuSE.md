---
title: "Customizing Ubuntu to look like OpenSuSE"
date: 2007-08-20
forum: Desktop Effects &amp; Customization
---

### Post by subzero1266 on 2007-08-20
Hi everyone,
 First things first - I like Ubuntu's stability, security and of course the community so much that I stopped using OpenSuSE. 

The only thing that I liked about OpenSuSE is that it had gr8 looks. So, what I want to do is to customize/replace Ubuntu's - Grub splash, Bootsplash & GDM splash screens with that of OpenSuSe's. 

(Few months back, a guy from neowin customization provided me a link to suse or opensuse rpm packages link from where I was able to extract Gilouche GTK theme. I don't have the link but I still have the theme. So, I am wondering that if there are any links to the original packages from where I would be able to extract opensuse's grub, bootsplash and gdm images. Is it legal to do such a thing?)

So, is this project possible at all by any chance? Any inputs and help is highly appreciated. 

Thank You.

---

### Post by Lars Ketil on 2007-08-20
Have you searched Gnome-look.org ??

---

### Post by kerry_s on 2007-08-20
> **subzero1266 said:**
> Hi everyone,
 First things first - I like Ubuntu's stability, security and of course the community so much that I stopped using OpenSuSE. 

The only thing that I liked about OpenSuSE is that it had gr8 looks. So, what I want to do is to customize/replace Ubuntu's - Grub splash, Bootsplash & GDM splash screens with that of OpenSuSe's. 

(Few months back, a guy from neowin customization provided me a link to suse or opensuse rpm packages link from where I was able to extract Gilouche GTK theme. I don't have the link but I still have the theme. So, I am wondering that if there are any links to the original packages from where I would be able to extract opensuse's grub, bootsplash and gdm images. Is it legal to do such a thing?)

So, is this project possible at all by any chance? Any inputs and help is highly appreciated. 

Thank You.


do you think you can find the link to the rpm's again?
if so you can try using alien to convert them to debs and install them in ubuntu, it's as simple as->

sudo apt-get install alien
alien name_of.rpm
sudo dpkg -i name_of.deb

---

### Post by subzero1266 on 2007-08-20
[quote=Lars Ketil]Have you searched Gnome-look.org ??[/quote]
Hi Lars,
 Yes, I searched at gnome-look, kde-look.

[quote=kerry_s]do you think you can find the link to the rpm's again?
if so you can try using alien to convert them to debs and install them in ubuntu, it's as simple as->

sudo apt-get install alien
alien name_of.rpm
sudo dpkg -i name_of.deb[/quote]
Hi Kerry,
 Yes, I know alien. Unless I find the right rpm in which bootsplash or others are located, i can't do it.

So, far the progress -

**1. Grub/Gfxboot customization - Done!**
------------------------------------------------------------
I managed to install gfxboot along with suse and sles themes for gfxboot (available at repos). Then apply suse message as the one to be booted.

Help taken from [this thread]("http://ubuntuforums.org/showthread.php?t=208855")

**2. BootSplash customization - I don't know how to do this yet**
-----------------------------------------------------------------------------------------------
I read guide - ["How to bootsplash using Splashy" here]("http://ubuntuforums.org/showthread.php?t=41709").

Splashy looked interesting but after following the guide, I stil got the default bootsplash. Later, I found that Splashy doesn't work on Feisty Fawn because Fesity doesn't have /etc/inittab. There is USplash but that doesn't support any image more than 256 colors. 

On google-ing, I found a hardway (or outdated way??) to patch the kernel using openSuSE's bootsplash and recompiling it. Gentoo user had done it [here]("http://forums.gentoo.org/viewtopic.php?t=26494").

Any ideas??

Screenshot and the link to openSuSE bootsplash is [here]("http://en.opensuse.org/Branding_Overview:os10.3:Bootsplash").
[B]
3. GDM customization - done![/B]
---------------------------------------------
I got openSuSE 10.3's GDM files [here]("https://forgesvn1.novell.com/svn/opensuse-art/trunk/login/").

I gzipped them and installed using LoginWindow and it works perfectly!

But, I wonder if it is possible to show existing users in the login screen as shown in the first screenshot [here]("http://en.opensuse.org/Branding_Overview:os10.3:GDM"). The theme that I applied looks like the one in the second screenshot of the page.

**4. Gnome Splash customization - done!**
-----------------------------------------------------------
I got the gnome splash screen from the same site and added it in splash screen manager.
[B]
5. Gnome customization - done![/B]
-------------------------------------------------
Gilouche GTK + metacity + Emerald theme is the one.

---

