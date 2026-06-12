---
title: "Changing Grub color mode."
date: 2005-12-12
forum: Desktop Environments
---

### Post by Sgood1971 on 2005-12-12
Hi all,
I followed instructions on another post here and installed a nice Ubuntu grub splash/background. My problem is, it is showing up in what appears to be 256colors. Is there any way to change this? At the moment it looks pretty cheesey.

Thanks in advance for all the help.:)

---

### Post by Sgood1971 on 2005-12-15
I hate to bump my post, but can anyone help me with this? I am very very close to Ubuntu Nirvana.

---

### Post by schilcha on 2005-12-15
[QUOTE=Sgood1971]I am very very close to Ubuntu Nirvana.[/QUOTE]
I've been there already... I gave up fiddling around with usplash. AFAIK, it is the way it is, no more colours, no other resolutions. But! I got the impression that there's a lot of confusion regarding these topics out there -- so maybe it's possible.

I would also be greatful for some contributions to clear things up a little.

---

### Post by canadianwriterman on 2005-12-15
I also had problems installing a prettier replacement for the GRUB boot menu. Whatever I did ended up trashing GRUB entirely and I had to reinstall.

For what it's worth, you can make the boot menu look a LITTLE better by removing the # from the line:

# Pretty colours
**#color cyan/blue white/blue**

...in menu.lst.

---

### Post by Sgood1971 on 2005-12-15
This wasn't exactly the answer I was hoping for, but it *is* just a grub splash after all. I will gladly live with this one minor issue. On a side note, I am going to delete my Windows XP partition tonight when I get home, So I guess Ubuntu Nirvana is closer than I thought.

---

### Post by LanceRushing on 2005-12-16
Sorry, last I checked, the grub background only supported 16 bit (14 color) images.  (could be different now).   I've had good success with black and white.  Or use a very monochromatic image, like a sky

Here is a gentoo write up on making backgrounds in grub by hand (in Gentoo you do everything by hand)
[LIST]
[*][http://gentoo-wiki.com/HOWTO_Splash_image_in_GRUB](http://gentoo-wiki.com/HOWTO_Splash_image_in_GRUB)
[/LIST]

Also don't forget there are several 'spalsh' images people talk about.
[LIST=1]
[*]Grub Splash
[*]Grub Menu Background
[*]Kernel/init Splash Image (splashy?)
[*]GDM Login
[*]Gnome Session Splash (gconf-editor apps->gnome-session->options ...)
[/LIST]

-Lance

---

### Post by Sgood1971 on 2005-12-17
[quote=LanceRushing]Sorry, last I checked, the grub background only supported 16 bit (14 color) images. (could be different now).[/quote] 
I didn't actually count them, but it looks kind of cheesey like when your vid card drivers are wrong in Windows and it will only display in 256 color mode.

> Here is a gentoo write up on making backgrounds in grub by hand (in Gentoo you do everything by hand)[LIST]
[*][http://gentoo-wiki.com/HOWTO_Splash_image_in_GRUB]("http://gentoo-wiki.com/HOWTO_Splash_image_in_GRUB")[/LIST] 
That is very similar to the how to here. Good link thank you.

> Also don't forget there are several 'spalsh' images people talk about.[LIST=1]
[*]Grub Splash
[*]Grub Menu Background
[*]Kernel/init Splash Image (splashy?)
[*]GDM Login
[*]Gnome Session Splash (gconf-editor apps->gnome-session->options ...)[/LIST]-Lance 
I guess I would be talking about # 2 it is the image that is the background for the list of choices to boot to. I went with your monochrome suggestion and came up with a landscape pic I can live with. The Ubuntu community is the best community I have ever seen. Polite and helpful and knowledgeable. Thank you.

---

