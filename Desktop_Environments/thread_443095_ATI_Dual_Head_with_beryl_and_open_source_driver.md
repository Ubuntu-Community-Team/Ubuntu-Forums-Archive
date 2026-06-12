---
title: "ATI Dual Head with beryl and open source driver"
date: 2007-05-14
forum: Desktop Environments
---

### Post by dodgePT on 2007-05-14
Hi there, finally it seems i have it all set and running smoothly, i'm pretty satisfied with what ubuntu has to offer me, thanks also to this great community always willing to help.
Although i have an ATI 9600 Pro, i've managed to get beryl working 100% and movies don't look blocky anymore when in fullscreen mode (thanks to xine). I used the "radeon" driver and AIGLX method.

Now, all i need to forget MS completelly is to get dual head working. I mean, it's working already, but i have to change my overall resolution to 800x600 and press Ctrl + - to export the image. Thing is, everything i see in my PC screen (Acer LA1916W in VGA port)  is the same as in my 40" Samsung LCD TV (DVI port).

Question is, what settings (monitor, device) must i tweak in xorg.conf to get different resolutions in both displays without it being in "clone" mode?
Is it possible to have different resolutions at the same time and two different desktops (ex: play a movie in my tv while watching something else in my PC screen) with the open source driver?
And most important, is this all possible with beryl running?
All i need is a link of some sort to a tutorial for all the possible xorg.conf configurations and options, i'd try to sort problems out myself.
Sorry if i'm posting this in the wrong section, it seemed the most obvious place to place this kind of topic.

Thank you for your support and keep up with the marvellous work :)

---

### Post by dodgePT on 2007-05-14
Through some research i did it seems that open source drivers have a 2048 px width limitation and i have to use MergedFB, which is built in the open source driver. Beryl doesn't support textures wider then 2048px, so i guess i have a limitation. I was thinking about setting my 19" LCD monitor to 1440x900 and my 40" LCD TV to something around 1024x768 which will stretch my desktop to 2464 px, way above the 2048 limitation.

Beryl behaviour under these conditions is not guaranteed, although some state it will work.

Here's a [link]("http://www.botchco.com/alex/radeon/mergedfb/cvs/DRI/final/radeon.4.html") with some more info that might be usefull to others. I'll try to tweak and will post some results later :)

---

