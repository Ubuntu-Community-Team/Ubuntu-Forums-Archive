---
title: "How to disable touchpad tap-to-click on Xubuntu/xfce in 10.04?"
date: 2010-05-02
forum: Dell Ubuntu Support (CLOSED)
---

### Post by hologon on 2010-05-02
Just installed 10.04 on a Dell Mini 1012.

GNOME is a bit slow, even in NBE form, so I installed xubuntu/xfce. Much snappier. Love it.

One problem: There's no option to disable tap-to-click. This is a huge problem with a small keyboard and touchpad because my palm keep accidentally clicking when I type.

I tried adding an xorg.conf with a Synaptics entry with MaxTapTime 0 in both /etc/xorg.conf and /etc/X11/xorg.conf -- did nothing.

I can do it, curiously, with synclient MaxTapTime = 0 from the command line but I don't know how to make it permanent. I have to do it again every time I log in.

There seem to be some kernel changes in 10.04 that deprecate HAL and SHMConfig but this is well beyond my ken.

Any help is appreciated.

Thanks.

-Jon

---

### Post by EricDP on 2010-05-05
Your command solved my problem thanks!

To autostart, make a small script out of it (don't forget to set it executable!). Then go to Applications --> Settings -> XFCE 4 Settings Manager. Select Session and Startup. Select Application Autostart. Select Add... and I think you can probably figure it out from there.

```
#!/bin/bash

# fix touchpad - turn off tap to click
/usr/bin/synclient MaxTapTime=0
```

---

### Post by Swooper on 2011-10-24
I can say for sure that this also works on Xubuntu 11.10.

If anyone needs a noob-friendly break down:

1 open text editor (like Vrim)
2 paste in script
3 save as death_to_touchpad_tap.sh
4 right click on the new script file -> permissions -> execute as application.
5 put in your start up

done. Thanks previous posters!

---

### Post by Partizan242 on 2011-12-07
Thanks guys. This worked perfectly on my Macbook 2.1.

---

### Post by charleseddy on 2012-03-02
Again, confirmed, works like a charm on Ubuntu 11.10.

---

### Post by HarmonicaGoldfish on 2012-03-04
So incredibly awesome to find this. Thanks for the step-by-step :)

---

### Post by poumtatalia on 2012-03-12
Hi there, 

I'd LOVE to implement this as the "tap to clic" just drives me mad!
Unfortunately, when I try and run this command I get a 
"Couldn't find synaptics properties. No synaptics driver loaded?"

Any idea?

Thanks in advance for your kind help!
(I'm running Ubuntu 11.10, the xserver-xorg-input-synaptics is installed, I'm on a DELL Latitude E5510)

---

