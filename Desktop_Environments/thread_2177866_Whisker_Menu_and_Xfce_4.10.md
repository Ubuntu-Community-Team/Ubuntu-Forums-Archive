---
title: "Whisker Menu and Xfce 4.10"
date: 2013-09-30
forum: Desktop Environments
---

### Post by Buntu Bunny on 2013-09-30
Has anyone had success installing Whisker Menu on Xfce 4.10? It was one of my favorite panel plugins in Xfce 4.8, but it is based on Ubuntu 12.04 libraries, which means it won't launch with Xfce 4.10. 

> 
**Plugin "Whisker Menu" unexpectedly left the panel, do you want to restart it?**
The plugin restarted more than once in the last 60 seconds. If you press Execute the panel will try to restart the plugin otherwise it will be permanently removed from the panel.

The only two solutions I can find are to compile it myself (way over my head), or, I found instructions on [this page]("http://linuxg.net/whisker-menu-1-1-0-comes-with-new-features-allowing-the-user-to-set-a-keyboard-shortcut-for-launching-the-menu/"), to install the lastest Whisker menu on Xubuntu with Xfce 4.10

```
$ sudo add-apt-repository ppa:landronimirc/xfce
$ sudo apt-get update
$ sudo apt-get install xfce4-whiskermenu-plugin
```

I tried this but still get the same error when trying to add it to my panel. Not only that, but the Screenshot plugin no longer works. :(

So, my question is, has anyone gotten Whisker Menu to run on Xfce 4.10? If so, how?

---

### Post by Frogs Hair on 2013-09-30
Are you using  XFCE session or Xubuntu ? . If it is the session it may have something to do with why it won't work . I have the 4.12 ppa installed so I can't try it via ppa but there is a .deb or apt install option  for only 13.04 with XFCE 4.10.

[http://www.ubuntuupdates.org/package/mint_import/olivia/import/base/xfce4-whiskermenu-plugin](http://www.ubuntuupdates.org/package/mint_import/olivia/import/base/xfce4-whiskermenu-plugin)

---

### Post by Buntu Bunny on 2013-09-30
> **Frogs Hair said:**
> Are you using  XFCE session or Xubuntu ? . If it is the session it may have something to do with why it won't work. 

Thanks for responding Frogs Hair. Actually, I'm using Xubuntu Session. I installed Xfce 4.08 on Ubuntu 12.04, and then had the choice of an Xfce session or a Xubuntu session. I recently updated Xfce to 4.10. I did wonder if installing it on Ubuntu had something to do with it.

> **Frogs Hair said:**
> I have the 4.12 ppa installed so I can't try it via ppa but there is a .deb or apt install option  for only 13.04 with XFCE 4.10.

[http://www.ubuntuupdates.org/package/mint_import/olivia/import/base/xfce4-whiskermenu-plugin](http://www.ubuntuupdates.org/package/mint_import/olivia/import/base/xfce4-whiskermenu-plugin)

Mint? But of course, Mint is based on Ubuntu. With 12.04, I doubt that would work for me, but I'm glad there are some fixes surfacing out there.  Whisker Menu is a nice little plugin and needs to evolve too.

---

### Post by Frogs Hair on 2013-10-01
According to Web Upd8 you have the correct ppa for 12.04 , but they seem to specify Xubuntu . I run only the XFCE session.  

[http://www.webupd8.org/2013/07/whisker-menu-update-brings-support-for.html](http://www.webupd8.org/2013/07/whisker-menu-update-brings-support-for.html)

---

### Post by Buntu Bunny on 2013-10-01
I tried my Xfce session, but still couldn't add Whisker Menu. I think it must have something to do with what you said earlier, about a clean Xubuntu install versus installing Xfce DE in Ubuntu. Oh well!

---

### Post by Buntu Bunny on 2013-11-03
Hurray! Whisker Menu is working in Xfce 4.10 after this morning's software update! Thank you to the Whisker Menu team!

---

