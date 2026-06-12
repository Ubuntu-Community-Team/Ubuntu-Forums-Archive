---
title: "Dual Wallpaper Changing"
date: 2016-02-26
forum: Desktop Environments
---

### Post by zathras1974 on 2016-02-26
Hello all. I'm currently running Ubuntu Gnome 15.10 with two 24" monitors. I have a rather large wallpaper collection and am attempting to switch wallpapers automatically on both screens with no luck. I have looked at both Variety and Wally, with no luck. Both programs DO change wallpaper, but display the same one on each screen. I am attempting to have them change independently of one another. 

Wallch just crashes as soon as I execute it. =(

Has anyone else successfully accomplished this? If so, what magic pixie dust did you use?

Thanks!

---

### Post by QDR06VV9 on 2016-02-26
This is how I do it..
Have you used nitrogen
To install it, run the following command in terminal:
```
sudo apt-get install nitrogen
```
Because nitrogen doesn't have a desktop file by default when it is installed, you need to run the following command from terminal to start it:

```
nitrogen
```

How to use it?
In it's Preferences, add your wallpaper folder, then at the bottom [...] select Screen 1, 2, etc., to set a different wallpaper for each monitor:

To be able to set a different wallpaper for each monitor, you must disable the file manager from handling the desktop. This means you'll no longer have folders, or icons on the desktop.
In GNOME / Unity, install GNOME Tweak Tool:
```
    sudo apt-get install gnome-tweak-tool
```

Then open GNOME Tweak Tool and on the Desktop section, set Have file manager handle the desktop to OFF.
And finally, to have the wallpapers restored each time you log in, add the following command:
```
nitrogen --restore
```
to your Startup Applications.

Source: [http://askubuntu.com/questions/390367/using-different-wallpapers-on-multiple-monitors-gnome-2-compiz](http://askubuntu.com/questions/390367/using-different-wallpapers-on-multiple-monitors-gnome-2-compiz)
Regards

---

### Post by QDR06VV9 on 2016-02-29
I can see that I misread your post..
You wanted something to change the wallpapers and specific intervals.. 
Variety is a good choice to check out..
[http://peterlevi.com/variety/how-to-install/](http://peterlevi.com/variety/how-to-install/)
[https://launchpad.net/~peterlevi/+archive/ubuntu/ppa](https://launchpad.net/~peterlevi/+archive/ubuntu/ppa)

---

