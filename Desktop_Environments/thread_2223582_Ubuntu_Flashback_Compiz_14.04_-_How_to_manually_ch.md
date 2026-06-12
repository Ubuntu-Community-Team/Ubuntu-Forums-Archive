---
title: "Ubuntu Flashback Compiz 14.04 - How to manually change icon beside Application menu"
date: 2014-05-11
forum: Desktop Environments
---

### Post by MaCkMeiN on 2014-05-11
I installed this gnome flashback session and login using gnome flashback compiz. I installed moka & faba icon themes which I really like. I realized that when using this theme, I get no icon for the icon beside the Application menu.; usually the Ubuntu icon. Just this one icon the in the whole system.  I just need to know how to manually change the icon beside the Application menu, usually ubuntu logo icon. (refer to picture)

[IMG]http://a.disquscdn.com/uploads/mediaembed/images/1010/8803/original.jpg[/IMG]


I try to rename and copy icon to moka and faba icons folder but still it won't work. This is the only thing that is missing with this icon theme. I don't know whether that particular icon use gnome-main-menu.png or start-here.png. I tried both but still no luck.:(

Thanks guys.

---

### Post by grumblebum2 on 2014-05-12
I do not get an icon next to the menubar applet?
Does clicking on the icon do anything?

---

### Post by MaCkMeiN on 2014-05-12
It's been there when I first install gnome flashback. I don't know why yours don't have icon.

---

### Post by grumblebum2 on 2014-05-12
Ye sorry, it's there in my test account with everything default.
If it's of any help, when using the ubuntu-mono-dark default icons the panel icon appears to come from 
/usr/share/icons/ubuntu-mono-dark/apps/22/**distributor-logo**.svg
Another icon search term would be **start-here**

---

### Post by Frogs Hair on 2014-05-12
My experience with Moka icons is that in recent versions the panel icons don't display properly on either of my computers and fortunately I had created an archive of an older set which included  moka-icon-theme-extras and moka-icon-theme-symbolic. The PPA for this version is no longer available. I don't how many people this affects or if the author is aware of it ,but I found an Ask Ubuntu question for the problem in 13.10. When transferring this older set to my other computer it worked fine. ?? The PPA I used didn't include the color variants for the folders. 

[https://bugs.launchpad.net/moka-icon-theme](https://bugs.launchpad.net/moka-icon-theme)

---

### Post by MaCkMeiN on 2014-05-13
> **grumblebum2 said:**
> Ye sorry, it's there in my test account with everything default.
If it's of any help, when using the ubuntu-mono-dark default icons the panel icon appears to come from 
/usr/share/icons/ubuntu-mono-dark/apps/22/**distributor-logo**.svg
Another icon search term would be **start-here**

I tried to copy the distributor-logo-ubuntu.png form folder places and put into apps folder and rename it to distributor-logo.png but still the icon won't show. :(

---

### Post by grumblebum2 on 2014-05-14
I tried a few things and I can't determine where the icon is coming from.
I thought it might be using the **start-here.svg** as set in alternatives but changing from ubuntu-logo to debian-swirl changes
the icon for the "main menu" but not the "menu bar" applet.

If you want to test, run.....
```
sudo update-alternatives --config start-here.svg
```

---

### Post by grumblebum2 on 2014-05-14
Bit more info:
Found the icon doesn't show when using my custom gtk themes which is why I was only seeing in my test user account which uses the ambiance theme.

When using ambiance I can turn off the showing of the icon by editing **/usr/share/themes/Ambiance/gtk-3.0/apps/gnome-panel.css**

```
gksudo gedit /usr/share/themes/Ambiance/gtk-3.0/apps/gnome-panel.css
```

Changing line #40 ...
    ```
-PanelMenuBar-icon-visible: **true**;
```
to
    ```
-PanelMenuBar-icon-visible: **false**;
```

---

### Post by MaCkMeiN on 2014-05-14
Thanks a lot man! I turn off the icon just like what you showed. Log out and log in back again, now the annoying little icon is not there anymore. Thanks a lot @[**[COLOR=#000000]grumblebum2[/COLOR]**]("http://ubuntuforums.org/member.php?u=1910493")

---

### Post by Frogs Hair on 2014-05-14
FYI [https://github.com/snwh/moka-icon-theme/issues/97](https://github.com/snwh/moka-icon-theme/issues/97)

---

