---
title: "Kubuntu vs KDE-Standard?"
date: 2012-09-15
forum: Desktop Environments
---

### Post by StewartM on 2012-09-15
Hello,

I have two computers, a desktop and a laptop. Both are now "Ubuntu 12.04" computers.

The laptop I kept on a 6-month release cycle. When I installed Ubuntu 11.10, because I also help maintain a number of non-techie friends' Ubuntu computers, with the demise of GNOME 2 I started investigating other desktop environments, in help them with the transition. Among these was Kubuntu-desktop, which I liked so much that I eventually switched to Kubuntu for daily use (though I changed the boot splash back to Ubuntu, as I preferred that splash screen, and I still have and keep Unity, GNOME 3/GNOME classic, and Enlightenment on my systems either for specific purposes or to keep handy in case something breaks in one Desktop environment as I can go in and fix it in another). I enabled the Kubuntu backports to keep abreast of the latest releases of KDE (it's now up to KDE 4.8.5.

My desktop computer was on Ubuntu 10.04 until I upgraded a little more than two weeks ago, with the release of Ubuntu 12.04.1. I searched for Kubuntu-desktop in the repositories, and did not find it. I did find the metapackage "kde-standard" and installed that, thinking that since Canonical was no longer supporting Kubuntu after the 12.04 release, it perhaps did not want to encourage its use. (Later I did find out that kubuntu-desktop *was* still in the repositories; one had to "show technical items" to find it).

I caught on that there was a difference between the two metapackages when I found out that:

1) Installing kde-standard didn't change my boot splash screen on my desktop (it had on the laptop)

2) When trying to customize the application look and feel for GNOME (or at least non-KDE) applications I couldn't get them to look the same. Here are some screenshots (with pretty much identical settings):

a) Evolution (desktop first, Laptop second)

[IMG]http://i211.photobucket.com/albums/bb262/netnguy01/Bug%20Reports/evolutiondesktop.png[/IMG]

[IMG]http://i211.photobucket.com/albums/bb262/netnguy01/Bug%20Reports/evolutionheaderlaptop.jpg[/IMG]

b) Firefox (desktop first, laptop second)

[IMG]http://i211.photobucket.com/albums/bb262/netnguy01/Bug%20Reports/firefoxdesktop.png[/IMG]

[IMG]http://i211.photobucket.com/albums/bb262/netnguy01/Bug%20Reports/firefoxheaderlaptop2.jpg[/IMG]

BTW, I have both gtk3-oxygen-engines and gtk2-oxygen-engines on both computers.

3) The Twokinds comic I used in Kubuntu broke earlier this year and wasn't fixed. In KDE-standard it works (I fixed in in the Kubuntu version by copying and pasting the relevant .desktop files into the /user/.kde/ subfolders).

4) When I enabled the backports in the desktop (originally with KDE 4.8.4), I got KDE 4.9 (!) instead of the KDE 4.8.5 which is the latest for Kubuntu.

Now that I have found the kubuntu-desktop in the "show technical items" in the repositories, I am wondering if it would be OK to install that customization. I am hesitant, because:

a) For some GNOME apps like Evolution and Rhythmbox, kde-desktop actually faithfully preserves the GNOME 3 look. My Kubuntu laptop does not (I've gotten it so I think it looks pretty, but it's not faithful);

b) More importantly, now that I'm on KDE 4.9 by enabling the backports on my desktop, but only on 4.8.5 by doing the same on my laptop, would downloading and installing kubuntu-desktop break something? (I figured that if kubuntu-desktop was ready for 4.9, it would already be in the backports).

Replies and input appreciated.

StewartM

---

### Post by Epodx64 on 2012-09-15
I don't think it would break anything it might grab some extra packages or say its already up to date however; if it looks like apt is going to grab a whole bunch of packages specifically if it looks like its going to "downgrade" anything abort it don't install it or if it looks like it's going to try and grab the entire desktop again I wouldn't do it either might cause some file conflicts but I think it will just grab whatever kde-standard didn't happen to download if anything. 

I'm really not sure about the GTK2/3+ themes could be a bug with the new KDE 4.9?

---

### Post by StewartM on 2012-09-19
Well, today I forced the laptop (kubuntu-desktop)from 4.8.5 to 4.9.1 by doing the update from the command line. 

After that, I was able to get Rhythmbox and Evolution to look exactly like they do on my kde-standard desktop by switching from "Radiance" to "Ambiance".

Now I'm going to see if can fix those boxy-like Pidgin and Firefox displays by playing around with the other themes.

Making Progress!

StewartM

---

### Post by Jakin on 2012-09-20
On 11.10 amd64 with KDE 4.8.5, what i did to fix odd looking app appearances (which were gnome3 based) i did the following:

sudo apt-add-repository ppa:gnumdk/ppa
sudo apt-get update
sudo apt-get install gtk3-engines-oxygen


Then, 
make gtk-3.0 folder in HOME/.config folder. (show hidden files in home directory)
Then in gtk-3.0 folder create text file " settings.ini " with following contents:

```
[Settings]
gtk-theme-name = oxygen-gtk3
```

Save the settings.ini and restart the computer- and all was good for me.

Although i see you upgraded to 4.9- so maybe this is irrelevant.

---

### Post by bra|10n on 2012-09-25
Alt-F2, kdesu systemsettings;

Go to Application Settings and check widget style in use is oxygen, GTK Style is Oxygen-GTK etc

---

### Post by kio_http on 2012-09-25
> **bra|10n said:**
> Alt-F2, kdesu systemsettings;

Go to Application Settings and check widget style in use is oxygen, GTK Style is Oxygen-GTK etc

Unfortunately gtk 3 themes are not applied using that in Kubuntu 12.04. This feature will be added in 12.10. In 12.04 you have to change the gtk3 using the gnome configuration tools which is why his applications retain the "Ubuntu" look.

---

