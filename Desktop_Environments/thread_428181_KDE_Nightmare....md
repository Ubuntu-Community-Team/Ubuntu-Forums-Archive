---
title: "KDE Nightmare..."
date: 2007-04-30
forum: Desktop Environments
---

### Post by GSF1200S on 2007-04-30
Weird stuff... I have 2 issues as of right now.

1) Whenever I boot into KDE, it opens evolution email, firefox, and a terminal window. Im guessing this is some kind of memory feature, as these are the programs I use alot, but I dont know where to change this in KDE (just started KDE recently).
2) My windows are all messed up, in the sense that they have no title bar. If I open Beryl, and change the window manager to metacity and back to Kwin, the windows look fine. Likewise, if I switch from Kwin to Beryl, Beryl rerenders the windows and everything works 5.0

I guess I could ask one other question. If I can get the 2 above listed issues fixed, id like to go pure KDE, with XFCE and Fluxbox as alternates... 

I started trying to do this, as I attempted to change the default window manager from GDM to KDM using:
sudo dpkg-reconfigure gdm

As soon as I rebooted all hell broke loose. My xwindow crashed, and even after I reverted to NV my wireless wouldnt work. I couldnt install either.. they just wouldnt work. So I did the command again, and went back to GDM. Reinstall video and wireless, and all is back to normal before I tried anything. Not so much a question as much as a little confusion.. What did I miss?

Any ideas on these questions?

---

### Post by CRIKEY on 2007-04-30
assuming your set up is the same as the default kubuntu

1) K-start-type-thing>system settings>advanced tab>session manager>start with empty session
(im not to sure about gdm to kde but that works with kde plain)

2) i dont understand what you are saying here are you trying to use metacity in kde if so the last i heard (which was about 2 years ago) you cant use metacity in kde without disabling some kde resources

as for the rest i can't help you much but i would advise you to try a pure kde (fresh kubuntu install) as all your problems seem to stem from having gnome and kde in the same install

---

### Post by GSF1200S on 2007-04-30
> **CRIKEY said:**
> assuming your set up is the same as the default kubuntu

1) K-start-type-thing>system settings>advanced tab>session manager>start with empty session
(im not to sure about gdm to kde but that works with kde plain)

2) i dont understand what you are saying here are you trying to use metacity in kde if so the last i heard (which was about 2 years ago) you cant use metacity in kde without disabling some kde resources

as for the rest i can't help you much but i would advise you to try a pure kde (fresh kubuntu install) as all your problems seem to stem from having gnome and kde in the same install

Agreed... I think im going to try and use a terminal to remove all GNOME libraries.. I know there is a few pages out there. Otherwise Id have to burn a Kubuntu CD.. unfortunately my dang DVDRAM drive wont burn (drives bad, not linux oriented).I havent had any conflict with XFCE or Fluxbox, but GNOME and KDE just dont seem to get along :)

I was only refering to Metacity as a means to fix the odd problem at bootup. Once I launch Beryl, it gives me the option to select my window manager. If I switch to metacity and back to Kwin, everything works fine. If I switch from Kwin to Beryl, everything works fine. If I just leave it at kwin, my windows have no borders and my title bar is missing.. No big deal really, as its easily resolved...

---

### Post by Nythain on 2007-04-30
gnome and kde get along great, as long as you dont try to use the others window managers... im assuming that trying to use kwin inside xfce would work just as horribly... i dont know why your kde is wanting to use metacity default instead of kwin, im not sure if removing all the gnome libraries is a highly recomended fix for this problem either... some of those libraries might be needed to run certain apps, even inside of kde...

---

### Post by mythstevie on 2007-04-30
Just my two cents and all, but I disagree. I am only just installing Ubuntu for the very first time, but...
I have been a fedora core user for many years (since fedora core 2)
This doesn't make me an expert at all but my experience is very related.
Just like your Ubuntu install, Fedora defaults to Gnome as its Desktop and Winmanager. I have ALWAYS installed KDE alongside and used it the majority of the time. (not out of strong feelings about it tho)
Even if I was on Kubuntu I would still install Gnome for occasional use, and its libraries!
While I have to have K3b and Amarok installed on all my computers, Gnome also has many indespensible packages. I want to post this in a timely manner, but I will post again with the instructions on changing the default desktop.

I mean I suppose there could be some issue, but I'll know soon as KDE will be my first install on Ubuntu!

As far as the Beryl thing goes,  make sure that you set the win manager to kwin in case of crash in beryl settings-manager, if that's applicable to ubuntu. I will check back in case you post.

---

### Post by GSF1200S on 2007-04-30
Learn new stuff everyday. I dont mind keeping GNOME on my box, just so long as KDE is default. As I listed in my first post, the whole default KDE didnt work out for me.. I must have missed something. Ive spent almost all of my time in Ubuntu on GNOME, so coming to KDE as well as the integration is foreign to me.. thanks for all the info...

---

### Post by CRIKEY on 2007-04-30
i actually remember having that same thing happen to me when i first installed beryl i cant remember how i fixed it though

---

### Post by Lord Landis on 2007-04-30
When you installed KDE, which package did you grab?  I installed KDE on my system via coding

sudo apt-get install kde-core

While installing, it asked if I wanted GDM or KDM to be the default window manager.  I choose KDM.  One reboot later, I selected KDE as my default session and everything has been fine.  You could also install the package 'kde', which would add in a lot more applications.  But anyway, if you had set it so that GDM was still the window manager, that could be why things are wonky for you (but I might also be wrong).

As for your session issue, do you close those programs before shutting down/rebooting/logging out?  I know that when I boot up all that comes up are the things I had open when I shut down - namely SuperKaramba, Amarok, and Firestarter.

---

### Post by TheWizzard on 2007-04-30
> **mythstevie said:**
> Just my two cents and all, but I disagree. I am only just installing Ubuntu for the very first time, but...
I have been a fedora core user for many years (since fedora core 2)
This doesn't make me an expert at all but my experience is very related.
Just like your Ubuntu install, Fedora defaults to Gnome as its Desktop and Winmanager. I have ALWAYS installed KDE alongside and used it the majority of the time. (not out of strong feelings about it tho)
Even if I was on Kubuntu I would still install Gnome for occasional use, and its libraries!
While I have to have K3b and Amarok installed on all my computers, Gnome also has many indespensible packages. I want to post this in a timely manner, but I will post again with the instructions on changing the default desktop.

I mean I suppose there could be some issue, but I'll know soon as KDE will be my first install on Ubuntu!

As far as the Beryl thing goes,  make sure that you set the win manager to kwin in case of crash in beryl settings-manager, if that's applicable to ubuntu. I will check back in case you post.


i disagree. gnome & kde don't work well together. if you want to use kde, just install the kubuntu cd. 
if you want to use both, make different partitions. 
there's more info on: 
[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

---

