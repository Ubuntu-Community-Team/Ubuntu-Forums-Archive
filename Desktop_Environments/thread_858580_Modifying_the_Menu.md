---
title: "Modifying the Menu"
date: 2008-07-13
forum: Desktop Environments
---

### Post by dodle on 2008-07-13
Hello, I found this screenshot of [Linuxmint]("http://linuxmint.com/img/screenshots/elyssa/small/mintmenu.png"), and I really like how the menu looks.  I was wondering if anybody knew how to make the menu look like that in gnome (or other DE's), where it has multiple columns instead of a single column with sub-menus.  If there is a way, please let me know.

---

### Post by dodle on 2008-07-13
Here is another example for the Xfce4 desktop.  This one is actually almost identical to what I would like to have (and since right now I am using Xfce4, this would be perfect).  [http://www.linuxsoft.cz/screenshot_img/9082-a.jpg]("http://www.linuxsoft.cz/screenshot_img/9082-a.jpg")I did some searching around and found out that in this screenshot, a program called Xfce4-panel-menu is used instead of the normal Xfce4-menu.  I found some packages for this and even a repository at [http://os-works.com/view/debian/]("http://os-works.com/view/debian/").  But whenever I try to install it from Synaptic, it tells me that it needs to uninstall the whole Xfce4 Desktop.  Does anyone have any advice?

---

### Post by FerN(SA) on 2008-07-14
I dont know if this might help you, but if you right click on the menu and choose add application there will be a main menu that is similar to the one the one that you want, or if that doesnt work.  If you really want the Xfce why not just install Xdm

Sorry that I cant be more helpful, sitting on a windows pc at the moment

---

### Post by coffeecat on 2008-07-14
> **dodle said:**
> I was wondering if anybody knew how to make the menu look like that in gnome 

Quite easy really. Go to [http://www.linuxmint.com/repository/](http://www.linuxmint.com/repository/) and download the .deb file for mintmenu. Install it, right-click on the panel > Add to Panel > mintMenu.

Trouble is, when I tried it in Ubuntu the Mint menu opened up OK but Accessories, Graphics and so on weren't populated. I tried right-clicking on the MintMenu to edit it, but I got the Alacarte editor for the conventional menu instead. I'm sure there's a way of doing it, but I've got an even better idea for you which is what I did on my laptop and from which I'm posting at the moment.

You want all the goodness of Ubuntu and Gnome, right? You want all the codecs to play various multimedia files, right? You want the Mint menu, right? Easy. Download the Mint iso, burn it and install. It would be unfair on Mint to call it a customised Ubuntu - it's a bit more than that - but in its heart beats good old Ubuntu.

Problem solved! :)

---

### Post by jeremyswalker on 2008-07-14
Go to the linux mint repository as coffecat suggested. Only, make sure you download version 3.2 of the mint menu .deb. It is toward the bottom of the page under the heading of Darnya. It is about the fifth package from the bottom of the page.

---

### Post by sayakb on 2008-07-14
You may also try USP: [http://code.google.com/p/ubuntu-system-panel/wiki/Installation](http://code.google.com/p/ubuntu-system-panel/wiki/Installation)

---

### Post by coffeecat on 2008-07-14
> **jeremyswalker said:**
> Go to the linux mint repository as coffecat suggested. Only, make sure you download version 3.2 of the mint menu .deb. It is toward the bottom of the page under the heading of Darnya. It is about the fifth package from the bottom of the page.
 

Thanks for that. I think it was the 3.0 version I downloaded. That's probably where I went wrong. I'll try 3.2 next time I'm in Ubuntu. I've set my Ubuntu desktop up with Avast instead of the lower panel, and it would be useful to make more room on the upper panel.

---

### Post by jeremyswalker on 2008-07-14
No problem. I've made the same mistake with the 3.0 version. I put the mint menu on my desktop computer, then I went to put it on my laptop and it didn't look the same. After a short period of frustration, I realized there were two different versions on the site. I have to say, the Linux Mint development team has done a great job on their 'slab'-like menu. I'm happy with it. Once again, so everyone knows, if you want the Linux Mint menu, download the .deb **version 3.2** from [http://www.linuxmint.com/repository/](http://www.linuxmint.com/repository/)

---

### Post by coffeecat on 2008-07-14
> **jeremyswalker said:**
> I have to say, the Linux Mint development team has done a great job on their 'slab'-like menu.

I'll second that. It's far, far better than the disaster that openSUSE gives you. I call that the slob menu.

---

### Post by jeremyswalker on 2008-07-14
> **coffeecat said:**
> I'll second that. It's far, far better than the disaster that openSUSE gives you. I call that the slob menu.

LOL! That's for sure!

:lolflag:

---

### Post by dodle on 2008-07-14
> **FerN(SA) said:**
> I dont know if this might help you, but if you right click on the menu and choose add application there will be a main menu that is similar to the one the one that you want, or if that doesnt work.  If you really want the Xfce why not just install Xdm
Is Xdm better than Gdm?

Thanks for the helpful posts everyone.  I'm going to try the mint-menu.

My mothers computer is running the Xfce4 desktop, because it's pretty wussy:).  If I install Xdm would I be able to run the xfce4-panel-menu?  Or is there a way to get mint-menu to work on Xfce4?  I would really like her to have a better menu.

---

### Post by chunchengch on 2008-07-14
I modify the mintmenu deb file to fit the Ubuntu style, you can find it here [http://ubuntuforums.org/showthread.php?p=5383757#post5383757](http://ubuntuforums.org/showthread.php?p=5383757#post5383757)

[ATTACH]77760[/ATTACH]

---

### Post by jeremyswalker on 2008-07-14
> **LinuxIsInnovation said:**
> You may also try USP: [http://code.google.com/p/ubuntu-system-panel/wiki/Installation](http://code.google.com/p/ubuntu-system-panel/wiki/Installation)

I just checked this out. This is not a bad menu either. There are a lot more customization features than in mintmenu. Definitely in the same league as mintmenu. The creator has done a fine job.

---

### Post by dodle on 2008-07-14
> **LinuxIsInnovation said:**
> You may also try USP: [http://code.google.com/p/ubuntu-system-panel/wiki/Installation](http://code.google.com/p/ubuntu-system-panel/wiki/Installation)

Sorry, I should have tried that earlier.  That works pretty well.  I was wondering if there were any other plugins for it though.

---

### Post by FerN(SA) on 2008-07-15
GDM is the gnome display manager
XDM is XFCE display manager

There is no better, it is just a matter of preference.  But I see you have already found your solution.  

I think that XDM is lighter on resources, while gnome has alot of functionality

---

