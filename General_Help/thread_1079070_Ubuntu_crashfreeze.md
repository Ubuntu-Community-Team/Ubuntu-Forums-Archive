---
title: "Ubuntu crash/freeze"
date: 2009-02-24
forum: General Help
---

### Post by stabec on 2009-02-24
Hello, I'm new to the forums and had a quick question. Hopefully this is the right place..

I've been running ubuntu on my laptop for over a month now and everything has been going smoothly until today. Ubuntu started up normally and everything was going great until the system froze while I was running firefox. I could still move my mouse cursor and my wireless light continued to flash, but I was unable to do anything else. A friend of mine told me to turn off the Dim effect, which I did, but as soon as I closed the screen saver window the system froze again. It has happened twice in firefox and once when I tried to close the ss window

I have a Dell Laptop, Inspiron 6400

Thats about all I have for now, it has only happened three times and hopefully won't happen again. If anyone has any help it would be greatly appreciated, thanks! 

-stabec

---

### Post by uprooted on 2009-02-24
a little information about what exactly you are viewing on the internet would be moderately helpful , i had the same problem watching youtube videos for a while that is why i ask

---

### Post by stabec on 2009-02-24
I believe the first time it froze I was on youtube. As for the second time I do not remember what site I was at. The third time was when I closed the screen saver window after changing the dim settings.

---

### Post by cecilmoney on 2009-02-24
[http://ubuntuforums.org/showthread.php?t=989630](http://ubuntuforums.org/showthread.php?t=989630)
[http://ubuntuforums.org/showthread.php?t=653623](http://ubuntuforums.org/showthread.php?t=653623)
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/233896](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/233896)

Chances are none of those will help, but I thought they might give us some ideas of what is wrong.

I think the first thing you should do is completely turn off compiz (go to system > preferences > appearance > desktop effects) and click none.

if you shut compiz off and your comp still freezes, let me know.

---

### Post by mtopro on 2009-02-24
Are you by any chance using a second monitor with Xinerama?

It is a known bug and I have a patch that works great for that one.

---

### Post by stabec on 2009-02-25
I do remember plugging my laptop into my samsung monitor the other day.. But I unhooked it because I was having difficulties setting it up. That might possibly be why my ubuntu started acting up in the first place, any ideas?

---

### Post by mtopro on 2009-02-28
It is possible if you were trying to setup the second monitor that you enabled the second monitor in your settings.  What is the graphics card you are using?  Do you see a way to disable the second screen in the driver application?

If not, perhaps you could try installing 'xautomation' under synaptic or with:
```
sudo apt-get install xautomation
```

The go to SYSTEM>PREFERENCES>KEYBOARD SHORTCUTS and create a shortcut to 'Run A Terminal'.  I use  Ctrl+Alt+T

Then the next time your computer mouse click stops working, use Ctrl+Alt+T  and at the terminal window type in:
```

xte "mousemove 1980 0"
xte "mousemove 0 0"

```

If this is truely an issue on your machine, you should be able to take your screen resolution (example 1680x1050) and freeze your mouseclick with:
```

xte "mousemove 1679 5"
xte "mousemove 1680 5"

```

If that is the case then you have a known issue in located at: [https://bugs.launchpad.net/bugs/296167]("https://bugs.launchpad.net/bugs/296167")

To fix this, you can either disable the 2nd monitor in the driver settings,  or you can have the 'fix' code run when you press a shortcut key (let me know if you need to know how),   or you can run a Fedora patch, or wait for it to be included in Ubuntu in the future.

---

