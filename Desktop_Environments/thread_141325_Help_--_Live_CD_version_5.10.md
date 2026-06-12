---
title: "Help -- Live CD version 5.10"
date: 2006-03-08
forum: Desktop Environments
---

### Post by gworley on 2006-03-08
I just tried the live CD for version 5.10 and had the following problems:

1) No display on the laptop monitor -- display on the external monitor.
2) No network access -- Compaq laptop has Broadcom WLAN 54g W450 wireless adaptor.
3) everytime I tried to play an MP3 got an error.   Sound was playing on boot up.

I am just learning how to use Linux been using Windows for years but am tired of the bugs.


Thank you,

George Worley

---

### Post by MichaelZ on 2006-03-08
Hello,

May be this link could help you a bit:

[http://www.linux-laptop.net/](http://www.linux-laptop.net/)

It is also possible that you have compatibility problems. You should try to check if your hardware supports ubuntu.

Best wishes,
Michael

---

### Post by somerville32 on 2006-03-08
Hi George,

 I'm happy to hear that you are exploring linux but am sorry that you are experincing difficulties.

> 
1) No display on the laptop monitor -- display on the external monitor.


Are you saying that you aren't getting any picture on the built-in laptop monitor but you are getting output to your external monitor that is connected to the laptop?

> 
2) No network access -- Compaq laptop has Broadcom WLAN 54g W450 wireless adaptor.


Your wireless network card may require some extra configuration. 
[https://wiki.ubuntu.com/WiFiHowto](https://wiki.ubuntu.com/WiFiHowto)

> 
3) everytime I tried to play an MP3 got an error. Sound was playing on boot up.


Ubuntu does not ship with the MP3 codecs. If you live in a country where it is legal, you can enable MP3 playback in the Ubuntu and Kubuntu media players by  enabling the universe repository and installing the gstreamer0.8-mad package. Use your favorite package manager to install the package or type in a terminal:

```

sudo apt-get install  gstreamer0.8-mad

```

For more information, visit: [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)
To learn how to enable the universe repository, please visit: [https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

If you are interested in installing Ubuntu, you might want to look at Automatix - a tool created by the community to install and tweak common applications and settings. To learn more about installing Ubuntu, visit: [https://wiki.ubuntu.com/Installation](https://wiki.ubuntu.com/Installation)
For more information on Automatix, please visit: [http://ubuntuforums.org/forumdisplay.php?f=77](http://ubuntuforums.org/forumdisplay.php?f=77)

If you have any more questions, feel free to post here or visit the Ubuntu IRC channel: irc.freenode.net/#ubuntu

Also, if you require any more assitance with Ubuntu on your laptop, please include the laptop make and model in your post.

Thank you and best of luck,

Cody A.W. Somerville

---

