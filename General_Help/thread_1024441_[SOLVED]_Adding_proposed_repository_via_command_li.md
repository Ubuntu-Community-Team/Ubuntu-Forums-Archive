---
title: "[SOLVED] Adding proposed repository via command line"
date: 2008-12-29
forum: General Help
---

### Post by ace214 on 2008-12-29
So, I am making a script to automate some of the things I do when I first install a Ubuntu system. I used [this page]("https://help.ubuntu.com/community/Repositories/CommandLine") to enable and add some repositories and such.

It seems though that I need something special to add the proposed repo, because it is not already there to just uncomment. Any ideas on how to add it?

Just for fun, here's my script:
```
#!/bin/bash
sudo cp /etc/apt/sources.list /etc/apt/sources.list.orig
sudo sed -i -e "s/# deb/deb/g" /etc/apt/sources.list
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/intrepid.list -O /etc/apt/sources.list.d/winehq.list
sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list --output-document=/etc/apt/sources.list.d/medibuntu.list
sudo echo 'deb http://ppa.launchpad.net/webkit-team/ubuntu intrepid main' >> /etc/apt/sources.list.d/webkitppa.list
sudo echo 'deb http://ppa.launchpad.net/awn-testing/ubuntu intrepid main' >> /etc/apt/sources.list.d/awnppa.list

sudo apt-get update && sudo apt-get --assume-yes install medibuntu-keyring && sudo apt-get update
sudo apt-get --assume-yes install drapes build-essential ubuntu-restricted-extras community-themes midori awn-extras-applets-trunk awn-manager-trunk quodlibet-ext bluefish jedit gshutdown agave cheese gftp skype-static audacity ardour vlc sound-juicer compizconfig-settings-manager nautilus-wallpaper nautilus-gksu nautilus-open-terminal nautilus-image-converter libdvdcss2
sudo apt-get --assume-yes upgrade
```

The line that needs to be added to sources.list is "deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) intrepid-proposed restricted main multiverse universe"


SOLVED: Using echo line >> file.

---

