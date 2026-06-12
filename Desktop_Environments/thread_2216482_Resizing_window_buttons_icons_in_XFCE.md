---
title: "Resizing window buttons icons in XFCE"
date: 2014-04-12
forum: Desktop Environments
---

### Post by tomislav.nikolic00 on 2014-04-12
Hello, community.

I've been looking for a way to resize the icons in taskbar to match the size of icons in panel launchers. I like the look of unity desktop's right panel so I moved one panel to the right and made it transparent, added a couple of application launchers and a taskbar (Window Buttons, as it says in the panel preferences) and also installed faenza-icon-theme, which looks nice.

I got a picture of it here: [http://en.zimagez.com/zimage/screenshot-120414-122919.php](http://en.zimagez.com/zimage/screenshot-120414-122919.php)

Now, I ain't posting here to show of my desktop, am I :)

I would like to make the window buttons' icons larger, possibly the same size as the launchers (in the picture, taskbar's icons are smaller then the launchers'). Editing files is ok with me, and I ain't scared of command line either, even tho I've been using linux only for a year now. Any help is appreciated :). Thanks a lot.

---

### Post by ajgreeny on 2014-04-12
I presume you mean the unity **left** panel not the **right** one, but aside from that I can not find any way to make the icon in the window buttons of xfce4 any bigger; even making the panel larger does not change the icon size.  Are the two bottom icons (firefox and a media player?) in the panel, the window buttons that you want to have larger icons; it is difficult to see exactly what's what in your picture.

No doubt it could be done by editing the source code, or some other hidden config file, but I don't know which one, nor what would need editing, and a quick grep through the xfce configuration folders in my home does not shed any light on this either.

---

### Post by Toz on 2014-04-12
The window button icon scales up to 32 pixels - no larger. There was [some discussion]("http://xfce.10915.n7.nabble.com/tweaking-Window-Buttons-defaults-td42890.html") about this recently. 

There is another plugin available, xfce4-taskbar-plugin, that will scale icons up to 49 pixels, but I don't think its included any more in the official repositories and you need to build from source if you want it. More info in this thread: [http://ubuntuforums.org/showthread.php?t=2090875](http://ubuntuforums.org/showthread.php?t=2090875).

---

### Post by tomislav.nikolic00 on 2014-04-12
Thank you for replying.

Sadly, I can find a ton of configuration files regarding panels and icons but changing any of them hasn't yielded any results.

I will look up xfce4-taskbar-plugin, hopefully build it successfully, and report back once I'm done.

---

### Post by tomislav.nikolic00 on 2014-04-14
Here is the update on the matter.

I tried building xfce4-taskbar-plugin, but failed in several attempts and when it seemd to have installed correctly it didn't want to play along with the panel.

I wanted to quit on the design but luckily I ran into a nice lightweight dock app called AWN ([here]("https://launchpad.net/~awn-testing/+archive/ppa") it is for saucy) which is easily configured and works very well with XFCE, even allows the native menu to be put as a standalone applet.

Here is a photo of my desktop, Xubuntu with Unity look: [http://www.zimagez.com/zimage/screenshot-140414-144703.php](http://www.zimagez.com/zimage/screenshot-140414-144703.php)


I call it XAWNbuntu :D

I'm marking this thread as solved, even tho it is not what I was looking for in the first place, but is a hell of a solution to the problem in my opinion.

---

### Post by ajgreeny on 2014-04-14
Your pic does not show any window buttons with large icons, only a number of launchers in the left panel, and the one window-button at the bottom still with a smaller browser icon than you wanted, and as you are probably aware the launchers can be enlarged greatly to 128px if you want, but that is surely not what you were asking about.

What you do show is possible to achieve even without adding a dock, simply by putting a panel on the left and adding launchers to it, which can be for any applications in the system, or any other panel applets, eg menu, window-buttons, etc etc.

What is awn giving you that a normal panel did not?

---

