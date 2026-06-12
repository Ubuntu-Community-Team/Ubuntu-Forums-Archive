---
title: "Where's the Updater tool Xbuntu 22.04"
date: 2022-08-30
forum: Desktop Environments
---

### Post by mtbdrew on 2022-08-30
Just finished a new clean install of Xubuntu 22.04 but can't find any tool that runs the updates. Do I need to install this or am I really limited to running the command line method?

---

### Post by &amp;KyT$0P# on 2022-08-30
What tool would you like to use?

---

### Post by mtbdrew on 2022-08-30
Ubuntu, Kubuntu, Bungie all have built in Software Updater does Xbuntu not have this?

---

### Post by &amp;KyT$0P# on 2022-08-30
To install Software Updater you need to install the packages [FONT=Courier New]update-manager[/FONT] and [FONT=Courier New]python3-aptdaemon.gtk3widgets[/FONT]

---

### Post by mtbdrew on 2022-08-30
That works great thanks. I saw under Kubuntu you have to add a repository in order to get all the updates is there anything like that needed for Xbuntu?

---

### Post by tea for one on 2022-08-31
> **mtbdrew said:**
> Just finished a new clean install of Xubuntu 22.04 but can't find any tool that runs the updates. Do I need to install this or am I really limited to running the command line method?
Update-manager is already included. It is in the Xubuntu manifest.
[https://cdimage.ubuntu.com/xubuntu/releases/22.04/release/xubuntu-22.04.1-desktop-amd64.manifest](https://cdimage.ubuntu.com/xubuntu/releases/22.04/release/xubuntu-22.04.1-desktop-amd64.manifest)
You can can find it via the Whisker menu.
> I saw under Kubuntu you have to add a repository in order to get all the updates is there anything like that needed for Xbuntu? 
Which repo are you referring to? Codecs in restricted extras perhaps?

---

### Post by ajgreeny on 2022-08-31
It is always worth checking that both the universe and multiverse repos are enabled; I seem to remember that is not the case in all flavours but I'm not totally sure.

---

### Post by &amp;KyT$0P# on 2022-08-31
> **tea for one said:**
> Update-manager is already included. It is in the Xubuntu manifest.
[https://cdimage.ubuntu.com/xubuntu/releases/22.04/release/xubuntu-22.04.1-desktop-amd64.manifest](https://cdimage.ubuntu.com/xubuntu/releases/22.04/release/xubuntu-22.04.1-desktop-amd64.manifest)
You can can find it via the Whisker menu.

It's not included by default in the minimal install of Xubuntu.

---

