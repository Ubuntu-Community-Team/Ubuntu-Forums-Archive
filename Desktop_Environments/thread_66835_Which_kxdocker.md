---
title: "Which kxdocker?"
date: 2005-09-18
forum: Desktop Environments
---

### Post by OttoDestruct on 2005-09-18
Maybe this sounds a bit dumb, but for the life of me, I can't understand what is what among the two dozen or so different links on the site for kxdocker as to what to download and install. Could anyone help?

---

### Post by Freddy on 2005-09-18
There are one or two precompiled packs for you to grab from their homepage, use those compiled for debian and they should work, I believe that the newest precompiled from their homepage is 0.33. 

My suggestion is you try to compile a new version yourself go down a bit on their page and download the 0.37 source and be sure to grab the resource pack to (themes and plugins), You need to have the devel files for KDE and X-Windows to be able to compile kxdocker but everything you need is in your repos.

If you have any problem just holler here in the KDE forum and I will answer as fast as I can.  /// Freddan

---

### Post by OttoDestruct on 2005-09-18
I'm not seeing the source. The only downloads that even have the number .37 I can see are under Gentoo and Redhat.

---

### Post by Freddy on 2005-09-18
You can find it at [http://www.xiaprojects.com/www/prodotti/kxdocker/main.php?action=download](http://www.xiaprojects.com/www/prodotti/kxdocker/main.php?action=download) scroll down, you will find it pretty low on that page, just at the right side in the redish area. You'll find the resource pack also on that page but higher up. Search and you will find. /// Freddan

---

### Post by OttoDestruct on 2005-09-18
When I go to grab the KDE devel files, its trying to install the entire KDE desktop... how can I just get the developer stuff?

---

### Post by Freddy on 2005-09-19
Hmm are you trying to compile it for Gnome ?

I installed the kde-devel files from repos without any problems but if you already have KDE installed, what's the problem? it only takes the packages it need to function.  Btw Kxdocker 0.38 came out earlier today.   /// Freddan

---

### Post by OttoDestruct on 2005-09-19
Yes I'm trying in gnome, and no I don't have KDE installed. Like I said though when I try the devel files, it tries to install the entire kubuntu-desktop stuff.

---

### Post by Freddy on 2005-09-19
Yeah I can understand that it will, you should be able to compile Kxdocker from 0.37 for Gnome but I don't know how, it's a KDE app and it's based on some of the devel files for KDE. Maybe if you can figure out which files and compile those by themself but that can be hard though, I would suggest that you should use something alike for Gnome instead or send a mail to the author of the program and ask him what to do.  ///  Freddan

---

### Post by drizek on 2005-09-19
a new version(.38) was released today, so you will want to get the sources for that.

also, since .37, kxdocker works in gnome.

---

### Post by Freddy on 2005-09-19
Yeah as I said in my post before, 0.37 and newer should be able to compile under Gnome but I've compiled 0.37 succesfully under KDE and it still use kde-devel and the kde-devel pack in our repos depends on kde-desktop. How to compile it under Gnome, I'm sorry but I do not know. In a standard Kubuntu desktop it only needs three develpacks, KDE, Xorg and X-Windows but it's the Kde devel that is the problem here. 

Have you tried to install Gnome's devel pack ? maybe it works.  /// Freddan

---

### Post by vassalle on 2005-09-19
probably a bit off topic.. im using kubuntu-breezy-preview. I have installed kde-devel, build-essential and loads of other stuff that i could gather from the forums. However, i cant compile anything, even kxdocker. I ran ./configure, make and sudo make install and theres no problems. The only problem is when i type, kxdocker for eg. nothing happens. ie seems like its not installed. any idea of whats going on ?

---

### Post by Freddy on 2005-09-20
You can find your kxdocker inside /usr/local/kde/bin, you can start it from there or make a symlink to /home/username/.kde/Autostart for a instant start with KDE.

I'm not sure of this but if you make a symlink of kxdocker inside /usr/local/kde/bin and put it in /usr/bin, I believe that you would be able to start it from run command or a console.  /// Freddan

---

### Post by vassalle on 2005-09-20
[QUOTE=Freddy]You can find your kxdocker inside /usr/local/kde/bin, you can start it from there or make a symlink to /home/username/.kde/Autostart for a instant start with KDE.

I'm not sure of this but if you make a symlink of kxdocker inside /usr/local/kde/bin and put it in /usr/bin, I believe that you would be able to start it from run command or a console.  /// Freddan[/QUOTE]
 thanks for the tip. is there a way for me to get around this ? like issuing a prefix or something when ./configure ?

---

### Post by Ptero-4 on 2005-09-20
[QUOTE=vassalle]thanks for the tip. is there a way for me to get around this ? like issuing a prefix or something when ./configure ?[/QUOTE]
 you can use --prefix=`kde-config --prefix` in the ./configure command. This tells ./configure to ask kde-config where kde is installed, and use whatever folder kde-config points to as install destination. By doing this you make sure that your KDE app will be installed where KDE expects it to be.

---

