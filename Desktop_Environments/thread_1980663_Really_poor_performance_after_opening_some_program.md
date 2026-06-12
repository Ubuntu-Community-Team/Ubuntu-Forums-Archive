---
title: "Really poor performance after opening some programs (ATi HD4890 Gallium 0.4)"
date: 2012-05-15
forum: Desktop Environments
---

### Post by razor7 on 2012-05-15
Hi, i have installed Ubuntu 12.04 on my Intel Core i7 4GBram (DDR3 1333), Gigabyte H55M-USB3, ATi HD4890 and I got really poor performance on ALL effects of unity after opening a small JPG of 1mb with gnome image viewer!

The fact is that after opening some aplications (in this case the image viewer) the overall desktop performance is really poor (I mean 5 to 7 FPS!!!!!!!!!)

Is there something I can do to fix that?, I really dont want to switch to jollycloud or Fedora, but, man, this issues come since inmemorial thimes!

Remember, I have a u$s250 (at launch time) graphics card, so my hardware is not the problem.

Please, really need some good advise to solve this.

Thanks!

PS: ti fix it, I have to kill compiz

---

### Post by QIII on 2012-05-15
Do you have the fglrx driver installed?

---

### Post by razor7 on 2012-05-15
Not, al all!

---

### Post by QIII on 2012-05-15
Are you dead set on the Gallium driver?

---

### Post by razor7 on 2012-05-15
Well, the fglrx driver went really worse!

So I followed ubuntu official guide to get rid of it and reinstalled gallium, but if there is a better driver, just let me know and guide me to install it, I really want to try. This is the only bad thing think I have to say Ubuntu 12.04

---

### Post by codingman on 2012-05-15
doubt its the driver. Do the usual upgrade and update and then restart and see what happens.

---

### Post by razor7 on 2012-05-15
Well, that's what i do every single day, update sources, upgrade packages, but no luck, allways is a program that messes crashes compiz and I have to reboot.

At least, I realized that killing compiz solves the slowness problem withoutrestart, but again, it could be possible that some program messes it all again!

---

### Post by QIII on 2012-05-15
The fglrx driver works very well, as a matter of fact -- provided you install the one in the Ubuntu repository and do not attempt to compile it from source from the ATI website.

The difference between the Ubuntu version of the 12.4 driver (development version 8.960) and the 12.4 version released to the public after Ubuntu 12.04 was released (development version 8.961) is little more that a number, but enough to make it problematic for some people.

The 8.960 version works fine and full hardware acceleration is available for it in VA-API, which takes about 4 packages to install in Ubuntu.

The Gallium driver is a layer that attempts to generalize the process to make developing easier.  General tools are rarely better than specialty tools at a given task.

How did you install the fglrx driver?

---

### Post by razor7 on 2012-05-15
Oh, I see, I installed fglrx manually using AMDs one.

Please tell me, how may I install the BEST driver from ubuntu official repos?

Thanks!

---

### Post by QIII on 2012-05-15
Remember, the one in the repo **IS** the ATI driver.  The development version 8.960.  The difference is that a MOTU has prepackaged it as needed so that it installs correctly.

Uninstall and blacklist the Gallium driver.  Purge the fglrx driver if you haven't done so already.

Don't install the driver via the additional drivers method, since that has caused some users difficulty.

Use the terminal:

```
sudo apt-get install fglrx fglrx-amdcccle
```Some people say to use the fglrx-updates and fglrx-amdcccle-updates versions.  This has led to the inability to use the Catalyst Control Center on the six machines I have done that on.

Then BEFORE you shut down, create an initial xorg.conf, since one does not exist any longer in Ubuntu:

```
sudo aticonfig --initial
```Reboot.

After that, to get hardware acceleration via VA-API and the xvba backend:

```
sudo apt-get install vainfo xvba-va-driver libva-egl1 libva-glx1
```To test that hardware acceleration is working:

```
vainfo
```You should get something like this:

```
libva: VA-API version 0.32.0
Xlib:  extension "XFree86-DRI" missing on display ":0".
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/x86_64-linux-gnu/dri/fglrx_drv_video.so
libva: va_openDriver() returns 0
vainfo: VA-API version: 0.32 (libva 1.0.15)
vainfo: Driver version: Splitted-Desktop Systems XvBA backend for VA-API - 0.7.8
vainfo: Supported profile and entrypoints
      VAProfileH264High               :    VAEntrypointVLD
      VAProfileVC1Advanced            :    VAEntrypointVLD

```Then use the Catalyst Control Center to make your desired adjustments to your video.

Some users have reported that Catalyst won't open from the menu.  If it won't, just open it from the terminal:

```
sudo amdcccle
```

---

### Post by razor7 on 2012-05-15
Well, thats what I call  great support.

Please tel me how to > Uninstall and blacklist the Gallium driver. Purge the fglrx driver if you haven't done so already.

---

### Post by QIII on 2012-05-15
```
sudo apt-get remove --purge fglrx*
``````
sudo apt-get remove --purge glxinfo && sudo apt-get install glxinfo
```Check here for how to blacklist the Gallium driver.

[http://askubuntu.com/questions/36268/how-do-i-blacklist-the-gallium-ati-driver](http://askubuntu.com/questions/36268/how-do-i-blacklist-the-gallium-ati-driver)

Edit:  Just happened to realize that if you installed via AMD's website, you'll probably need to uninstall the driver following their instructions.

---

### Post by razor7 on 2012-05-15
Hi, on 
```
sudo apt-get remove --purge glxinfo && sudo apt-get install glxinfo
```

I get 

> E: Couldn't Find Package package glxinfo

---

### Post by QIII on 2012-05-15
You probably don't have it installed, so it quit on the first command.

Install glxinfo.  It is not required, but it reports some information that might be useful.

---

### Post by razor7 on 2012-05-15
OK, got it.

Now i get

> E: Couldn't find package xvba-va-driver

---

### Post by QIII on 2012-05-15
Do you have the multiverse repository enabled?

---

### Post by razor7 on 2012-05-15
Great!, that did the trick.

Any furter question will be back on this thread

---

### Post by QIII on 2012-05-15
Good.

Is your performance good now?  Or are you still experimenting with that?

---

### Post by razor7 on 2012-05-15
No, the performance is OK now.

I had had oppened the jpg of 1mb and now the sistems doesn't freezes.

Thanks!

---

### Post by razor7 on 2012-05-15
So far, not so good!

Now I'm facing great performance issues in Firefox (12.0) in plain html pages (like this one), nothing about flash or animations or videos.

When scrolling the page up and down the scrolling gets pretty slow!

---

### Post by QIII on 2012-05-15
If your video performance is otherwise good, it might be a good idea to start a new thread specifically for the Firefox issue.

---

### Post by razor7 on 2012-10-13
As this is a real shame for Ubuntu,I have filled a bug report. If you want to support this motion, please suscribe to this bug report [https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1066313](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1066313)

PS: Steam on Ubuntu, but warning, you won't be able to surf the web descently!

---

