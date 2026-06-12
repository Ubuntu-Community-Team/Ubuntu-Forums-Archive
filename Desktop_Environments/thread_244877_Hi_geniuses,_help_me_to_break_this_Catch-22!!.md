---
title: "Hi geniuses, help me to break this Catch-22!!"
date: 2006-08-27
forum: Desktop Environments
---

### Post by redleafong on 2006-08-27
Hi all,

Finally I got the Ubuntu settled in my usb drive :D . But now I am jamed, because I can only access internet by wifi, however the wifi adapter, intel3945, is not recognized. :(  I would like to compile the driver but since I cant access internet I cant get the compiler stuffs installed... #-o Seems an infinite loop :confused: 

So, any idea? Thank you very much!!

---

### Post by aysiu on 2006-08-27
The compiler stuff like *build-essential*? It's on the Desktop CD *and* the Alternate CD: ```
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install build-essential
```

---

### Post by redleafong on 2006-08-27
Thanks aysiu! It works!!

However I found that the wifi is already supported. It is just not activiated!

Here comes another question. Since the firefox came with Ubuntu does not allow me to install the flash plugin (always fail after download complete) I wanna to get rid of this build in firefox. But when I tried to remove the firefox it told me there are some dependences, something like "ubuntu-desktop" that I dont want to touch...

So is it safe to remove the firefox as well as the "ubuntu-desktop" and other stuff? Thanks for your attentions!

---

### Post by aysiu on 2006-08-27
To install the Flash plugin...

1. Make sure you have extra repositories enabled:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

2. Paste this command in the terminal: ```
sudo aptitude update && sudo aptitude install flashplugin-nonfree
```

In general, it's not so bad to remove *ubuntu-desktop*--it's just a label (not a real package) that points to all the default packages in Ubuntu.

In this case, though, removing Firefox is a bad idea, as I've heard the way Gnome is built in Ubuntu, a lot is dependent on Firefox. If you must use the official Mozilla Firefox, install it on top of the Ubuntu one.

You can do it manually following these instructions:
[https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion)

Or you can have this script install it for you:
[http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Install_Firefox_1.5](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Install_Firefox_1.5)

---

### Post by redleafong on 2006-08-28
Thanks again aysiu!

Too bad... I removed firefox before seeing your reply so, now, the firefox messes up... My downloaded firefox couldn't work, and I tried to reinstall the default firefox package, it didnt work neither... The process just refuse to start up with out any trace info...

I will look into the given information now and if you have any suggestion to my situation, please share with me. Thanks.

---

### Post by aysiu on 2006-08-28
Can you try this? ```
killall firefox
sudo aptitude update
sudo aptitude install ubuntu-desktop
```

---

### Post by redleafong on 2006-08-28
I dont know... But when I typed "ps -ef | grep firefox" it seems that no firefox process is running. Moreover I have re-installed the ubuntu-desktop from the "Add/Remove", but still no effect...

Anyway I'll try your suggestion. Thanks!

---

### Post by redleafong on 2006-08-28
enn... no luck... it doesnt work...

Now I have to use Opera to come here... faint...

---

### Post by redleafong on 2006-08-28
Ok... I know what happen... All my fault actually...

I didnt remove my own firefox, whose path is piroir to the system's... Due to unknown reason my own firefox doesnt work...

Anyway the firefox is OK now... Thanks aysiu!!

---

