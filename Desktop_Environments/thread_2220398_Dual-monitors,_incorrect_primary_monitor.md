---
title: "Dual-monitors, incorrect primary monitor"
date: 2014-04-27
forum: Desktop Environments
---

### Post by dannyboy79 on 2014-04-27
I have a GTX 760 and I am using the nvidia driver from the website, Nvidia binary 334.21. I have 2 displays. the asus monitor is directly in front of me on my desktop and I want that to be my primary monitor where my desktop icons appear and my panels live, and then I want the 2nd display, a samsung, which is on the left such that when I move my mouse to the left it goes onto that display. 

What I have now is that I have to move my mouse to the right in order for the mouse cursor to go on the monitor which is physically on the left. IF I switch the setup in nvidia-settings so that the left physical monitor is on the left of my asus monitor than all my icons and panels appear on the samsung monitor which is not what I want.

here's a picture and my xorg.conf
[IMG]https://lh6.googleusercontent.com/-92Edi0_cI-E/U12b3MrY7TI/AAAAAAAACrA/RuKnvD_1OLk/s800/monitors.jpg[/IMG]

[http://pastebin.com/Hs0q6GEL](http://pastebin.com/Hs0q6GEL)

---

### Post by raspatan on 2014-04-29
I solved the position of screens in settings >> display. I can select there the position (right of, left of). The panel can be set in either screen in settings >> panel. All this is with Xubuntu, so xfce settings. I see you also have the same so that should work for you.

---

### Post by dannyboy79 on 2014-04-30
i sort of figured that out last night, i didn't realize that i could change the preferences of the panel and tell it to go on which display or even span across multiple displays but how do i get the desktop icons to be on the monitor on the right. I suppose I could drag them over to the panel on the right. But i believe this is an issue because Ubuntu always sets the default location at 0,0. I will play around with it some more, thank you for replying. 

I am new to dual monitors and I love the extra room and with workspaces I have sooo much room now for apps.

---

### Post by mrhaw on 2014-04-30
I gave up and got used to pull the mouse right ro get to my screen on the left side. ](*,)


[SIZE=2]UPDATE: Latests software update fixed this for me. ...Or I just did something wrong all the time :P[/SIZE]

---

