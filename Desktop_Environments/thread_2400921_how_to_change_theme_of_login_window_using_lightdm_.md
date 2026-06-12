---
title: "how to change theme of login window using lightdm - ubuntu 18.04"
date: 2018-09-11
forum: Desktop Environments
---

### Post by Claus7 on 2018-09-11
Hello,

I wanted to change the background of the login screen in ubuntu 18.04 using gnome flashback (compiz). 

I had upgraded from 16.04 and at the very beginning I had some problems with gdm3, which I purged and substituted with lightdm. The default greeter of lightdm is unity-greeter, which shows the beaver in the login screen. Nice as it is, yet I wanted at some point to change the wallpaper of the login window.
I was not able to change the image while using the unity-greeter.

I was also able to find some videos, yet the options provided were not exactly the ones needed from my ubu box. So here, I summarize the steps I followed in order to make the change.

The steps are:
1) install lightdm-settings AND slick-greeter (the latter, even not a dependency of the former, is needed for the former to work)
2) run the command: lightdm-settings
(it will require password) and make the appropriate changes (e.g. change wallpaper)
3) in /etc/lightdm/ **create** the file lightdm.conf and add
[Seat:*]
greeter-session=slick-greeter

(it can be reverted back by writing unity-greeter in place of slick-greeter)
4) restart is required!

In order to see which configurations are in place issue the command:
lightdm --show-config

I did not use lightdm-gtk-settings and this package was not installed in my box.

Regards!

---

### Post by james-dickson-f on 2018-12-28
Very helpful thanks. Recently upgraded to 18.04 with unity desktop. These steps worked perfectly, thanks Claus :)

---

