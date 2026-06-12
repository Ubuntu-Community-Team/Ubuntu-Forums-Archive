---
title: "me a wanta helpa"
date: 2011-05-25
forum: Desktop Environments
---

### Post by the-noob-mister on 2011-05-25
_**want help with some things!!!**_
 
**basicly i have no internet connection and i wanted to use the mediaplayer but i have no codec thingys to play my mp3's and wonderd does anyone know where i can find a extension pack wht the most common plugins**
 
**also i was wondering that button on the side bar that shows you 4 copys of your home screen is there anyway to change them so you can have 4 diffrent home screens for example one desktop for games one for documents one for games and one for folders if poss with diffrent backgrounds? if not then why dose it have that function?**
 
 
**_THANKS FROM CAVE RAVE DAVE (THE-NOOB-MISTER). _**:confused: ):P :-k :???: :-? :oops: [-o< :?:

---

### Post by codeslicer on 2011-05-25
Hmm... I'll take you seriously.

To play MP3s, get the Fluendo pack at: [http://www.fluendo.com/shop/product/fluendo-mp3-decoder/]("http://www.fluendo.com/shop/product/fluendo-mp3-decoder/")

As for your second question, workspaces just let you manage your desktop better. If you have a lot of windows open, you can switch between workspaces (it is your job to open apps in the workspaces you want them to be in). If you want different wallpapers, install [desktop effects configuration]("http://mirrors.ccs.neu.edu/ubuntu//pool/universe/c/compizconfig-settings-manager/compizconfig-settings-manager_0.9.4-0ubuntu2_all.deb"). Then follow this tutorial: [http://ubuntuguide.net/different-wallpapers-on-each-workspace-in-ubuntu]("http://ubuntuguide.net/different-wallpapers-on-each-workspace-in-ubuntu"). (Save any files to a flash drive and transfer them to your Ubuntu box.)

---

### Post by Petrolea on 2011-05-25
For common codecs, install restricted extras, for the rest of the question read the above post.

run: sudo apt-get install ubuntu-restricted-extras

---

### Post by 3Miro on 2011-05-25
Without the Internet,  you can use another Ubuntu machine to make a repository CD and then use the CD to install software on the Ubuntu machine that is not connected to the Internet. Without another Ubuntu machine, things get harder as you will have to download a .deb files one at a time and make sure you have satisfied all the required dependencies. It would be best if you can find a temporary connection just to make the installation.

Here is an official HowTo on packages and repositories:

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

------------------------

As for the Four "copies" of your "home screen", they are actually call "workspaces". By default, you have four of them and you have different programs running on every one of them. If you want separate wallpapers, then you have to install CCSM (compizconfig-settings-manager) and compiz-plugins-extra. Again it is best to use Internet connection and Synaptic Package Manager.

You need the following packages:
```

compizconfig-settings-manager
python-compizconfig
compiz-plugins-extra

```

After you have CCSM installed, go to the Wallpaper plugin and enable it. From the settings of the plugin, select the image files that you want to be the wallpapers. After enabling the wallpaper plugin, Hit Alt + F2 and type
```
gconf-editor
```
From the editor, find Apps -> Nautilus -> Preferences, then on the right find "show_desktop" and disable it. This will replace the default desktop background with the one from compiz and you will have the different wallpapers on every workspace.

---

### Post by the-noob-mister on 2011-05-26
> **codeslicer said:**
> Hmm... I'll take you seriously.

To play MP3s, get the Fluendo pack at: [http://www.fluendo.com/shop/product/fluendo-mp3-decoder/]("http://www.fluendo.com/shop/product/fluendo-mp3-decoder/")

As for your second question, workspaces just let you manage your desktop better. If you have a lot of windows open, you can switch between workspaces (it is your job to open apps in the workspaces you want them to be in). If you want different wallpapers, install [desktop effects configuration]("http://mirrors.ccs.neu.edu/ubuntu//pool/universe/c/compizconfig-settings-manager/compizconfig-settings-manager_0.9.4-0ubuntu2_all.deb"). Then follow this tutorial: [http://ubuntuguide.net/different-wallpapers-on-each-workspace-in-ubuntu]("http://ubuntuguide.net/different-wallpapers-on-each-workspace-in-ubuntu"). (Save any files to a flash drive and transfer them to your Ubuntu box.)

thanking you man.  for the second part but i don't rely want to sign up for the mp3 codec.

---

