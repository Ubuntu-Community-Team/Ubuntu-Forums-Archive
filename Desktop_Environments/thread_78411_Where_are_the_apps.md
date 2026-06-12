---
title: "Where are the apps?"
date: 2005-10-18
forum: Desktop Environments
---

### Post by nixhead on 2005-10-18
Hello everyone. I am new to Kubuntu, having just now installed 5.10. I am pleased with it so far, since the installation and setup went very well. I did have to uninstall quite a bit from adept. Although it has been years since I have used a binary distro, I knew to expect this from previous experience with binary distros.

It would be more accurate to say I run KDE than to say I run Linux. KDE is my favorite environment besting all others, including Windows, Gnome, OSX, take your pic. One of the reasons I chose Kubuntu was because it is possible to install individual KDE apps, such as kopete, without having to install monolithic KDE packages such as kdenetwork. I don't want my system and especially my menus to be overloaded with useless apps, forcing me to read 20 entries on a submenu to find the app I need. 

Kubuntu seems to have a nice slimmed down default install of KDE apps. However, it is lacking in some areas. I require the following must-have apps, which are not to be found in the Kubuntu repositories:

kuickshow
apollon
knode
opera
either of qtorrent or ktorrent
kdf
guarddog
qtparted
filelight
bibletime
privoxy
gift
gift-fasttrack
gift-gnutella
gift-openft
gift-ares

I would have no problems installing any of these from source. Given that Kubuntu is a binary distro, I think it would be asking a bit much to have to install basic desktop apps, such as knode, from source, rather than install a binary. 

Do any Kubuntu repositores exist which include the above apps? I know it is possible to add Debian unstable repositories. I would prefer to not include anything from Debian unstable. There is a reason it is called unstable after all. I am especially concerned that if I add Debian unstable repositories, I would be forced to install packages such as kdenetwork, rather than individual apps such as knode.

Any help, ideas or suggestions would be greatly appreciated.

---

### Post by gingermark on 2005-10-18
You'll need to activate the Universe repository in your source.list file (located in /etc/apt - or do it in Adept) and you will find many of the apps you are looking for.

As far as Opera goes, go to the website and download the Ubuntu ".deb" file for it. Open up Konsole, CD to the folder where you saved the .deb and type "sudo dpkg -i Opera" and then hit tab to fill in the rest of the filename (or, to be more correct "sudo dpkg -i [filename]") and hit enter.

---

### Post by nixhead on 2005-10-18
[QUOTE=gingermark]You'll need to activate the Universe repository in your source.list file (located in /etc/apt - or do it in Adept) and you will find many of the apps you are looking for.[/QUOTE]

Thanks for the information. I found the Ubuntu guide which answers some of these questions, even though it appears to be written for 5.04. 

[QUOTE=gingermark]As far as Opera goes, go to the website and download the Ubuntu ".deb" file for it. Open up Konsole, CD to the folder where you saved the .deb and type "sudo dpkg -i Opera" and then hit tab to fill in the rest of the filename (or, to be more correct "sudo dpkg -i [filename]") and hit enter.[/QUOTE]

I had actually done this previously on Debian stable. The problem was dpkg did not detect the Opera dependency of motif or libmotif or whatever it is called. It was easily corrected but I wasn't sure if Kubuntu would detect the motif dependency or not.

The only things I am now missing since adding the multiverse are gift-fasttrack, gift-openft, gift-gnutella, gift-ares and j2se. The Ubuntu Guide provides instructions for installing sun-j2re1.5, which doesn't appear to exist in the 5.10 multiverse. Do more updated instructions exist to install sun-j2re1.5? If I remember correctly, it was possible to build a deb for it in Debian stable. Should I follow those same instructions for Kubuntu?

Also, it appears that the various gift plugins will need to be built from source. Would /usr be the appropriate --prefix option to configure? And would I need to install any additional foo-dev packages in order to build the gift plugins? If so, what foo-dev packages would I need?

Thanks so much for the tips which worked exactly as stated, except for these last few apps.

---

