---
title: "desktop display issue - new icons off screen"
date: 2018-01-21
forum: Desktop Environments
---

### Post by babag on 2018-01-21
having an issue with the xfce desktop. using ubuntu studio, fresh install of current version. 

when i create new launchers they appear off screen and i have to reposition my display through the settings manager to find them. in addition to new launchers, sometimes windows op[en off screen or partially off screen, such as with their title bars off screen so they can't be accessed to drag them so as to be fully visible.

of three attempted installs, i tried avlinux and kxstudio as well, ubuntu studio was the only one that seemed to correctly detect my four-monitor setup. i'm working with multimedia so this setup is critical. ubuntu has been great with the exception of the off-screen thing. i've linked two screenshots to illustrate the issue. it looks like the system is defining the desktop as the combined height and width of my entire display layout, which is, of course, not quite right. there are empty areas on either side of the upper display. by defining the desktop by combined height/width the system thinks it can place icons in the upper left area, which is off screen. 

the first screenshot shows my normal display positioning. the second shows how i have to reposition the upper display to find or access off screen items.

how do i fix this?

thanks,
BabaG
 
[[img]https://farm5.staticflickr.com/4713/25954846868_8abfd03b7f_b.jpg[/img]](https://flic.kr/p/FxxnHN)[Display_setup_normal](https://flic.kr/p/FxxnHN) by [BabaG01](https://www.flickr.com/photos/25636857@N04/), on Flickr
[[img]https://farm5.staticflickr.com/4716/39118292814_9e096d7fe7_b.jpg[/img]](https://flic.kr/p/22AKtAo)[Display_setup_find_icons](https://flic.kr/p/22AKtAo) by [BabaG01](https://www.flickr.com/photos/25636857@N04/), on Flickr

---

### Post by Holger_Gehrke on 2018-01-21
Two things which are both probably not very helpful:

[LIST=1]
[*]Your screenshots don't show up, they only show a message from photobucket: "Please update your account to enable 3rd party hosting". 
[*]Repositioning windows whose title bar is off screen is done by alt-dragging (hold the alt-key while dragging from anywhere in the window with the left mouse button) 
[/LIST]
Also, I'm not sure if XFCE is the right environment for a display setup like this. (If I understand your problem right, you've got 4 displays, 3 in a row and a 4th on top in the middle; XFCE seems to treat it as six displays with two missing). From what I've read,  multi-display setup seems to be a particular strength of KDE. You might want to give a Kubuntu live system a try. The multimedia applications you need might not come pre-installed on that, but they can be installed.

Holger

---

### Post by babag on 2018-01-21
thanks, holger_gehrke. the alt-drag tip is actually very helpful. i've updated first post with, hopefully, better links.

thanks again,
BabaG

---

