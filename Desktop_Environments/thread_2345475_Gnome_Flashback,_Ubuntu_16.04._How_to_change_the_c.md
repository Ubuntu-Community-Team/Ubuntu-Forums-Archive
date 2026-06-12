---
title: "Gnome Flashback, Ubuntu 16.04. How to change the color of the top window bar?"
date: 2016-12-04
forum: Desktop Environments
---

### Post by richterbg on 2016-12-04
I'm using Ubuntu 16.04 LTS with Gnome Flashback. The theme is Radiance. I prefer things to be in light colors. However, for the love of life, I can't change the decoration of the window to match the Radiance theme. The top window bar stays dark. The Unity Tweak Tool and Gnome Tweak Tool do not seem to make any difference.

I'm providing a link to the image:

[http://imgur.com/a/lTO3e](http://imgur.com/a/lTO3e)

[IMG]http://i.imgur.com/zSsyHXM.png?1[/IMG]

Any suggestions will be greatly appreciated!

---

### Post by Frogs Hair on 2016-12-06
You might try the following though the command may be dated for 16.04. 


```
gsettings set org.gnome.desktop.wm.preferences theme radiance
```

---

### Post by muktupavels on 2017-01-08
If you use metacity session:

```
gsettings set org.gnome.metacity theme Radiance
```

[http://askubuntu.com/questions/785205/cant-use-metacity-themes-in-gnome-flashback-session-metacity-ubuntu-16-04](http://askubuntu.com/questions/785205/cant-use-metacity-themes-in-gnome-flashback-session-metacity-ubuntu-16-04)

---

