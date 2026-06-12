---
title: "Installing and running themes"
date: 2009-03-17
forum: Desktop Environments
---

### Post by pmhauge on 2009-03-17
So I just installed Ubuntu on a Dell 300m I got for free. Runs great. I have compiz running, and everything seems dreamy. I'm wanting to mess around with themes though. I see a lot of people running ubuntu with an OS X like dock, and some other nifty things. The thing is, I can't for the life of me figure out how to install and change the theme, run a dock, etc. Anyone have any links to some how-to pages, or some quick instructions? 

Thanks in advance for any help you can provide!

---

### Post by pmhauge on 2009-03-18
Bump.

---

### Post by bbgman on 2009-03-18
**To change a theme**
[LIST]
[*]right click on an empty space of your desktop,
[*]select 'Change Desktop Background' from the pop-up menu,
[*]select the 'Theme' tab from the 'Appearance Preferences' dialog,
[*]select the theme you want and it will automatically be applied.
[/LIST]

**To install a theme, you need to download it as a zip/tar file**
[LIST]
[*]right click on an empty space of your desktop,
[*]select 'Change Desktop Background' from the pop-up menu,
[*]select the 'Theme' tab from the 'Appearance Preferences' dialog,
[*]click on the 'Install' button,
[*]select the theme zip/tar you downloaded.
[/LIST]

Hope this help.

---

### Post by pmlxuser on 2009-03-19
> **pmhauge said:**
>  I see a lot of people running ubuntu with an OS X like dock, and some other nifty things.  

Thanks in advance for any help you can provide!

```
 
$sudo apt-get install awn-manager

```

more info
[http://awn.wetpaint.com/?t=anon](http://awn.wetpaint.com/?t=anon)
[https://launchpad.net/awn](https://launchpad.net/awn)
wiki.awn-project.org/index.php?title=Main_Page

---

### Post by pmhauge on 2009-03-19
What type of theme am I supposed to download? On gnome-look I'm seeing GDM Themes, Xine Themes, VLC Themes, XMMS, etc. I downloaded one called Hardy-Mariux 2.0.tar, but it will not install by way of the above provided instructions. I'm trying to not look as clueless as I really am, but I'm afraid I can't help it. 

Thanks again.

---

### Post by Kayden on 2009-03-20
> **pmhauge said:**
> What type of theme am I supposed to download? On gnome-look I'm seeing GDM Themes, Xine Themes, VLC Themes, XMMS, etc. I downloaded one called Hardy-Mariux 2.0.tar, but it will not install by way of the above provided instructions. I'm trying to not look as clueless as I really am, but I'm afraid I can't help it. 

Thanks again.
You'll want to use GTK 2 themes. To install, you should just be able to download the tarball and drag it to the Appearance Properties dialog.

Hope this helps.

---

### Post by Skol312000 on 2009-03-20
We cant use all themes that are on gnome-look.org? Why only gdk?

---

### Post by tonyW303 on 2009-03-20
Hi. Okay this is my first post. I feel retarded...> select the theme zip/tar you downloaded.
and
> To install, you should just be able to download the tarball and drag it to the Appearance Properties dialog.

........ When I download a GTK 2.x theme from gnome-look.org, I get it as a .tar.gz. I am relatively new to Ubuntu (back and forth between Windows and Linux for a few years but am sticking to Ubuntu now). Someone please help. Thanks!

---

### Post by Kayden on 2009-03-24
> **tonyW303 said:**
> ........ When I download a GTK 2.x theme from gnome-look.org, I get it as a .tar.gz. I am relatively new to Ubuntu (back and forth between Windows and Linux for a few years but am sticking to Ubuntu now). Someone please help. Thanks!
.tar.gz *is* a tarball. ;)

[quote=skol31200]We cant use all themes that are on gnome-look.org? Why only gdk?[/quote]
Well, that actually depends on what it is you're looking to theme. If you're using a default Ubuntu installation with GNOME, you'd want to install GTK 2.x themes. However, if you're using something like Emerald, you could install those themes, same thing with Metacity.

Likewise, with KDE and Xfce (if you're using either) you'd want to install whatever matches your respective window manager.

GDM/KDM themes can change the look of the login screen, VLC themes change the look of VLC media player, etc. It's all subjective to what you want to specifically theme.

---

