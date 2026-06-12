---
title: "initial loading screen"
date: 2009-03-27
forum: Desktop Environments
---

### Post by Sojurner on 2009-03-27
How do i change the initial load screen.. where it either say ubuntu or kubuntu and has the progress bar? Whats this screen called and can i get custom ones for it.

I tried kubuntu for a while and uninstalled it and went back to ubuntu but the load screen still is blue with the kubuntu name on it.

---

### Post by tom56 on 2009-03-27
I'm not completely sure how to change it but it is called "usplash".

Try these:
[http://www.google.co.uk/search?source=ig&hl=en&rlz=&=&q=change+usplash&btnG=Google+Search&meta=lr%3D](http://www.google.co.uk/search?source=ig&hl=en&rlz=&=&q=change+usplash&btnG=Google+Search&meta=lr%3D)
[https://help.ubuntu.com/community/USplash](https://help.ubuntu.com/community/USplash)

---

### Post by Sarai the Geek on 2009-03-27
First, download the splash screen you want, gnome-look is a good place to look: [http://www.gnome-look.org/index.php?xcontentmode=160](http://www.gnome-look.org/index.php?xcontentmode=160). Make sure the description says it is for usplash.

Now that you have a new splash screen downloaded and extracted on your desktop, you need to install the Start up manager.

```
sudo apt-get install startupmanager
```Then in your System>Administration menu you will find "StartUp-Manager". Click the "appearance" tab and at the bottom of the window it says "usplash themes". Select "manage usplash themes" then add. In the navigation bar type /home/USERNAME/Desktop and select the .so file for your theme. 

Tada! New splash screen.

Good luck!

---

