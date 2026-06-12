---
title: "Disguising Ubuntu as Windows XP??? (Solved)"
date: 2005-11-19
forum: Desktop Environments
---

### Post by Fearan on 2005-11-19
i need to find themes that will make my gnome desktop look like Windows XP to the untrained eye!!! i haven't been able to find one due to the severe hatred of windows everywhere... (good, but annoying right now!) Anyway, i need to disguise my desktop as Windows XP.  It needs to look like Windows XP has been installed on the computer, even though ubuntu was installed.  i will need a theme for gtk, metacity, icons, gdm, and possibly grub and the boot-up progress screen.  does anyone have any suggestions as to where i could find such themes?
thanks,
Fearan

---

### Post by GeneralZod on 2005-11-19
This isn't what your looking for (sorry) but I'll post it anyway as some might get a kick out of it :)

[http://www.kde-look.org/content/show.php?content=1499](http://www.kde-look.org/content/show.php?content=1499)

---

### Post by Fearan on 2005-11-19
nice... now if only they had it for gnome...

---

### Post by varunus on 2005-11-19
There is a GTK engine called the "eXPerience engine."  Its supposed to make GNOME look exactly like windows XP.

There are some debian packages available, but they are for debian and not ubuntu.  They're for debian stable, though, so they should work.  Here they are:
[http://benjamin.sipsolutions.net/debian/stable/gnome-icon-theme-experience_2.0+pre2.1-9_all.deb](http://benjamin.sipsolutions.net/debian/stable/gnome-icon-theme-experience_2.0+pre2.1-9_all.deb)
[http://benjamin.sipsolutions.net/debian/stable/gtk2-engines-experience_0.10.0-1_i386.deb](http://benjamin.sipsolutions.net/debian/stable/gtk2-engines-experience_0.10.0-1_i386.deb)
[http://benjamin.sipsolutions.net/debian/stable/gtk2-themes-experience_3.03-10_all.deb](http://benjamin.sipsolutions.net/debian/stable/gtk2-themes-experience_3.03-10_all.deb)
[http://benjamin.sipsolutions.net/debian/stable/gnome-icon-theme-crystalsvg_1.2.0-5_all.deb](http://benjamin.sipsolutions.net/debian/stable/gnome-icon-theme-crystalsvg_1.2.0-5_all.deb)

With those four packages, which include an icon, metacity, and GTK2 theme, I think, you should be able to get an XP look.

Download them all to a folder, open up a terminal, and then type the following:
```

cd /path/to/stuff/
sudo dpkg -i *
sudo apt-get install -f
```

After this, you should have some XP themes in your chooser.

---

### Post by aysiu on 2005-11-19
[SmoothXP](http://gnome-look.org/content/show.php?content=16732)?
[Redmond Login](http://gnome-look.org/content/show.php?content=22254)?

---

### Post by Fearan on 2005-11-20
thanks for your help guys! my ubuntu is disguised now! (i needed it for my future laptop, which will "require having windows installed on it") LOL!

---

### Post by ren wins on 2005-11-20
just out of curiosity
who would require you to have windows installed?

---

### Post by HermanAB on 2005-11-20
Cool, but how are you going to simulate the BSODs?

---

### Post by matthew on 2005-11-20
[quote=HermanAB]Cool, but how are you going to simulate the BSODs?[/quote]
System->Preferences->Screensaver
Choose BSOD

---

### Post by Hairy_Palms on 2005-11-20
i just XPeed all over my computer lol [http://i21.photobucket.com/albums/b264/Hairy_Palms/winbloze2.jpg](http://i21.photobucket.com/albums/b264/Hairy_Palms/winbloze2.jpg)
[http://i21.photobucket.com/albums/b264/Hairy_Palms/Winbloze.jpg](http://i21.photobucket.com/albums/b264/Hairy_Palms/Winbloze.jpg)

---

### Post by matthew on 2005-11-20
[quote=Hairy_Palms]i just XPeed all over my computer lol[/quote]
I'm not sure whether to be impressed or frightened... :)

---

### Post by ecobuntu on 2005-11-20
[QUOTE=GeneralZod]This isn't what your looking for (sorry) but I'll post it anyway as some might get a kick out of it :)

[http://www.kde-look.org/content/show.php?content=1499](http://www.kde-look.org/content/show.php?content=1499)[/QUOTE]

Oh that's just dreadful :)

---

### Post by Hairy_Palms on 2005-11-21
i also got the vlc wmp10 skin and changed openoffice to have an MSoffice splash screen lmao
im almost done but does anyone know how to make openoffice look like it does in kde/windows? i installed the kde integration package but nothing really changed, once ive done that im gonna test it out on people to see if they can even tell theyre using linux :D

---

### Post by Fearan on 2005-11-22
[QUOTE=ren wins]just out of curiosity
who would require you to have windows installed?[/QUOTE]
the leaders of the household require it... such is life.

---

### Post by cdsboy on 2005-11-22
lol i wouldn't suggest doing that they'll find out sooner or later...

---

### Post by sawjew on 2005-11-22
If you really want the XP look check this out.

[http://www.xpde.com/index.php]("http://www.xpde.com/index.php")

---

### Post by kairu0 on 2005-12-03
[QUOTE=Hairy_Palms]i just XPeed all over my computer lol [http://i21.photobucket.com/albums/b264/Hairy_Palms/winbloze2.jpg](http://i21.photobucket.com/albums/b264/Hairy_Palms/winbloze2.jpg)
[http://i21.photobucket.com/albums/b264/Hairy_Palms/Winbloze.jpg](http://i21.photobucket.com/albums/b264/Hairy_Palms/Winbloze.jpg)[/QUOTE]

Please tell me that's not Linux LOL

---

### Post by IanLowe on 2005-12-03
[QUOTE=cdsboy]lol i wouldn't suggest doing that they'll find out sooner or later...[/QUOTE]

of course... by that time, you will have enough of a demonstration that Ubuntu can do the same things as that XP machine and remove the original objection!

Ian.

---

### Post by Fearan on 2005-12-03
[QUOTE=Hairy_Palms]i also got the vlc wmp10 skin and changed openoffice to have an MSoffice splash screen lmao
im almost done but does anyone know how to make openoffice look like it does in kde/windows? i installed the kde integration package but nothing really changed, once ive done that im gonna test it out on people to see if they can even tell theyre using linux :D[/QUOTE]
If they're using it, they will be able to tell the difference on openoffice... the layout is slightly different than MS office.

---

### Post by Fearan on 2005-12-03
[QUOTE=kairu0]Please tell me that's not Linux LOL[/QUOTE]
I think it is... he's running firestarter!

---

### Post by Fearan on 2005-12-03
[QUOTE=IanLowe]of course... by that time, you will have enough of a demonstration that Ubuntu can do the same things as that XP machine and remove the original objection!

Ian.[/QUOTE]
I agree... but it's too late! they've finally agreed to let me use open-source software on my laptop, if i get one.  but too bad they don't switch to it on their own machines! lol. too bad for *them!*

---

