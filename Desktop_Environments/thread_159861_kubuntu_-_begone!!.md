---
title: "kubuntu - begone!!"
date: 2006-04-13
forum: Desktop Environments
---

### Post by sadjack on 2006-04-13
My laptop was purchased with Kubuntu unstalled. Since then I have installed Ubuntu and to be honest now much prefer the Gnome desktop. I have used Synaptics to remove Kubuntu and it tells me that I have successfully removed Kubuntu.

It may seem a small thing, but when I boot I still get a Kubuntu splash screen to start with. It changes during install to the brown Ubuntu.

How can I get rid of the initial splash of Kubuntu?

---

### Post by Sutekh on 2006-04-13
How did you remove kubuntu?  Did you use Synaptic to remove **kubuntu-desktop** or did you find and remove each and every package?

I think you should read this thread

[Ubuntu Forums - Howto Fully Uninstall the kubuntu-desktop meta-package](http://www.ubuntuforums.org/showthread.php?t=96048)

Try this first, it might fix the splash screen aswell.  If not, you can change it back to the brown Ubuntu one, using

```
sudo update-alternatives --config usplash-artwork.so
```
You get an output like
```
user@ubuntu:~$ sudo update-alternatives --config usplash-artwork.so
Password:

There are 3 alternatives which provide `usplash-artwork.so'.

  Selection    Alternative
-----------------------------------------------
*     1        /usr/lib/usplash/usplash-default.so
 +    2        /usr/lib/usplash/kubuntu-splash.so
      3        /usr/lib/usplash/xubuntu-splash.so

Press enter to keep the default[*], or type selection number:

```Then you can go ahead and change that splash screen

---

### Post by sadjack on 2006-04-14
Thanks for the suggestions. I have tried them both but I'm still left with the blue Kubuntu logo as the system starts to boot, but it changes to the brown theme at the logon screen.

---

### Post by schweitzereffect on 2006-04-14
you can reinstall the splash screen (i forgot its name, search for splash or splas screen) and it will say ubuntu again

---

