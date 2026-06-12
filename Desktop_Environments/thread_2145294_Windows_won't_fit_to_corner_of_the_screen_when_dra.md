---
title: "Windows won't fit to corner of the screen when dragged to edge of desktop; 12.04 LTS"
date: 2013-05-15
forum: Desktop Environments
---

### Post by aesoptheterrific on 2013-05-15
Hello all.

I recently installed a windows 7 and ubuntu 12.04LTS dual boot on an Acer Aspire 12.04LTS. Sometime between updating the OS and now, I have managed to break the unity component that allows me to fit a window to half the screen by dragging it to the corner of the ubuntu desktop. Before it was broken, dragging a window to the side would illuminate half the screen in an orange box, and the window would automatically resize to fit that half of the screen. I really like this feature, and would like to recover it for my system. Any idea how I could do that?

Thanks.

---

### Post by zombifier25 on 2013-05-15
Install ccsm first, it'll allow you to modify settings of Compiz.
```
sudo apt-get install compizconfig-settings-manager
```
Then open ccsm, navigate to the plugin "Grid" and check the settings in the tab "Edges". It should be obvious.

---

### Post by aesoptheterrific on 2013-05-15
That actually doesn't work. I tried that a few days ago to no avail. All the settings in there are default.

---

### Post by zombifier25 on 2013-05-15
There's one last thing you can try: reseting Compiz/Unity's settings.
```
unity --reset
```

---

### Post by aesoptheterrific on 2013-05-15
I tried that and it didn't work. :/

---

### Post by aesoptheterrific on 2013-05-31
This is not solved. Can anyone assist?

EDIT

Actually, I just fixed it somehow. 

I was trying to get steam to work on my ubuntu 12.04 LTS, so I followed the instructions at source 1 (regarding steam installation). I then went to source 2, and followed an answer which linked me to source 3. I then followed the instructions on link 3. I then looked at link 4 which confirmed link 3, and I also ran one of the lines there (sudo apt-get install bumblebee bumblebee-nvidia) to make sure that nvidia was somehow involved. After this, I ended up restarting, and I clicked on steam and it actually opened, and then I drug a window to the corner of the screen and that works now too. Hope this can help someone.


1. [http://steamcommunity.com/app/221410/discussions/0/864959809718795052/](http://steamcommunity.com/app/221410/discussions/0/864959809718795052/)
2. [http://askubuntu.com/questions/217792/drivers-not-listed-under-additional-drivers](http://askubuntu.com/questions/217792/drivers-not-listed-under-additional-drivers)
3. [https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)
4. [http://askubuntu.com/questions/171074/my-nvidia-geforce-610-in-asus-a43sd-doesnt-recognize-on-ubuntu-12-04](http://askubuntu.com/questions/171074/my-nvidia-geforce-610-in-asus-a43sd-doesnt-recognize-on-ubuntu-12-04)

---

