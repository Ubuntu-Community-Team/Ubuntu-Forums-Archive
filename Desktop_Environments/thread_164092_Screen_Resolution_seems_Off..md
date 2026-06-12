---
title: "Screen Resolution seems Off."
date: 2006-04-22
forum: Desktop Environments
---

### Post by nismoskys on 2006-04-22
i just hooked up a new//old dell e153fp, 15" lcd flat panel, to my computer. The monitor's maximum resolution is 1024x768, which works fine, but everything seems so **huge**. It seems that there is much less room for things in 1024x768 in ubuntu, than there is in windows. 

Here's a screenshot of what my desktop was like @ 1024x768 in windows
(yes i had a mac theme at the time.. it was only for like a day lol.)
[[IMG]http://img233.imageshack.us/img233/4466/macbackround2ua.th.jpg[/IMG]](http://img233.imageshack.us/img233/4466/macbackround2ua.jpg)


and this is 1024x768 in ubuntu.
[[IMG]http://img92.imageshack.us/img92/9709/10241bd.th.png[/IMG]](http://img92.imageshack.us/img92/9709/10241bd.png)

everything's just _enormous_. just look at how much room there is to move things around in the windows screenshot, in comparison to the ubuntu one.

i think i could lower the font size, but all the pictures on icons and stuff would still be huge then..

anybody have my remedy?
thanks.

---

### Post by nalmeth on 2006-04-22
theme looks pretty good!
do you not have extra resolutions in SYSTEM - PREFERENCES - RESOLUTION ?
If not, you can re-edit your X-Server configuration in the terminal with:
*sudo dpkg-reconfigure xserver-xorg*
You will have the option to add the resolutions you need.
For the rest of the options, the defaults will be right unless you know better.

---

### Post by nismoskys on 2006-04-22
thanks

i do have extra resolutions availible, but the screen itself only supports up to 1024x768. Attempting anything higher only results in a black screen that says Video Mode Not Supported. That's what makes me wonder though, why do i have so much space in 1024x768 in windows, than i do in ubuntu?.

---

### Post by Ramses de Norre on 2006-04-22
Nautilus: edit > preferences > views : set default zoom level to a lower value. 
And choosing a smaller font does a lot too. 
You can make your task panes a bit smaller maybe (right click properties on panel).

---

