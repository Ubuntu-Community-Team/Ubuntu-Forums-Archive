---
title: "Win7 style Aero Snap Effects for Compiz"
date: 2009-10-29
forum: Desktop Environments
---

### Post by gotsanity on 2009-10-29
Ok boys and girls, get ready to write this down.

First you need to make sure you have the following installed:

```

sudo apt-get install compizconfig-settings-manager wmctrl

```

*While that is running find out how big the dimensions of your screen is (Mine has a width of 1600 pixels by a height of 1200 pixels). Write these down you will need them later.*

Next, open compizconfig settings manager by clicking on **System > Preferences > Compizconfig Settings Manager**

At the very top is a button labeled **Commands**. Select it.

*Wmctrl will do the window sizing via the following command:*

```

wmctrl -r :ACTIVE: -e <Gravity>,<X>,<Y>,<Width>,<Height>

```

**Gravity:** Leave this 0.
**X,Y:** This is the top left position of the window (AKA: Where to start drawing the window.)
**Width,Height:** How large the window should be drawn.


Input the following (Adjusting the totals for the dimensions of your screen):

**Command Line 0** ```
wmctrl -r :ACTIVE: -e 0,0,0,800,1155
```
**Command Line 1** ```
wmctrl -r :ACTIVE: -e 0,800,0,800,1155
```
**Command Line 2** ```
wmctrl -r :ACTIVE: -e 0,0,0,1600,1155
```

And the final steps. Switch to the **Edge Bindings** tab and select the following edges:

**Run Command 0** - Left
**Run Command 1** - Right
**Run Command 2** - Top

Last step: Click **Back** and then click on **General Options**. Set your **Edge Trigger Delay** to something you find comfortable with. *Mine is set at 400.*

*Only disadvantages I have come across is that if you let the cursor hover too long over a hot point you will accidentally start resizing whatever window you have active. Also, there is a quirk with some windows that will not allow them to resize to the correct size (I am assuming due to the size of the widgets within the window).*

---

### Post by Bonster on 2009-11-07
Interesting, I usually use the compiz tile feature for the snap of the two windows. but ill give this a try see how it goes cheers =)

---

### Post by t.rei on 2009-11-08
```
wmctrl -r :ACTIVE: -e 0,0,0,1600,1155
```

Is there any way to not use hard-coded values but get MIN/MAX values of the screen the window is currently on?
I have a "maximum pain" setup here: 3 screens, all different resolutions. ;)

---

### Post by zlatkart on 2009-11-08
> Is there any way to not use hard-coded values but get MIN/MAX values of the screen the window is currently on?
I have a "maximum pain" setup here: 3 screens, all different resolutionsYes, try this:

[http://gtk-apps.org/content/show.php/ctrlwm?content=114565](http://gtk-apps.org/content/show.php/ctrlwm?content=114565)



(But it should be also possible with wmctrl: toggle MaximizedHorizontal (something like this). Read wmctrl --help for more info on this)

---

### Post by aardvark4 on 2010-08-09
For anyone still looking, the non hard-coded version for maximizing works as:

wmctrl -r :ACTIVE: -b add,maximized_vert,maximized_horz

via

[http://www.omgubuntu.co.uk/2009/11/aero-snap-ubuntu-linux.html](http://www.omgubuntu.co.uk/2009/11/aero-snap-ubuntu-linux.html)

---

### Post by MathMcC on 2010-10-28
> **gotsanity said:**
> *Only disadvantages I have come across is that if you let the cursor hover too long over a hot point you will accidentally start resizing whatever window you have active.*

Sorry for dragging up this old thread. But has anyone found a workaround for this? Its highly annoying!

---

### Post by davidinsaskatoon on 2010-10-29
...or you could use Kubuntu.  It has an "Aero Snap" workalike built in as a default.

---

