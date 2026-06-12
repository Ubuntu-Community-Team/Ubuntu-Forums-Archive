---
title: "Multiple Monitors X Server Software Glitch"
date: 2012-01-29
forum: Desktop Environments
---

### Post by caseykoons on 2012-01-29
I am trying to use multiple monitors with a recent installation of Ubuntu 11.10 on a HP Pavilion G7 laptop with an AMD A6 64 bit processor.

It has a AMD Radeon HD 6520G graphics card, for which I am using Catalyst 12.1, Driver Package 8.93-111205a-132081C-ATI.

If anyone knows how to make this graphics card work with the open-source drivers, I would LOVE to know this! I was forced to install the fglrx driver after using the alternate installer to place Ubuntu on the machine. For some reason, the open-source driver did not recognize the fglrx.

Using Catalyst, I was able to get multiple monitors to work. However, in an attempt to get the open-source drivers to work ( so that I could try Gnome 3 shell ), I seem to have done something to break the multiple monitors in a software way.

If I configure to span my desktop using amdcccle, I get the extended desktop that I set up. As soon as I log in, however, a white window opens in the second monitor, briefly showing a menu with "File, Edit, View, etc." and then that screen goes completely white. I can move my mouse over to the second screen, but the mouse cursor turns into a large black X. This is extremely vexing, because for a second right after I log in and as I'm logging out, this effect vanishes and the desktop works as expected!

Any help on this would be greatly appreciated. I have purged and re-installed fglrx according to the instructions at

[http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#Removing_Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#Removing_Catalyst.2Ffglrx)

I have most recently manually updated Catalyst to 12.1 in an attempt to fix this, but it seems like it's not my driver that's causing the problem, but some aspect of the X server software itself.

So: if anyone has advice for making the open-source driver work with my card, or an insight on this multiple monitors glitch, I would love the help.

---

### Post by mrmonitors on 2012-05-02
Hey, if you're looking for information on setting up [multiple monitors](http://dual-monitors.org/multiple-monitors/) then you might want to check out this site: [http://dual-monitors.org/multiple-monitors/](http://dual-monitors.org/multiple-monitors/)

They have a ton of articles on setting up multiple monitors, and I'm pretty sure I saw one related to ubuntun.

---

### Post by abisdad on 2012-06-02
Hi,

I've had same problem on two different machines.  Happened again tonight and found this post:

[http://askubuntu.com/questions/125409/how-are-separate-x-screens-supposed-to-work-probable-problem/145501#145501]("http://askubuntu.com/questions/125409/how-are-separate-x-screens-supposed-to-work-probable-problem/145501#145501")

This led me to do some playing and then posted this:

I've got the same problem! Just installed Ubuntu 12.04 onto an old Acer Travelmate with Nvidia graphics, and same problem.

After reading what you said about Nautilus, tried loading a few diferent window managers. Follow this link to find out how:

[http://ramannanda.blogspot.com.au/2009/06/changing-window-manager-in-ubuntu.html](http://ramannanda.blogspot.com.au/2009/06/changing-window-manager-in-ubuntu.html)

(Tried Gnome, Unity 2D, and lxde - all flicked the wallpaper up, then went white like yours).

However xfce worked! I think I did this:

```
sudo apt-get install xfce4
```

Xfce fixed it, and works a treat!

I really like the way xfce is uncluttered - it takes 1/2 hour to get your head around it, but is well worth it.

See: [http://docs.xfce.org/xfce/getting-started]("http://docs.xfce.org/xfce/getting-started")

Different windows being run on each monitor, can independently set the backgrounds on each monitor! :-) They each have their own workspace too. Fantastic!

Rob (abisdad)

PS If anyone can tell me how to get rid of the white x screen, I'd love to know. I've another old desktop with a quad monitor card in, but it only works with 2 screens - the other two are white! (Hate to admit it, but Windoz works great on all 4! :-( )

---

