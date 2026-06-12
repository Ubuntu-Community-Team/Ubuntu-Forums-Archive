---
title: "Taskbar Effects"
date: 2007-05-19
forum: Desktop Effects &amp; Customization
---

### Post by Ayien on 2007-05-19
Hello everyone. I'm a new Linux user. Started out about yesterday when I got the huge desire to make my own distro. with some of my friends. Right now, I'm using Linux (Edubuntu's latest version) and I installed Beryl without a hitch on a 5 year old laptop. From seeing what I can do with a 5 year old laptop and beryl, makes me laugh at Windows Vista. :popcorn:


Anyway, my question is this: what is a good program to use that can make some cool changes to the taskbar? I'm looking for something that looks like Vista's taskbar, but...much better.


Thanks a lot guys.

P.S. Ubuntu > world.

---

### Post by Ub1476 on 2007-05-19
Hiya

I don't know of any application which make your panel look like Vista, but you may try kiba-dock, which make it look like Mac:) Guide here: [Linky]("http://ubuntu1501.blogspot.com/2007/04/install-kiba-dock-oncedgy-eft.html")

---

### Post by reacocard on 2007-05-19
Or AWN for another dock, much better IMO: [HOWTO]("http://ubuntuforums.org/showthread.php?t=385981")

You can also fiddle with the options under 'background' in your panel's properies, or try installing a  [Vista GTK theme]("http://gnome-look.org/content/show.php/LiNsta+%28LiNsta+is+Not+Vista+%3B-%29?content=42697&PHPSESSID=f8ae2e23edc69e23dfa0806da141c72c") that changes the taskbar.

---

### Post by Ayien on 2007-05-19
Thanks guys. I installed Kiba Dock without a hitch. = )

---

### Post by Ayien on 2007-05-19
The GTK theme is rather difficult to follow on installation. Does anyone know where there is a tutorial for installing these kinds of theme adaptations? 

Thanks.

---

### Post by reacocard on 2007-05-19
> **Ayien said:**
> The GTK theme is rather difficult to follow on installation. Does anyone know where there is a tutorial for installing these kinds of theme adaptations? 

Thanks.

Open System -> Preferences -> Theme

Drag & Drop the GTK theme into the window to install it.

Select your current GNOME theme (Human, if you haven't changed it), choose Customize and set the 'Controls' option to your new GTK theme (LiNsta is the one from the link), and click close. Now select the custom theme option that just appeared, choose 'Save Theme' and give it a name. Now your new theme is installed and will stay active between restarts. To reset to the default, just open Theme again and select 'Human'.

---

### Post by Ayien on 2007-05-19
Thanks.

I'm also wondering how do I uninstall Kiba-Dock. I used the terminal through one of the HOWTO's here. Basically, downloading all the packages without using the package manger. How do I uninstall it through the terminal?

Thanks.

---

### Post by reacocard on 2007-05-19
> **Ayien said:**
> Thanks.

I'm also wondering how do I uninstall Kiba-Dock. I used the terminal through one of the HOWTO's here. Basically, downloading all the packages without using the package manger. How do I uninstall it through the terminal?

Thanks.

You installed from packages, not source? If so, a simple
```
sudo apt-get remove --purge kiba-dock
```
should do it. If you installed from source, open a terminal in the directory where you put the source (it has a Makefile in it) and do
```
sudo make uninstall
```

---

### Post by Ayien on 2007-05-19
No, I don't think it was source. I tried the fist option.

This is what I get:

```
ayien@ayien-laptop:~$ sudo apt-get remove --purge kiba-dock
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package kiba-dock
ayien@ayien-laptop:~$ 

```

I used this site to install the dock: [http://ubuntu1501.blogspot.com/2007/04/install-kiba-dock-oncedgy-eft.html](http://ubuntu1501.blogspot.com/2007/04/install-kiba-dock-oncedgy-eft.html)

---

### Post by reacocard on 2007-05-20
> **Ayien said:**
> I used this site to install the dock: [http://ubuntu1501.blogspot.com/2007/04/install-kiba-dock-oncedgy-eft.html](http://ubuntu1501.blogspot.com/2007/04/install-kiba-dock-oncedgy-eft.html)

That's from source. Whenever you use 'make' to install something, you're going from source. Just go back to the folder you did make in, open a terminal in it and do 'sudo make uninstall'.

---

