---
title: "Removing KDE 4 without removing KDE 3"
date: 2011-07-07
forum: Desktop Environments
---

### Post by Raevyn on 2011-07-07
I have Ubuntu running with GNOME and for fun I installed Kubuntu KDE 4. After that I installed Trinity and have fallen in love with it. But I am having an odd issue with the theming of various pop up appearing as KDE 4 rather than as Trinity. 

So my first question is, can I uninstall KDE 4 without removing anything from Trinity? 

The next question I have is, can I isolate the two environments better so I can avoid removal of kDE4?

---

### Post by ankspo71 on 2011-07-08
Hi,
I'm sure some of those KDE applications you use are KDE4 applications so they require running the newer KDE4 components and settings causing the KDE4 themes to be used. So before attempting to remove KDE4, see if you can log into the KDE4 desktop and choose the same theme style and window decoration that Trinity is using (if possible). Then log into into the Trinity desktop again to see if the problem continues. 

> So my first question is, can I uninstall KDE 4 without removing anything from Trinity? 

Possibly, but I suspect it could be risky. I don't know if KDE4 can be removed without breaking Trinity or removing some of your favorite applications, but you could try using the Kubuntu removal commands located here: [http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

Note 1: at the end of the command is a shorter second command to reinstall ubuntu-desktop, so you must replace that command with the command you used to install Trinty.
So replace "&& sudo apt-get install ubuntu-desktop" with "&&  sudo apt-get install kubuntu-default-settings-kde3 kubuntu-desktop-kde3" (which is the command shown here: [http://www.trinitydesktop.org/installation.php#ubuntu](http://www.trinitydesktop.org/installation.php#ubuntu) )

Note 2: The above psychocats/puregnome link is specific to Ubuntu 11.04, so if you are using an earlier version of Kubuntu/Ubuntu then click on the appropriate links at the top of that page.

Note 3: Make backups of all of your important files and settings just in case the removal command fails. If it fails then you might have to reinstall your Kubuntu (or install the trinity ISO) to fix it.

> The next question I have is, can I isolate the two environments better so I can avoid removal of kDE4?

From my experience, I found the only way to eliminate every possible conflict between different desktop environments is to install them on separate linux systems (ex: dual booting Kubuntu and Trinity). Here is the link to the Trinity ISO's if you would like to try dual booting. [http://apt.pearsoncomputing.net/cdimages/](http://apt.pearsoncomputing.net/cdimages/).

Hope this helps.

---

### Post by CWM on 2013-02-25
> **ankspo71 said:**
> Hi,
I'm sure some of those KDE applications you use are KDE4 applications so they require running the newer KDE4 components and settings causing the KDE4 themes to be used. So before attempting to remove KDE4, see if you can log into the KDE4 desktop and choose the same theme style and window decoration that Trinity is using (if possible). Then log into into the Trinity desktop again to see if the problem continues. 



Possibly, but I suspect it could be risky. I don't know if KDE4 can be removed without breaking Trinity or removing some of your favorite applications, but you could try using the Kubuntu removal commands located here: [http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

Note 1: at the end of the command is a shorter second command to reinstall ubuntu-desktop, so you must replace that command with the command you used to install Trinty.
So replace "&& sudo apt-get install ubuntu-desktop" with "&&  sudo apt-get install kubuntu-default-settings-kde3 kubuntu-desktop-kde3" (which is the command shown here: [http://www.trinitydesktop.org/installation.php#ubuntu](http://www.trinitydesktop.org/installation.php#ubuntu) )

Note 2: The above psychocats/puregnome link is specific to Ubuntu 11.04, so if you are using an earlier version of Kubuntu/Ubuntu then click on the appropriate links at the top of that page.

Note 3: Make backups of all of your important files and settings just in case the removal command fails. If it fails then you might have to reinstall your Kubuntu (or install the trinity ISO) to fix it.



From my experience, I found the only way to eliminate every possible conflict between different desktop environments is to install them on separate linux systems (ex: dual booting Kubuntu and Trinity). Here is the link to the Trinity ISO's if you would like to try dual booting. [http://apt.pearsoncomputing.net/cdimages/](http://apt.pearsoncomputing.net/cdimages/).

Hope this helps.


wow lubuntu user I have kinda fell in love with it :)

---

