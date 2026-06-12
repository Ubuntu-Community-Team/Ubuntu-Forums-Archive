---
title: "remove KDE completely"
date: 2010-12-18
forum: Desktop Environments
---

### Post by c2tarun on 2010-12-18
I am using ubuntu 10.04 Lucid.
I installed KDE on my system, my splash screen changed, some new items introduced in my desktop.
But now i want to remove KDE ***pletely.
I tried to look into few threads, but they not getting exactly how to do it.
I installed kde using synaptic.
Can anyone please tell me how to remove it ***pletely, such that splash screen change and all the items get uninstalled.

---

### Post by c2tarun on 2010-12-18
***pletely means ***pletely
dont know y it happened :(

---

### Post by inobe on 2010-12-19
[http://psychocats.net/ubuntu/puregnomelucid](http://psychocats.net/ubuntu/puregnomelucid)
that's a good way.

side note, it's not recommended installing different desktop environments on a single os, you should try them on separate installations, these desktop environments are not accurate representations when installed side by side and changed in sessions, what you dislike about kubuntu could be solely related to how you installed it.

---

### Post by c2tarun on 2010-12-19
> **inobe said:**
> [http://psychocats.net/ubuntu/puregnomelucid](http://psychocats.net/ubuntu/puregnomelucid)
that's a good way.

side note, it's not recommended installing different desktop environments on a single os, you should try them on separate installations, these desktop environments are not accurate representations when installed side by side and changed in sessions, what you dislike about kubuntu could be solely related to how you installed it.
is there anyway of removing it via synaptic

---

### Post by 3Miro on 2010-12-19
> **c2tarun said:**
> is there anyway of removing it via synaptic

You can look at the components:
```
akonadi-server
akregator
amarok
```
they are listed in the command. You can remove them one by one from Synaptic. At the end, make sure to add ubuntu-desktop to ensure you did not remove anything important.

It is a tedious job, that is why they used the one-line command.

---

### Post by c2tarun on 2010-12-19
> **3Miro said:**
> You can look at the components:
```
akonadi-server
akregator
amarok
```they are listed in the command. You can remove them one by one from Synaptic. At the end, make sure to add ubuntu-desktop to ensure you did not remove anything important.

It is a tedious job, that is why they used the one-line command.


When i open synaptic in the left column i see an option of KDE Desktop Environment. Clicking on it is giving me a list of applications some installed and others no installed.
(look at the attachment )

---

### Post by 3Miro on 2010-12-19
Those are applications associated with the KDE environment specifically. Not all of them are installed, since not all of them are considered "default". You can start uninstalling them (if you are not using any of those), however, there is no guarantee that you will remove everything. I don't know if the splash screen is there for example.

If you remove those, you should cover most of KDE.

---

### Post by c2tarun on 2010-12-19
> **3Miro said:**
> Those are applications associated with the KDE environment specifically. Not all of them are installed, since not all of them are considered "default". You can start uninstalling them (if you are not using any of those), however, there is no guarantee that you will remove everything. I don't know if the splash screen is there for example.

If you remove those, you should cover most of KDE.

actually in the psychocat line in the first post in end they installed ubuntu-desktop. but i already have one, do i have to install it again??

---

### Post by inobe on 2010-12-19
> **c2tarun said:**
>  do i have to install it again??


yes unless you want to use a busted desktop !

you should have followed the link directions......

---

### Post by CB_Rider on 2011-02-15
I was successful using Synaptic's history. In the Synaptic Package Manager, there is a "Status" button in the bottom left. When you click on that button the content pane regroups the packages. In the status pane the KDE installs were all grouped together in one of the categories. I think that KDE was the last thing that I installed using Synaptic, so that may have made things unusually nice for me. The Desktop splash hadn't been changed back but this worked to fix that.

 sudo update-alternatives --config default.plymouth

cheers!

-Lee

---

