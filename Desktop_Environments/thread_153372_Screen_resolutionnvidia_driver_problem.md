---
title: "Screen resolution/nvidia driver problem"
date: 2006-03-31
forum: Desktop Environments
---

### Post by sturat_7 on 2006-03-31
I have just set-up this wonderful OS and now I can't resize my screen. I have a nvidia geforce 5600 and I have no idea how to get the driver to work. I have gone through the DIY and still have no idea how to get it to work. I am also not sure if I am using the proper driver. 


thank you,
STU

---

### Post by Sutekh on 2006-04-01
[QUOTE=sturat_7]I have gone through the DIY[/QUOTE]
What DIY did you follow?


[QUOTE=sturat_7]I am also not sure if I am using the proper driver. 
[/QUOTE]
Try following this HOWTO.

[Ubuntu Forums - HOWTO Latest NVIDIA Drivers](http://ubuntuforums.org/showthread.php?t=75074)

 - Method 1 is very easy to accomplish and should get things working correctly


If this does not resolve your problem then you should reconfigure the X windows server and ensure that you choose the resolution you want.

You can do this by issuing the command
```
sudo dpkg-reconfigure xserver-xorg
```
 - when prompted for a password, use your users password.  The characters of the password won't appear on the screen, but trust me it is typing them.

 - you will be asked a long string of questions regarding the input devices of your PC; your keyboard, mouse and monitor.  If you don't know what you should answer to these questions go with the default/suggested ones.

 - you should be able to choose the resolution you wish to use

 - when you are finished press Alt+Ctrl+Backspace to restart the GNOME display manager (not Alt+Ctrl+Del, which would restart the PC)

---

