---
title: "Possible Resolution Problems"
date: 2009-03-11
forum: General Help
---

### Post by hjehkj34h on 2009-03-11
I am running Ubuntu 8.10 on a Dell Dimension 8200, along with a [Dell E771a]("http://www.shopping.com/xPF-Dell-Dell-Monitor-E771A-CLR-17-SVGA-1280-1024-27DP-FST-16-VIEW-BLK") monitor, and I seem to have some screen resolution problems.  I currently have the resolution set to 1024 x 768, and I'm pretty sure that's what it was when I had Windows XP installed.  However, mostly when I'm viewing web pages, all of the contents are a lot smaller than what they were on XP.  Would there be any way to correct this?

In addition, would there happen to be a "lighter" version of Ubuntu that I could install?  My computer doesn't seem to handle this version particularly well.

Thanks in advance for any help!

---

### Post by taurus on 2009-03-11
For resolution, look in System -> Preferences -> Screen Resolution and see if you can set it to something else.

And for something that is lighter on system resources, try Xubuntu.

```
sudo apt-get update
sudo apt-get install xubuntu-desktop
```
You need to log out and at the GUI login screen, pick Xfce4 as your window manager from the Sessions.

But if you want to do a fresh install of Xubuntu, then download and burn it to a CD.

[http://www.xubuntu.org](http://www.xubuntu.org)

---

### Post by anlag on 2009-03-11
Try to go to

System -> Preferences -> Screen Resolution

and see what your screen resolution is actually set to. You should be able to change it there.

Xubuntu is a variant of Ubuntu which uses the Xfce desktop environment instead of Gnome, which should make it perform better, but also look a bit less fancy. Been meaning to try it myself, might do that if I buy a netbook soon...

edit// snap, and snap!

---

### Post by hjehkj34h on 2009-03-11
Thanks for the suggestion of Xubuntu!  I might have to try that.

The resolution is currently set to 1024 x 768 in the Preferences.  I set it to 832 x 624, and the size of the pages look almost exact to what they did in Windows.  However, it makes the application windows too big, and the screen becomes too small.  For example, on my Firefox Bookmarks, I cannot see the arrow to scroll down.

I have been using "Ctrl + or -" to make the pages bigger, but it causes any images on the screen to become distorted.

---

### Post by hjehkj34h on 2009-03-11
Another thing.  I was searching about this on the internet, and one thing that I read about the resolution is that it could be like this because I don't have a graphics driver installed.  I believe that it is an Nvidia, but I am not certain.  Would there be any way for me to check this?  Also, could this actually help the resolution at all?

Thanks again for any help!

---

### Post by anlag on 2009-03-11
> **hjehkj34h said:**
> Another thing.  I was searching about this on the internet, and one thing that I read about the resolution is that it could be like this because I don't have a graphics driver installed.  I believe that it is an Nvidia, but I am not certain.  Would there be any way for me to check this?  Also, could this actually help the resolution at all?

Thanks again for any help!

Not so sure about that... but you should make sure you have proper graphics drivers installed either way:

System -> Administration -> Hardware Drivers

Check that you're using one of the listed drivers. If not, mark, activate and follow instructions on-screen. You'll be prompted to restart. To test that it's working afterwards, you could check back to the same place, and run 'glxgears' at a terminal.

---

