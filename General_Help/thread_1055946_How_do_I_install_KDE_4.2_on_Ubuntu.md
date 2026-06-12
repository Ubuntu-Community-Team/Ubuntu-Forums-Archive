---
title: "How do I install KDE 4.2 on Ubuntu?"
date: 2009-01-31
forum: General Help
---

### Post by Universal344 on 2009-01-31
I recently heard about KDE 4.2 and want to give it a try.  I currently run Ubuntu 8.10 with GNOME.  I do not, however, want to get rid of GNOME.  I want to be able to start into either.  So how should I do this?  I found a guide on Kubuntu's site but I don't don't think it will work for Ubuntu.  Thanks for any help you can provide.

---

### Post by Universal344 on 2009-01-31
> **Universal344 said:**
> I recently heard about KDE 4.2 and want to give it a try.  I currently run Ubuntu 8.10 with GNOME.  I do not, however, want to get rid of GNOME.  I want to be able to start into either.  So how should I do this?  I found a guide on Kubuntu's site but I don't don't think it will work for Ubuntu.  Thanks for any help you can provide.

EDIT: I read the guide more carefully and I think it will work.  Could someone confirm that I can indeed install KDE4.2 using this guide:

[http://www.kubuntu.org/news/kde-4.2](http://www.kubuntu.org/news/kde-4.2)

Sorry for second post.  I wasn't paying attention, thought I hit edit not quote.

---

### Post by abn91c on 2009-01-31
> **Universal344 said:**
> EDIT: I read the guide more carefully and I think it will work.  Could someone confirm that I can indeed install KDE4.2 using this guide:

[http://www.kubuntu.org/news/kde-4.2](http://www.kubuntu.org/news/kde-4.2)

Sorry for second post.  I wasn't paying attention, thought I hit edit not quote.
Yes it will first do ```
sudo apt-get install kubuntu-desktop
``` then follow the guide to install the upgrade, just to be safe disable compiz in ubuntu before you begin and make sure you run the PUBKEY code

---

### Post by Universal344 on 2009-01-31
First, I have desktop effects enabled but I haven't installed compiz.  Should I disable desktop effects all together.  If so can I re-enable them once KDE 4.2 is installed?  Also what do you mean by running pubkey?

Also, in the guide it said uninstall any plamoids as they are not compatible.  How do I uninstall all plasmoids.

---

### Post by abn91c on 2009-01-31
> **Universal344 said:**
> First, I have desktop effects enabled but I haven't installed compiz.  Should I disable desktop effects all together.  If so can I re-enable them once KDE 4.2 is installed?  Also what do you mean by running pubkey?

Also, in the guide it said uninstall any plamoids as they are not compatible.  How do I uninstall all plasmoids.
disable desktop effects first then the run the code they give you in a terminal ```
gpg --keyserver keyserver.ubuntu.com --recv-keys 493B3065 && gpg --export -a 493B3065 | sudo apt-key add -
```
the plasmoid are if you have kubuntu already. when the desktpo installs it loads a couple by default just close them then run he upgrade, see my desktop for examples, I have a desktop folder, clock and weather

---

### Post by Universal344 on 2009-01-31
Ok so I should do the following:

1. disable desktop effects

2. add deb [http://ppa.launchpad.net/kubuntu-experimental/ubuntu](http://ppa.launchpad.net/kubuntu-experimental/ubuntu) intrepid main to my third party tab in software sources.

3. run gpg --keyserver keyserver.ubuntu.com --recv-keys 493B3065 && gpg --export -a 493B3065 | sudo apt-key add -

4. run sudo apt-get install kubuntu-desktop

5. run adept updater to get KDE 4.2 after closing widgets.

All I have to do is close widgets, not run a command to uninstall them?

---

### Post by abn91c on 2009-01-31
> **Universal344 said:**
> Ok so I should do the following:

1. disable desktop effects

2. add deb [http://ppa.launchpad.net/kubuntu-experimental/ubuntu](http://ppa.launchpad.net/kubuntu-experimental/ubuntu) intrepid main to my third party tab in software sources.

3. run gpg --keyserver keyserver.ubuntu.com --recv-keys 493B3065 && gpg --export -a 493B3065 | sudo apt-key add -

4. run sudo apt-get install kubuntu-desktop

5. run adept updater to get KDE 4.2 after closing widgets.

All I have to do is close widgets, not run a command to uninstall them?
Yes to all, I just closed the widgets and the install went fine for me. The plasmoids were removed during my set up. I have an old Dell Gx240 P4 1.6ghz with ati rge 128 video. So I did not get any errors, it took a while, my download was something like 240Mb, so it will depend what you have running in Ubuntu that needs to be removed/upgraded during the install.
Please note I ONLY had Kubuntu 8.10 running in my computer when I started.

---

### Post by Universal344 on 2009-01-31
Alright, thank you very much.  I will try this and see if it works.

---

### Post by abn91c on 2009-01-31
Good Luck :-)

---

