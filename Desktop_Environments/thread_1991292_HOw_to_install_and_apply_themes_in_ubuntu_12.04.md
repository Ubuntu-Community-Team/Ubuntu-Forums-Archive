---
title: "HOw to install and apply themes in ubuntu 12.04???"
date: 2012-05-30
forum: Desktop Environments
---

### Post by Jaskaran498 on 2012-05-30
hi
As i am new to everything for ubuntu including ubuntu itself.
I want to know how to install and apply themes in ubuntu 12.04. I am talking about custom themes ofcourse, not defaults.
i read some tutorials but they dont seem to be for ubuntu 12 including using trying some app called "advanced settings". nothing works. Even if i proceed as directed, the theme doesnt show in theme selection drop-down menu.

Additional INfo--> I am trying to install "Azenis" theme.


Please tell me how to install themes.
Thanks in advance and sorry if i am posting in wrong section.

---

### Post by Frogs Hair on 2012-05-30
Hello and Welcome 

The theme you would like to install is a GTK 2 and won't work in 12.04. 

Install Downloaded Themes or icons in 11.10-12.04

Install the Gnome Tweak Tool / Advanced Settings for making theme selections from the software center .  


Use only GTK 3.4 themes for 12.04 amd 3.2 themes for 11.10. Check this in the theme description at the download loation. 

Download and fully extract the theme packages and hold the folders on the desktop until needed . 


(Single User) Create a .themes and .icons folder in home / hidden folders . Use Crtl + H to open hidden folders in Nautilus.

(All Users) Use gksudo nautilus in the terminal to open  Nautilus as root and navigate to > File System / usr / share / themes or icons .

Place the folders in either Loation . Use Advanced Settings to make theme selections . Logout - in may be required before themes are visible in Advanced Settings.
  
Theme PPAS are easy to install and keep themes up to date. below is one example. 


[http://www.webupd8.org/2012/04/zukitwo-zukini-holo-theme-packs-updated.html](http://www.webupd8.org/2012/04/zukitwo-zukini-holo-theme-packs-updated.html)

---

### Post by JRV on 2012-05-30
Install ubuntu-tweak with these commands:
```

sudo add-apt-repository ppa:tualatrix/ppa
sudo apt-get update
sudo apt-get install ubuntu-tweak

```

Navigate to Tweaks=>Theme.

---

### Post by Jaskaran498 on 2012-05-31
OK. Thanks for info.
I did following-->
Installed unbuntu tweak/advanced settings (preinstalled).
Downloaded "Zukitwo" theme from above link given.
Extracted "Zukitwo-Brave".
Created a new folder ".Themes" in home and pressed ctrl+h.
Put the .tar.gz and the folder "Zukitwo-brave" in .themes.
but my theme doesnt appear ins theme selection options.
in teminal, ran commands-->
```
sudo add-apt-repository ppa:webupd8team/themes
sudo apt-get update
sudo apt-get install zukitwo-gtk-theme zukitwo-brave-gtk-theme

```
but it gave me error something like E: location not found (not exactly this one but like this).
i also used sudo apt-get install zukitwo-colors-theme. It did successfully but theme doesnt show in theme selection still.
please tell why and the solution.


Edit:
I just accidently installed a theme by trying some method.
now when i use same method for another supported theme, the error appears in terminal-->
E: Unable to locate package zukitwo-Wise-gtk-theme
please tell solution.



Please give me step-by-step tutorial for installing themes. :(

---

### Post by traditionalist on 2012-05-31
> **Jaskaran498 said:**
> 

<SNIP>


Please give me step-by-step tutorial for installing themes. :(

Just use this;

[http://ubuntuforums.org/showthread.php?t=1988119](http://ubuntuforums.org/showthread.php?t=1988119)

---

### Post by overcast on 2012-05-31
Myunity also lets you change the themes and icons and other theme related tweaks. Install Myunity from the repository.

---

### Post by Frogs Hair on 2012-05-31
>  It did successfully but theme doesnt show in theme selection still.
please tell why and the solution.

Have you installed the Gnome Tweak Tool / Advanced Settings ?

---

### Post by Jaskaran498 on 2012-06-01
> **Frogs Hair said:**
> Have you installed the Gnome Tweak Tool / Advanced Settings ?
yes. I already said that in 1st post.
Thanx overcast, ill try and then tell results here.
Also thanx to traditionalist. But one stupid question... How to use it? I created a new folder .systemcolors and put extracted file in it. Now what after that?

---

### Post by Frogs Hair on 2012-06-01
> **Jaskaran498 said:**
> yes. I already said that in 1st post.
Thanx overcast, ill try and then tell results here.
Also thanx to traditionalist. But one stupid question... How to use it? I created a new folder .systemcolors and put extracted file in it. Now what after that?

Usually themes that don't appear in the Tweak Tool , Ubuntu Tweak , or My Unity are not the correct themes or not fully extracted that doesn't mean there isn't an other problem.

The following command won't work because zukitwo brave is part of the zukitwo colors package.

```
sudo apt-get install zukitwo-gtk-theme zukitwo-brave-gtk-theme
``` 

Use the following commands one by to install the PPA if you want to use it.
```
sudo add-apt-repository ppa:webupd8team/themes
sudo apt-get update
sudo apt-get install zukitwo-colors-theme
```

---

### Post by dancairns on 2012-06-01
hey everyone i found some cool themes here for 12.04 [http://ubuntudan.blogspot.com.au/2012/06/themes-collection-for-ubuntu-1110.html](http://ubuntudan.blogspot.com.au/2012/06/themes-collection-for-ubuntu-1110.html) hope you all liked them as much as i did :)

---

### Post by Jaskaran498 on 2012-06-01
thanx a bunch Frogs Hair. That worked and i was finally able to change some good themes :v
and dancairns thanx for link. Theme are good there.

Problem solved!!!

---

