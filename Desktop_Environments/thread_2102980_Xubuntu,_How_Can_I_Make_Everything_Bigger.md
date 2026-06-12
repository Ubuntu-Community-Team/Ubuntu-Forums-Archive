---
title: "Xubuntu, How Can I Make Everything Bigger?"
date: 2013-01-08
forum: Desktop Environments
---

### Post by jancellor on 2013-01-08
Hello

I am running Xubuntu 12.10 on top of a Window 7 VirtualBox. My native resolution is 1366x768 on a 13 inch screen. Everything is too small for my eyes. I simply want to make everything bigger, and not just the fonts. This sounds simple to me but I have searched for hours and been unsuccessful.

Is this possible at all? I tried to use xrandr. Is it right to try to set something in X as opposed to Xfce? And if so is xrandr the right tool?

In any case it did not work. I can do "xrandr -s 1024x768" to change the resolution, but if I do "xrandr --dpi 120" or "xrandr --dpi 120 1366x768" nothing happens and nothing is output on the console. The output of "xrandr -q" is as below. Could the problem be VirutalBox related?

   1366x768       60.0*+
   1600x1200      60.0  
   1440x1050      60.0  
   1280x960       60.0  
   1024x768       60.0  
   800x600        60.0  
   640x480        60.0  

Many thanks for any help.

James

---

### Post by sudodus on 2013-01-08
You can change the screen resolution with xrandr like you tried: xrandr -s 1024x768, but you seem to have only one wide screen resolution (and that is your native resolution). Instead I suggest that you ***select larger fonts*** in your application programs. Often it can be set in the Preferences menu. In some programs, for example web browsers, you can increase it with the hotkey combination ***ctrl +*** and decrease it with ***ctrl -***

I hope this can help :-)

*Edit*: Everything will be bigger with
```
xrandr -s 800x600
``` but you won't use all the screen (or it will be distorted).

---

### Post by jancellor on 2013-01-09
Thanks for your reply.

I do not want just to change the font size. I need everything to be bigger, including title bars, panels, buttons, etc.

Doing "xrandr -s 800x600" does not make everything bigger. It simply uses only 800x600 physical pixels.

I think you imply that it is the resolution (eg 1366x768) rather than the dpi (eg 96) setting that would affect the size of buttons, etc. I can see how this would make sense if those 800x600 pixels were stretched to fit the entire screen, but that is not what happens (for me); there is a black border of unused pixels.

Any more ideas anyone? And is xrandr (or the display server) definitely the place to make changes to achieve what I want?

Many thanks

James

---

### Post by blackbird34 on 2013-01-09
You can edit the size of all OS elements in one go with DConf Editor, a graphical editor for a whole pile of system settings.

It is available in the repositories, so you can type in the following command or else get it from the Ubuntu Software Centre.
```
sudo apt-get install dconf-tools
```

Once you've got it go to the "org" section in the left hand margin then look for: gnome > desktop > interface > text scaling factor.

Default value is 1.0, if you make it bigger (say 1.2 or even 1.3) everything will get bigger, and if you make it smaller (say 0.9) everything will get smaller. Don't put it at 5 straight away or everything will be unusable :D

---

### Post by sudodus on 2013-01-10
> **jancellor said:**
> Thanks for your reply.

I do not want just to change the font size. I need everything to be bigger, including title bars, panels, buttons, etc.

Doing "xrandr -s 800x600" does not make everything bigger. It simply uses only 800x600 physical pixels.

I think you imply that it is the resolution (eg 1366x768) rather than the dpi (eg 96) setting that would affect the size of buttons, etc. I can see how this would make sense if those 800x600 pixels were stretched to fit the entire screen, but that is not what happens (for me); there is a black border of unused pixels.

Any more ideas anyone? And is xrandr (or the display server) definitely the place to make changes to achieve what I want?

Many thanks

James
On my computers the whole height will be used when 800x600 is selected (the pixel values will be interpolated). But on a wide screen there will be black borders at the sides, because only part of the width is used. But since that won't work for you, I agree that you need something else.

Did I get it correctly, that you run Xubuntu in VirtualBox, and that Windows 7 is the host operating system?

I think you can try two things.

- I thought you were using the whole screen for VirtualBox (not only a window in Windows). Try that (if you haven't)!

- Change the resolution of the screen in the hosting Windows 7 system! (At least it used to be done like this: right-click on the desktop background ...) ... and Xubuntu should inherit that resolution.

---

### Post by sudodus on 2013-01-10
> **blackbird34 said:**
> You can edit the size of all OS elements in one go with DConf Editor, a graphical editor for a whole pile of system settings.

It is available in the repositories, so you can type in the following command or else get it from the Ubuntu Software Centre.
```
sudo apt-get install dconf-tools
```

Once you've got it go to the "org" section in the left hand margin then look for: gnome > desktop > interface > text scaling factor.

Default value is 1.0, if you make it bigger (say 1.2 or even 1.3) everything will get bigger, and if you make it smaller (say 0.9) everything will get smaller. Don't put it at 5 straight away or everything will be unusable :D

This looks like a good tool :-)

---

### Post by jancellor on 2013-01-10
blackbird, are you aware I'm asking about Xubuntu not Ubuntu? Everything I can find seems to indicate this is exclusively for GNOME and not Xfce.

sudodus, full screen VirtualBox with Windows 7 host and Xubuntu guest. It sounds to me like what you are suggesting would be "tricking" the system into scaling an 800x600 image onto a 1366x768 one, which would make the fonts blurry (as well as not in proportion, as you mention).

---

### Post by drawkcab on 2013-01-10
On my htpc I run Gnome Shell instead of xfce precisely because it's so easy to scale the desktop to the point where it's functional (e.g. I'm typing this on my television while laying on the couch across the room.)

Because Gnome Shell is so sluggish, I would love to be able to run xfce but I've never been able to get it to scale correctly.  If there is some way to globally scale xfce, I'm all ears.

---

### Post by sudodus on 2013-01-11
> **jancellor said:**
> blackbird, are you aware I'm asking about Xubuntu not Ubuntu? Everything I can find seems to indicate this is exclusively for GNOME and not Xfce.

sudodus, full screen VirtualBox with Windows 7 host and Xubuntu guest. It sounds to me like what you are suggesting would be "tricking" the system into scaling an 800x600 image onto a 1366x768 one, which would make the fonts blurry (as well as not in proportion, as you mention).

I've used gnome and lxde quite a lot, not so much xfce. It seems to be hard(er) to scale the  screen size of xfce than those of the other two desktop environments. Anyway, with the ultra-light weight lxde it works, and you need not distort it. 800x600 makes 'everything bigger' without distortion (at least for me), but at the left and right parts of the screen it's black. It is somewhat blurred, but not too bad. I think it is worth testing.

If you install one of these packages
```
sudo apt-get install lubuntu-desktop
``` or
```
sudo apt-get install lxde
```
you will be able to select desktop environment at the login screen. Try if you get something better with lxde! If not, you can easily remove the newly installed package.

What about changing resolution in Windows? You can test it and go back if you don't like it.

The ultimate solution would be to get a big external monitor, where everything can be bigger simply because the screen is big. So if you mirror your internal screen to the external one it will be big (somewhat blurred because of interpolation of the pixels, but still quite good). But of course, it costs money.

---

### Post by jancellor on 2013-01-11
> **sudodus said:**
> blurred

I am specifically trying to do it without interpolating (yes, that's the word for describing the concept, isn't it) and hence blurring.

You're right, I can change the resolution in Windows to get it to do the interpolation. What you're suggesting may help others but it is not proper scaling (like in Windows... even if some non-DPI-aware apps are blurry).

Having tried to find out the same thing for GNOME, there was more info online, and the answer was no, not possible. I therefore imagine the same is true for Xfce. (Though drawkcab seems to be suggesting otherwise. I thought there was only a font DPI setting just like in Xfce.)

Thanks anyway.

---

### Post by dogtag1968 on 2013-05-05
Thank you for your *ctrl+  ctrl- recommendation.*

---

### Post by dentaku65 on 2013-05-05
Choose Setting Manager -> Appearance -> Fonts and select the desired Custom DPI

---

### Post by pednick2 on 2014-04-12
Sorry haven't read all the posts in this thread with that out of the way shouldn't dconf Editor be installed by default? I've installed it, it's very useful thank you. :)

> **blackbird34 said:**
> You can edit the size of all OS elements in one go with DConf Editor, a graphical editor for a whole pile of system settings.

It is available in the repositories, so you can type in the following command or else get it from the Ubuntu Software Centre.
```
sudo apt-get install dconf-tools
```

Once you've got it go to the "org" section in the left hand margin then look for: gnome > desktop > interface > text scaling factor.

Default value is 1.0, if you make it bigger (say 1.2 or even 1.3) everything will get bigger, and if you make it smaller (say 0.9) everything will get smaller. Don't put it at 5 straight away or everything will be unusable :D

---

