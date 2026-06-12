---
title: "how to restore my graphic settings for D410"
date: 2007-07-24
forum: Dell  Ubuntu Support
---

### Post by koidenouvo on 2007-07-24
Hi, 

I launch some tweacking with little knowlege of unix commands and ubuntu at all and my graphics are working quite working but not as efficiently as before...

Change made following this site : [http://www.arsgeek.com/?p=1313](http://www.arsgeek.com/?p=1313)

Pascal

---

### Post by ajgreeny on 2007-07-24
This will depend on your graphics card and whether or not it can handle beryl properly.  More detail needed about your system please.

---

### Post by koidenouvo on 2007-07-24
Hi,

here are my syst spec. : 

Processor Speed: 1.86 GHz
RAM: 512 MB
Weight: 3.8 lb
Screen Size: 12.1 inches
Graphics Card: Intel Graphics Media Accelerator 900 GM 

The first few times I installed Ubuntu everything was working well such as desktop effects, at least one at a time like the cube.

But since I tried to install what I think is an extra component for graphics from this site : [http://www.arsgeek.com/?p=1313](http://www.arsgeek.com/?p=1313) my graphics have changed. First, the system would only boot under the command line after a few error message from a file named x-configure i think, the one I had to modify to set the extra component. So I went on another site, reconfigured the graphic file and gnome is working again but not fully as before. Like when the system starts, there is a messy graphic flash and then the gnome user interface comes.

There is this new item in the menu : Emerald Theme Manager that wasn't there before....

I think you got all the facts.

---

### Post by jephrandall on 2007-07-24
Did you install more than the emerald theme manager?  Perhaps new nvidia drivers?

I would run the following to reset up your xorg file...  

```
sudo dpkg-reconfigure xserver-xorg
```

Run through the prompts, most of which you'll accept the defaults.  Just make sure your graphics card is detected and you select the right resolution/refresh rate for your monitor.  You might also want to uninstall any new software and "start fresh".

I'm fairly new to this as well...but if there's one problem you'll have with Ubuntu, it's graphics support.

---

### Post by Dellfan on 2007-07-24
You need to verify that you are using the right video drivers. Once you have done that it likely will come down to settings in your xorg.conf file. I can run Beryl on a C400 which is significantly older/slower (both CPU and graphics card wise) than your D410, with many/most of the graphics effects enabled.

The "Emerald Theme Manger" is the default theme manager for Beryl. If you want to get back to using Gnome as a window manager, you can right click on the icon and select it as the default window manager.

What exactly are you trying to achieve?

---

