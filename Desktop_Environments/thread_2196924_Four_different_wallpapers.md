---
title: "Four different wallpapers?"
date: 2014-01-01
forum: Desktop Environments
---

### Post by diverlonnie on 2014-01-01
):P Happy New Year!!! Welcome to my first post! Here's my first dumb question. With the Ubuntu 12.04 LTS install came Workspace Switcher. I really like the whole concept, layout, and function of four desk tops except I can't figure out how to put different wallpapers on the different desk tops. I would like a different background for my different desk tops themes/categories. Can I do this?:!: 

Please bear in mind this is posted in the "Dumber Than a Post" section so step by step instructions are greatly appreciated if this can in fact be done. :-P

---

### Post by Frogs Hair on 2014-01-01
Hello and Welcome

You can set different wallpapers for each work space, but the ability temporally  drag files or photos to the desktop will be lost when desktop handling by the file manager is disabled  . The method at the link requires installation of the Compiz Configuration Settings Manager(CCSM) and Plug-ins witch can break the desktop. Newer versions of this application display a warning when it is opened. If you want to take the risk do more research on methods _specific to 12.04_ because Unity, the CCSM and the plug-ins package  have changed since 12.04. Applying different themes for each work-space is not possible.  

[http://www.youtube.com/watch?v=FSqDk3I6v8c](http://www.youtube.com/watch?v=FSqDk3I6v8c)

---

### Post by monkeybrain20122 on 2014-01-01
According to this link you can still use different wall papers on different desktops in 13.04. Wallpaper plugin was removed from 12.10 but it comes back in 13.04 and 13.10 (so would work in 13.10 too)
[http://ubuntuguide.net/enable-different-wallpapers-for-each-workspace-in-ubuntu-13-04](http://ubuntuguide.net/enable-different-wallpapers-for-each-workspace-in-ubuntu-13-04)

I haven't tested it and I am not sure why anyone would want to do that. :)

---

### Post by grahammechanical on 2014-01-01
I have just tried it in Trusty Tahr (14.04 under development) and it works. Something to watch out for. When adding the new wallpapers do not have any blank lines in the panel where the path to the wallpaper image is entered otherwise you will get a black workspace. It took me a while to work out what I had done wrong.

Also, we can use the default wallpapers. For those who do not know they are in file system /usr/share/backgrounds. These are the steps as shown in the link from a previous post.

```
sudo apt-get install compizconfig-settings-manager compiz-plugins-extra
```

1) open CCSM
2) under Image Loading tick JPEG
3) under Utility tick Wallpaper
4) click the word Wallpaper
5) in the dialog click New
6) in the dialog browse to the location of the background image.

We need to have enabled workplaces in System Settings>Appearance>Behaviour

Regards.

---

### Post by 33Nicolas on 2014-01-15
I'm on the same wavelength as Diverlonnie.  I followed all the steps, but I don't see where I can allocate a different wallpaper for each workspace.  Am I in the right thread?  Thanks,

---

### Post by cariboo on 2014-01-16
Moved to Desktop Environments.

---

### Post by grahammechanical on 2014-01-16
We do not actually allocate wallpapers to different workspaces. If we have 4 workspaces we list 4 background images/wallpapers using the dialog box that appears when we click New. It is a small dialog and there is a panel called Image and we can enter the path to the image or we can click the folder icon on the right and we get a Open file dialog. We then click File System, then usr, then share, then backgrounds and then we will see all the default background images. Select one. And repeat until we have selected 4.

If we have other images files that we want to use instead, then browse to the location of those image files.

Regards.

---

### Post by 33Nicolas on 2014-01-16
Thank you both.  I'll try [COLOR=#000000]Desktop Environments and the instructions.[/COLOR]

---

