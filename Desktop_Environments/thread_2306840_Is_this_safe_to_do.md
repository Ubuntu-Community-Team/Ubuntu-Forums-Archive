---
title: "Is this safe to do?"
date: 2015-12-19
forum: Desktop Environments
---

### Post by DigiAngel on 2015-12-19
So I hate Nautilus as it stands now.  I need a dual-pan environment that I can mount/unmount smb shares.  I settled on Nemo for a long time [http://www.webupd8.org/2013/10/install-nemo-with-unity-patches-and.html]("http://www.webupd8.org/2013/10/install-nemo-with-unity-patches-and.html"), but it has this annoying bit where the columns are ALWAYS reset [https://github.com/linuxmint/nemo/issues/626]("https://github.com/linuxmint/nemo/issues/626").  Doesn't look like it's going to get a fix any time soon, so I heard tale of Caja, from Ubuntu Mate.  Now I'm running stock 14.04 with the Unity Desktop.  I tested on a VM from here [https://launchpad.net/~ubuntu-mate-dev/+archive/ubuntu/trusty-mate]("https://launchpad.net/~ubuntu-mate-dev/+archive/ubuntu/trusty-mate"):

    sudo apt-add-repository ppa:ubuntu-mate-dev/ppa
    sudo apt-add-repository ppa:ubuntu-mate-dev/trusty-mate
    sudo apt-get update
    sudo apt-get upgrade
    sudo apt-get install caja

This appears to have worked well....now when I start Caja all I have to do is hit Extra Pane and I'm in business.  When I did the install i did see an upgraded Compiz and other things.  Is this a safe thing to do?  I really don't want to hose up my sweet setup...thank you!

---

### Post by vanadium on 2015-12-19
This is not supported, because untested. So is this a safe thing to do? No, even if it might work.

---

### Post by grahammechanical on 2015-12-19
It is too late now. Don't you think?

The update to Compiz was part of the apt-get update/upgrade commands and not part of the apt-get install caja command. It is most likely that Compiz would have been updated anyway. And things are working as they should and you are able to work as you want to. That is the benefit of Free & Open Source Software & Linux.

Regards.

---

### Post by DigiAngel on 2015-12-19
Well...not too late as I made a snapshot before I did anything on the virtual machine ;)  Thanks for the responses all...I went with Sunflower....I miss the tree view, but it does what I need :)

---

