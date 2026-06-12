---
title: "Configure mouse so button 3 is more useful?"
date: 2007-07-23
forum: Desktop Environments
---

### Post by QwUo173Hy on 2007-07-23
I use a graphics tablet, which has a total of 3 buttons.

A tablet does fall down in one area, which is scrolling. this can't really be done with a pen. Is there a way I can setup button 3 so when I press it I can scroll up and down the page when I move the pen?

---

### Post by robgill on 2007-07-23
Try expresskeys if its a wacom tablet.  I was able to make my buttons anything ( I chose alt-left and alt-right with the graphire4 scroll-wheel, it works well) 

0) [get expresskeys]("http://hem.bredband.net/devel/wacom/")

1) install expresskeys

2 edit config file in ~/.expresskeys  (mine's called graphhire4.conf1) 
uses keycodes where it says left and right buttons
pg up: 99 
pg down: 105
find more using xev

edit: scroll up 995; scroll down 994

3)make a text file called expresskeys_launch.sh (or whatever) with:
```

#!/bin/bash
expresskeys -d pad

``` in it.

4) Make it executable```
chmod +x expresskeys_launch.sh
```

5) add to sessions to start at boot

I figured this out yesterday and I'm not real talented so you should get it, reply if it works for you or if you need more help.

Good Luck

---

### Post by QwUo173Hy on 2007-07-26
Hi robgill. Thanks so much for your helpful reply. What are the chances of someone with a Wacom tablet having done this!? I'm stuck straight off with dependencies and don't know what I need to install.

> Checking the X compiling environment in detail...

/usr/lib/libX11.so OK
/usr/lib/libXext.so OK
/usr/lib/libXi.so OK
Can not link with Xtst /usr/lib/libXtst.so library!
/usr/include/X11/Xlib.h OK
/usr/include/X11/Xutil.h OK
/usr/include/X11/extensions/XInput.h OK
/usr/include/X11/extensions/XIproto.h OK
/usr/include/X11/extensions/XTest.h OK

The X compiling environment is NOT complete!
Some linux distributions omit parts of, or sometimes
the whole, X development environment. Based on the
error message(s) above you should be able to hunt down
which package(s) you need to install. For example, one
distribution call their xinput and xtest packages
libxi-dev and libxtst-dev


Any ideas?

---

### Post by robgill on 2007-07-26
Where are you when you get that error? Install expresskeys?

Anyway, it appears that you are missing the libxtst-dev package.  Install it from Synaptic.

Reply and I'll give you the best answer I can.  I'm no linux wiz, but I'm starting to understand more, so hopefully we'll figure this out.

---

### Post by QwUo173Hy on 2007-07-27
Thanks robgill. I've installed libxtst and I was able to install express keys. Now the problem I'm having is that my config file is fairly sparse and there isn't an entry for page-up/down. I've attached the file.

 Also, xev isn't giving me keycodes for my buttons, just 'button 2' and 'button 3'.

---

### Post by robgill on 2007-07-27
What other files are in your .expresskeys folder.  I have the padless one too, but that's not where I configured it. 
Which tablet do you have? I have a Graphire4 and the file I edited was graphire4.conf1

Try posting the other files and I'll try to figure out which one should be edited!

when you use xev it will tell you keycodes for keys on the keyboard, that's where I got pgup, pgdown.

---

### Post by QwUo173Hy on 2007-07-30
Oh good. I thought you got the keycodes from your stylus so I was dissapointed :) I'll attach the few files I have.  I really appreciate the effort you're going to here.

<edit> Oh yeah, I'm using a Volito 2! </edit>

---

### Post by robgill on 2007-07-30
It appears express keys doesn't support your tablet since it does not have buttons/scroll wheel on the pad.  I'll let you know if I find another solution.

---

### Post by strabes on 2007-07-30
You can use the [all-in-one gestures](https://addons.mozilla.org/en-US/firefox/addon/12) firefox extension and enable grab & drag scrolling with the 3rd mouse button. I use it; it's great.

---

### Post by QwUo173Hy on 2007-07-30
Rob, thanks again for all your effort! Strabes, that plugin is great. Makes web-browsing much more enjoyable for me, thank you.

Now if I can get something similar for the desktop, I'll have a perfect system and I'll never need to upgrade :)

---

