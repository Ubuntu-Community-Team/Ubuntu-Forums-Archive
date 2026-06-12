---
title: "Gnome icons in Firefox and Openoffice (Kubuntu)"
date: 2005-06-24
forum: Desktop Environments
---

### Post by wdso on 2005-06-24
Hi,

I heard a lot of good things about Ubuntu and I really like its concept, being complety free and designed to be "for humans".

However, I really can't stand Gnome (curiously enough, KDE seems to be a lot more popular in Europe). When I heard about Kubuntu I decided to give it a try. Installation went fine, KDE is up and running. It took me a while to figure out the universe/multiverse concept and to find the backports but after all, everything went fine.

Sadly, there a two things I don't like about Kubuntu, apart from the obvious lack of proper configuration GUIs:
Firefox is compiled with Gnome Support, thus it has Gnomy-style OK and CANCEL buttons (read: ugly Gnome Icons). OpenOffice also has Gnome Icons, although OpenOffice-kde is installed (OpenOffice.org2 seems to be okay, but not usable yet, btw, why isn't there a current build of the beta in universe yet?)

I did an apt-get source mozilla-firefox and it turned out that there were various gnome configure flags and an .xpm patch. Maybe Kubuntu needs an extra package, say "mozilla-firefox-kubuntu" (which could include Plastikfox). Since I'm planning to get to know Debians Build system (I built a couple of rpms), I would volunteer.

Btw, I know of gtk-qt-engine, but I don't think its usable for Firefox (lots of bugs and it seems it won't get fixed any time soon). Therefore, I'm using gtk-industrial - looks a bit like Plastik.

One more question: It seems GDM is used in Kubuntu (at least I've never seen that style), how can I switch to KDM?

Another aspect is that Ubuntu - as well as Kubuntu - is optimized for i386 only. Are there any plans to optimize for i686? Shouldn't be too complicated when using apt-build...

Thanks in advance!

---

### Post by deadlands on 2005-06-24
I just use the vanilla Firefox package from Mozilla.org with Plastikfox. The Gnome centric Ubuntu build is obnoxious. I don't like the file navigation at all.

---

### Post by wdso on 2005-06-24
Of course, thats a way around Ubuntus Firefox, but you sacrifice all advantages that come with apt-get. Kubuntu should include a special version.

---

### Post by SGC on 2005-06-24
[QUOTE=wdso]
One more question: It seems GDM is used in Kubuntu (at least I've never seen that style), how can I switch to KDM?[/QUOTE]

Kubuntu cames with kdm by defualt, but if for some reason you have GDM then , do the following:

- Install kdm if you don't have it ( apt-get install kdm )

- Run the folllowing command ( dpkg-reconfigure kdm )

[QUOTE=wdso]
Btw, I know of gtk-qt-engine, but I don't think its usable for Firefox (lots of bugs and it seems it won't get fixed any time soon). Therefore, I'm using gtk-industrial - looks a bit like Plastik.
[/QUOTE]

Go to control center and choose "Appearances & Themes" then "GTK Style and fonts" under "GTK  style" choose "Use another style" and select "Qt" then hit apply button

 After that select "Use my KDE style in GTK applications" and hit the apply button again. That should makes you firefox look like a KDE/QT applications and uses thier buttons.

---

### Post by coolclassic on 2005-06-24
you may have to install gtk2-engines-gtk-qt before you can do the above you can use kynaptic to install.

---

### Post by wdso on 2005-06-24
Maybe I didn't express myself clearly. I gave gtk-qt-engine a try, but it screws up Firefox (e.g. menu hovers). So gtk-qt is no option here. What I want (and I'm sure a lot of other Kubuntu users think the same) is a non Gnome build of Firefox. The same applies to OpenOffice.

---

### Post by Firetech on 2005-06-24
You can install the plastikfox theme ([http://www.polinux.upv.es/mozilla/plastikfox/releases/crystalsvg/plastikfox-crystalsvg/install.html](http://www.polinux.upv.es/mozilla/plastikfox/releases/crystalsvg/plastikfox-crystalsvg/install.html)) for Firefox, and it will get more KDE-ish.

For OpenOffice, I can only recommend you to use either Koffice 1.4 (read [http://www.kubuntu.org/hoary-koffice-14.php](http://www.kubuntu.org/hoary-koffice-14.php) for info) or openoffice 2 beta, which is fairly (98%), though not entirely stable. (the packages you need are openoffice.org2 and openoffice.org2-kde).
I have uninstalled OpenOffice 1 on my computer and rely entirelly on OO2 and KOffice.

---

### Post by wdso on 2005-06-24
Thanks for the tip, but I don't like Plastikfox. If you're using OO.org2 I can recommend builds from: [http://ftp.linux.cz/pub/localization/OpenOffice.org/](http://ftp.linux.cz/pub/localization/OpenOffice.org/)
They have full KDE support and seem very stable. Another good thing is, you can get .debs from there.

---

### Post by wdso on 2005-06-24
Alright, I got rid of the Gnome Icons, here is what I did:

```
added apt-src debian/testing to /etc/sources.list (find a mirror first)
apt-src install mozilla-firefox (should download 1.04 from debian testing)
cd mozilla-firefox-1.04
fakeroot dpkg-buildpackage
apt-get remove firefox (conflicts with mozilla-firefox)
dpkg -i mozilla-firefox(...).deb
```

Still this is no real solution. As mentioned before, there should be a special Firefox version for Kubuntu users. I suggest to integrate Debian's mozilla-firefox in Ubuntu universe or add it to the backports, how about the name mozilla-firefox-kde (as a goodie, this package could ship Plastikfox for those who like it). Only that way, one could benefit from updates via apt.

---

### Post by Feanor on 2005-06-25
[QUOTE=wdso]Hi,

I heard a lot of good things about Ubuntu and I really like its concept, being complety free and designed to be "for humans".

However, I really can't stand Gnome (curiously enough, KDE seems to be a lot more popular in Europe). When I heard about Kubuntu I decided to give it a try. Installation went fine, KDE is up and running. It took me a while to figure out the universe/multiverse concept and to find the backports but after all, everything went fine.

Sadly, there a two things I don't like about Kubuntu, apart from the obvious lack of proper configuration GUIs:
Firefox is compiled with Gnome Support, thus it has Gnomy-style OK and CANCEL buttons (read: ugly Gnome Icons). OpenOffice also has Gnome Icons, although OpenOffice-kde is installed (OpenOffice.org2 seems to be okay, but not usable yet, btw, why isn't there a current build of the beta in universe yet?)

I did an apt-get source mozilla-firefox and it turned out that there were various gnome configure flags and an .xpm patch. Maybe Kubuntu needs an extra package, say "mozilla-firefox-kubuntu" (which could include Plastikfox). Since I'm planning to get to know Debians Build system (I built a couple of rpms), I would volunteer.

Btw, I know of gtk-qt-engine, but I don't think its usable for Firefox (lots of bugs and it seems it won't get fixed any time soon). Therefore, I'm using gtk-industrial - looks a bit like Plastik.

One more question: It seems GDM is used in Kubuntu (at least I've never seen that style), how can I switch to KDM?

Another aspect is that Ubuntu - as well as Kubuntu - is optimized for i386 only. Are there any plans to optimize for i686? Shouldn't be too complicated when using apt-build...

Thanks in advance![/QUOTE]

I've the same problem with gnome icons in OpenOffice and Firefox. I've installed plastik fox, but in this way the colours and icons are different respect my kde-theme. I've installed gtk2-engines-gtk-qt, and problem now is that some colours are not adapted as well as kde-theme, and however icons in OpenOffice are gnome icons.

In reguard of i386, you can download and install i686 kernel from apt-get, it will appear as a new entry in your grub list.

Sorry for my bad english!  :-#

---

### Post by wdso on 2005-06-25
Packages can also be optimized to i686, unfortunately Debian and Ubuntu release i386 only.
I might recompile some packages with apt-build, maybe I get a performance gain (I have my doubts to be honest)

---

### Post by daniel2501 on 2005-06-25
I've have similar problems. gtk-qt on my system seems a little broken. It works for some app, but not others, i.e. synaptic, which appears with the basic gtk look.
Choose a nice looking control style in GCC, and make sure gnome-settings-daemon is running.

---

### Post by wdso on 2005-06-25
You don't need to run gnome-settings-daemon, its a waste of ressources when you run KDE.
You can either manually edit .gtkrc-2.0 or us the kcontrol modul of gtk-qt-engines (open KDE's Control Center).

---

### Post by Feanor on 2005-06-29
[QUOTE=wdso]Packages can also be optimized to i686, unfortunately Debian and Ubuntu release i386 only.
I might recompile some packages with apt-build, maybe I get a performance gain (I have my doubts to be honest)[/QUOTE]

Does it work?  :shock: 

It will be very cool if on apt-get it will be possible to upgrade packets from i386 to i686... I think recompiling them will take a lot of time! And honesty I don't know how I can do it  :-|

---

### Post by wdso on 2005-06-29
[http://julien.danjou.info/article-apt-build.html](http://julien.danjou.info/article-apt-build.html)

---

### Post by Feanor on 2005-07-01
It seem just a little complicated for my skills...  :-? Is this the only way to convert i386 in i686? Is there something that automatically detects the configuration of my system and recompile the packets?  ](*,)

Thanks anyway for the tip  ;-)

---

