---
title: "Flash player for opera"
date: 2008-12-15
forum: General Help
---

### Post by charanpreethu on 2008-12-15
How to install flash player for opera??

Flash didnt work with mozilla.Check this thread to know abt flash player problem with mozilla.
[http://ubuntuforums.org/showthread.php?t=1009801&highlight=adobe+flash](http://ubuntuforums.org/showthread.php?t=1009801&highlight=adobe+flash)


Atleast tell me how to make the flash player to work with opera..

---

### Post by PocketDog on 2008-12-15
What worked for me is removing flashplugin-nonfree using Synaptic, and then downloading and installing the Flash 10 .deb installer (not tar.gz) manually. Get it from Adobe. You didn't say your OS version, I'm using 8.04 32bit.

---

### Post by charanpreethu on 2008-12-15
That also did not work for me... I am also using ubuntu 8.04

---

### Post by sandy8925 on 2008-12-16
I'm using Ubuntu 8.10 and flash works on Firefox but not on Opera.
Can anybody please help us ?

I installed flash by downloading the .deb for Ubuntu 8.04+ from the Adobe website.

---

### Post by Arup on 2008-12-16
Somehow Opera doesn't link the libflashplayer.so correctly when flash is installed. The solution is to remove the flash plugin as well as opera along with config file and then first install the flash plugin and then install Opera, make sure to a a total --purge remove rather than just remove. For x64 the x64 Flash plugin works fine in Opera and it directly picks it up from /usr/lib/mozilla/plugins

---

