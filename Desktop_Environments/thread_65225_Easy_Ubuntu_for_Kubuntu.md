---
title: "Easy Ubuntu for Kubuntu?"
date: 2005-09-13
forum: Desktop Environments
---

### Post by perlmonger on 2005-09-13
Has anyone modified the Easy Ubuntu script to work with KDE? Or is there possibly a Kubuntu equivalent out there somewhere? It would be great to have a way to get all the browser plugins and multimedia apps working in one fell swoop.

Thanks

---

### Post by frodon on 2005-09-13
[http://olwin.free.fr/](http://olwin.free.fr/)

---

### Post by perlmonger on 2005-09-13
[QUOTE=frodon][http://olwin.free.fr/](http://olwin.free.fr/)[/QUOTE]

Uh...that's exactly what I'm looking for...sort of. This would be perfect if I could read french. At least I think it's french. Do you think I could get by ok just taking defaults and clicking the button? Maybe someone will translate it eventually.

Thanks much!

---

### Post by frodon on 2005-09-13
This is the translated text line by line :
Download archive here
INSTALL : open a terminal and type :  dpkg -i easykubuntu-0.3.deb
To run the application : menu kde --> System --> Easy Kubuntu 
UNINSTALL : in kynaptic search for easyubuntu or with a terminal : apt-get remove easykubuntu

The first window ask you your root password because easyubuntu need to be run as root to perform apt-get functionalities.
The second windows tell you that easyubuntu want to modify your source.list file in order to add the good repositories.

Now this is the translation of the Kdialog box line by line :
Multimedia : Install most of needed packages to read and play viseos/music
Firefox plugin : install popular plugins (java, flash, realplayer, videos,)
Peer to Peer : Install amule and Azureus
Desktop tools : Koffice install
Lamp : Linux Apache2 Mysql Php4
Web development : Quanta + install
Install gtk-qt which allow your gnome/GTK application to get KDE-like looking
Photo : install a software to manage your photo albums (digikam)

Ok i think you will be able to understand what you do now  ;-)

---

### Post by jbinc1 on 2005-09-13
Thanks for the translation. It's what I've been looking for.

---

### Post by snowjunkie on 2005-09-14
[QUOTE=jbinc1]Thanks for the translation. It's what I've been looking for.[/QUOTE]

Hi jbinc1,
Did it work for you ok?

The whole installation bit confuses me a bit.... I assume you install it by unpacking the debian package.  The run it, ticking all the appropriate categories you need.  And then after it has completed you uninstall easykubuntu using apt-get remove ??

---

### Post by jbinc1 on 2005-09-14
[QUOTE=snowjunkie]Hi jbinc1,
Did it work for you ok?

The whole installation bit confuses me a bit.... I assume you install it by unpacking the debian package. The run it, ticking all the appropriate categories you need. And then after it has completed you uninstall easykubuntu using apt-get remove ??[/QUOTE]

It worked ok for me. I still think I'd like to see an english translation though.:)  You have the install and run correct. I believe frodon was just giving all of the info from the site in the translation as far as how to uninstall it. I don't see any reason to uninstall unless you want to. Make sure you have a current backup of your sources.list file before installing this app. It does change your repository list. I think it makes a backup for you, but I would make one yourself just to be safe.
Good luck.

---

### Post by olwin on 2005-09-18
First beta for Easy Kubuntu (English and French version , I have only test the french version for the moment):
 
 (Only for Hoary)
 Easy Kubuntu allow you to:
 
 Localization : Translation Kubuntu in your language
 Multimedia : Needed codecs to read lot of sounds and videos
 Konqueror : Most used plugins (Java, Flash, Real, ...), Microsoft fonts
 Additional archiving tools (rar and ace)
 Peer to Peer : aMule (eMule clone) and Azureus (BitTorrent)
 Skype : A free (as a free beer) Voice Over IP software
 KOffice - Integrated Office Suite
 Makes your GTK 2(Gnome) apps look like Qt (KDE) ones
 DigiKam : a simple digital photo management application
 Drivers with 3D support for NVIDIA AND ATI graphics cards (beta)
 
 INSTALL :
 dpkg -i EasyKubuntu-0.4.deb
 
 RUN :
 Menu K --> System --> Easy Kubuntu
 
 REMOVE :
 apt-get remove EasyKubuntu
 
 [TEST IT](http://olwin.free.fr/EasyKubuntu-0.4.deb)

---

### Post by jbinc1 on 2005-09-18
When I click on the the "test it" link, I see the file has a .fr after it. I'm guessing that's for French. How do I get the english version? Also, why do you have to uninstall the app after using it? I don't quite understand this, I guess. 

Thanks

---

### Post by olwin on 2005-09-18
> When I click on the the "test it" link, I see the file has a .fr after it. I'm guessing that's for French. How do I get the english version? 
 
 Thanks 

By default, EasyKubuntu is in English.

If it detect Fr locales it uses the French translation (tested),else  it must use the English version (not tested).

>  Also, why do you have to uninstall the app after using it? I don't quite understand this, I guess.
you might want to remove it afterwards ;)

---

### Post by jbinc1 on 2005-09-18
Probably not a question for this thread, but here goes. How do I backup my whole system just in case I have a problem? Last time I tried EasyKubntu, it worked fine, but it changed all of my repositories. I restored my previous repositories from a backup copy, but then I started receiving errors from synaptic and apt-get. I ended up reinstalling kubuntu (I've become quite adept at the kubuntu install over the past few weeks). I have it back to where I started before Easykubuntu. It would be alot nicer to not have to go through the entire install again.:)

---

### Post by frodon on 2005-09-18
All is in this thread : [http://www.ubuntuforums.org/showthread.php?t=35087&page=1&pp=10](http://www.ubuntuforums.org/showthread.php?t=35087&page=1&pp=10).
Goos luck  ;-)

---

### Post by jbinc1 on 2005-09-18
Thanks guys, for all of your help! I really appreciate it.:razz:

---

### Post by sig_UVa on 2005-09-23
I installed and ran the newest version of Easy Kubuntu....where are all these wonderful apps it supposedly installed?  Specifically I need Java and Azureus.  Thanks!

---

