---
title: "Ubuntu Feisty with Beryl"
date: 2007-05-25
forum: Desktop Effects &amp; Customization
---

### Post by trialsboysam on 2007-05-25
Hi.  

I am new to Linux but not to computers and am getting on with ubuntu great.  However i have run into problems while trying to install Beryl.  I have Nvidia GeForce 6600 graphics cards and have followed some instructions for installing beryl found at

[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_nVidia](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_nVidia)

using the 123 NoFile Automatic Installation Method,  This all seems to go fine except after a reboot i get the white screen problem.  I have tried may fixes for this and none have worked.  

I have been trying many different solutions and even tried the Uberyl distribution.  In this case i ran a bundled program called envy and chose to install Nvidia drivers.  After this is completed it asks to restart.  this time on reboot i get a "failed to start the x server" error and am no longer able to load ubuntu.

Please would anyone be able to help.  I fear that i may have to give up and end up back with windows.

Thanks alot

Sam

---

### Post by pHreaksYcle on 2007-05-25
This is not really a fix, so sorry if I got your hopes up...

I posted with similar problems on my Dell 1501 about Beryl (still can't get it to work, damnit!) and that and got some posts that were revolutionary for me. In short, people told me, "It is just a window manager! Chill and out and enjoy the rest of the cool shitt that Ubuntu has to offer!"

Basically, keep working on this till you die from lack of sleep, but do not switch back to M$ Windoze just because of this. It doesn't justify it! Have a good night and good luck!

---

### Post by trialsboysam on 2007-05-26
I just tried to run desktop effects.  Was told to restart and when i did i got the same "failed to start x server" message.  This time after viewing the messages i typed 

$ sudo dpkg-reconfigure xserver-xorg

this then asked me various setting changes and i was able to choose the correct nvidia drivers.  However after a restart it was still not working.

Anyone know how to help with this?

---

