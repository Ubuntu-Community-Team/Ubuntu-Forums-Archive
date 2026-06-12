---
title: "Dual Screen Sending Window to Other Screen"
date: 2005-12-20
forum: Desktop Environments
---

### Post by deity_me on 2005-12-20
Hi
I finally got dual screen setup working 
but just one more thing to do and I have no Idea if i can do this or its even possible.

If I open a window on Screen 1 how do I send it to screen 2?

I'm using an ATI Radeon and my xorg is configured for dual head
I'm not using xinerama or Big desktop

If i drag a window to the edge of screen 1 it shows up on the other edge of screen1
i want it to go over to screen 2

Help would be nice.

Thanks

---

### Post by kb3hkg on 2005-12-20
I am having this problem as well. I have an ati 9700 and am now using the fglrx driver for the dual screen which is setup for dual head as well. Can anyone help us?

---

### Post by deity_me on 2005-12-21
Okay I've got that big desk top thing going but i dont know how to specify screen resolutions for each monitor
Screen 1 I have 19" Widescreen
Screen 2 is 17" traditional 4:3

I need to specify different resolutions for each so that things dont get stretched on the wide screen

Help would be nice
Thanks

---

### Post by HermanAB on 2005-12-22
Screen size is defined in the xorg.conf file.
$ sudo su -
password
# cd /etc
# find -name xorg.conf
# cd X11
# vi xorg.conf

---

### Post by deity_me on 2005-12-22
the screen resolution for 1 monitor is there
but not the other

---

