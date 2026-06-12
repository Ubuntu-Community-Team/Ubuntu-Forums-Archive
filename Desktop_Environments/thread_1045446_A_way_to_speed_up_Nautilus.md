---
title: "A way to speed up Nautilus"
date: 2009-01-20
forum: Desktop Environments
---

### Post by LittleKoy on 2009-01-20
I've always found Nautilus a very slow fm, but since it's really great, imho much better than faster ones like Pcmanfm or Thunar, I've been sticking to it. 

I just realized that it shows, when you click on a folder, the count of items it contains. Now, wouldn't it slow down a lot? Especially when you have a lot of folders with loads of files inside. One could think that the value is probably cached, but the fs may be modified not only by Nautilus (for example by another fm, or by shell), and the cached values would become wrong. And I don't think the value is stored at lower levels, since I found this: [http://www.linux.org/docs/ldp/howto/Bash-Prompt-HOWTO/x700.html](http://www.linux.org/docs/ldp/howto/Bash-Prompt-HOWTO/x700.html)

Is there a way to disable this feature, since it has never been useful to me? I'm just guessing, maybe the performance slowdown is caused by other factors, maybe those amazing programmers, that are probably much better and more experienced than me, found a clever way to do it, but I see that Nautilus is very slow to show the content of a folder with many subfolders which have many files inside (and I have a 1600mhz Duron, so I can notice :D)

---

### Post by joshzam on 2009-02-21
First Open the Nautilus File Manager. Now go to Edit > Preferences. There, under Preview tab, you can modify the following settings to gain a small speed-up:

1. Turning off Thumbnails: By changing setting to never, you can turn off thumbnails of pictures that are shown by default in nautilus file manager. This setting can speed up nautilus significantly if you have a slow system and the directory you are browsing has a lot of high resolution images.

2. Turning off text in icons: This is another setting that can be turned off. Unnecessary resources are wasted in showing the content of text files as thumbnails. This can help speed up nautilus a bit.

3. Turning off count for number of Items: Now this can speed up things a bit in nautilus since some resources are used in counting the number of items present in a directory, however it won't show any significant improvement on new machines or even on half-decent machines. Try this only on very slow computers.

4. Turning off sound preview: If you have mpg123 or ogg321 installed, Nautilus provides a way of previewing sound files. Now this does consume some resources and hence can be switched off.

---

### Post by Vadi on 2009-02-21
Interested in this too, as nautilus seems to have slowed down while opening a folder for me. I thought it was a custom action I added at first, but it's not it.

In a similar position of not being able to switch either.

---

### Post by frankzen on 2009-02-22
I run Intrepid and noticed recently that Nautilus was coming up quickly but then taking 5-8 seconds to load my home directory. Normally it's almost instantaneous.

A few weeks ago I found a bunchof errors in .xsessions.errors file which looked like this:

gnome-session[5213]: atk-bridge-WARNING: AT_SPI_REGISTRY was not started at session startup.
gnome-session[5213]: atk-bridge-WARNING: IOR not set.
gnome-session[5213]: atk-bridge-WARNING: Could not locate registry
(metacity:5327): atk-bridge-WARNING **: AT_SPI_REGISTRY was not started at session startup.
(metacity:5327): atk-bridge-WARNING **: IOR not set.
(metacity:5327): atk-bridge-WARNING **: Could not locate registry
(gnome-panel:5337): atk-bridge-WARNING **: AT_SPI_REGISTRY was not started at session startup.
(gnome-panel:5337): atk-bridge-WARNING **: IOR not set.
(gnome-panel:5337): atk-bridge-WARNING **: Could not locate registry


and so on. 
So I went to my sessions and turned on atk.
That wiped out those atk errors....however that's when Nautilus started taking 5-8 secs to load directories.

I don 't know what atk is...but obviously it's still buggy.

YMMV

---

### Post by Vadi on 2009-02-22
ATK means Accessibility Toolkit, it's a feature for the screenreaders and whatnot.

---

### Post by frankzen on 2009-02-22
> **Vadi said:**
> ATK means Accessibility Toolkit, it's a feature for the screenreaders and whatnot.


Interesting....it fill my xsessions error log whenever it's not turned on...and I don't use screen readers or such. Turn it on and it drags down Nautilus.

---

