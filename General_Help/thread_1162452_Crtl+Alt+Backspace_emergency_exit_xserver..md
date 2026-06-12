---
title: "Crtl+Alt+Backspace emergency exit xserver."
date: 2009-05-17
forum: General Help
---

### Post by Wiebelhaus on 2009-05-17
I went through 5 how to's resulting in two screwed xorg's and one failed boot from various sites for something so stupidly simple. I should have just went to [www.ubuntugeek.com](www.ubuntugeek.com) first as it's always right and has the perfect how to's. I just wasted my time fooling with anywhere else.

I'm providing this for future users searching the board for it.

[Crtl+Alt+Backspace emergency exit xserver.]("http://www.ubuntugeek.com/howto-enable-ctrl-alt-backspace-in-ubuntu-jaunty.html")

And just in case it moves:

> By default Ctrl + Alt + BackSpace key combination in Ubuntu Jaunty was disabled.This shortcut key is used  to restart X.This tutorial will explain how to enable this key combunation.

Install the “dontzap” package using the following command

  ```
  sudo apt-get install dontzap
```

Open Terminal and type

    ```
sudo dontzap --enable
```

or

    ```
sudo dontzap --disable
```

Where “disable” means that Ctrl+Alt+Backspace restarts the xserver while “enable” means that it won’t.

Thanks [www.ubuntugeek.com](www.ubuntugeek.com) !

---

### Post by geirha on 2009-05-17
It's also mentioned in the release notes. [http://www.ubuntu.com/getubuntu/releasenotes/904#Ctrl-Alt-Backspace disabled by default in Xorg](http://www.ubuntu.com/getubuntu/releasenotes/904#Ctrl-Alt-Backspace disabled by default in Xorg)

---

### Post by Wiebelhaus on 2009-05-17
> **geirha said:**
> It's also mentioned in the release notes. [http://www.ubuntu.com/getubuntu/releasenotes/904#Ctrl-Alt-Backspace disabled by default in Xorg](http://www.ubuntu.com/getubuntu/releasenotes/904#Ctrl-Alt-Backspace disabled by default in Xorg)

Ahh thanks mate! , I didn't notice that.

---

