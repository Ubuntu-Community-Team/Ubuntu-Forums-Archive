---
title: "How to upgrade to kde 3.5.1?"
date: 2006-02-01
forum: Desktop Environments
---

### Post by zeltak on 2006-02-01
hi!

i think this would interst alot of new users so im posting it in a new thread. i have installed kubuntu and as i understand form other threads kde 3.5.1 fixes alot of eye candy issues. i looked at kubuntu.org for instructions and searched the forums yet as a very very new Linux user i really cant see how to upgrade. i added the deb [http://kubuntu.org/packages/kde351](http://kubuntu.org/packages/kde351) breezy main to my synaptic manager but i dont know which file to download, there isnt a kde 3.5.1 upgrade file there:) (would be to simple).. can anyone instruct me on how to upgrade

Thx alot in advance!!

Zeltak

---

### Post by NeoChaosX on 2006-02-01
In Konsole, do **sudo apt-get update**, then **sudo apt-get dist-upgrade**. That should get your KDE 3.5.1.

---

### Post by devipl on 2006-02-01
Do you know if it fix problem with oowriter2? try to clik on hyperlink inside wiriter it will open konqueror and broke both application,

regards

---

### Post by l.capriotti on 2006-02-01
it should be as easy as typing:

sudo apt-get update
sudo apt-get dist-upgrade

and you should be up and running after logging out and in again. 
I had a flawless upgrade but, as usual, YMMV....

Cheers
Luigi

---

### Post by NeoChaosX on 2006-02-01
[QUOTE=devipl]Do you know if it fix problem with oowriter2? try to clik on hyperlink inside wiriter it will open konqueror and broke both application,

regards[/QUOTE]
This seems to be a common problem for the changes in the kio_slaves in KDE 3.5.x. The problem you're describing can be fixed [here](http://ubuntuforums.org/showthread.php?p=537216).

---

### Post by raggamuffin on 2006-02-01
there's no need for a "sudo apt-get **dist**-update" to upgrade KDE...(as you're not upgrading the whole distro, just the desktop enviornment)...

just add the following line to your /etc/apt/sources.list ...

```
deb http://kubuntu.org/packages/kde351 breezy main
```

and then...

```
sudo apt-get update &&sudo apt-get upgrade
```

---

### Post by Sokraates on 2006-02-02
Just be carefull, what you install. Some metapackages have been updated to install new stuff.

E.g. zeroconf is now included in kdenetwork (or was it networking?). Problem was, that it screwed up my network-connection by automatically assigning a random IP to my NIC, which uses a static IP for internet-access. Strangely, the /etc/network/interfaces was left as it was before. Had to remove the package to make it work (DHCP is no option in my case).

Just make shure to have a list of all the packages installed, so that you know what causes the problems you might experience.

As for installing KDE 3.5.1: after adding the repo in synaptic just update and install. All installed packages including metapackages will be updated.

---

