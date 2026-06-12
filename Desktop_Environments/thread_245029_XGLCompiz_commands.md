---
title: "XGL/Compiz commands"
date: 2006-08-27
forum: Desktop Environments
---

### Post by The Pinny Parlour on 2006-08-27
I couldn't find much on these forums easily, so I went searching.  
Here is what I found and hope it helps others.

Credit: [Website]("http://justpretending.net/wp/2006/08/14/new-and-improved-enable-xglcompiz-on-ubuntu-dapper-drake/") taken from.
Some commands to get you started, rember you can edit a lot through the gconf-editor.

    o Switch windows = Alt+Tab
    o Arrange and view all windows = Moving the pointer to the top right screen corner turns on or off; clicking a window will zoom it to the front
    o Switch desktops on cube = Ctrl+Alt+Left/Right Arrow (or moving your mouse to the edge of your screen and rolling your mouse wheel)
    o Switch desktops on cube with the active window following = Ctrl+Shift+Alt+Left/Right Arrow
    o Rotate cube manually = Ctrl+Alt+Left-click and grab an empty desktop space.
    o Make window translucent/opaque = Either with the “transset” utility or Alt+Mouse wheel (or right clicking on a window’s title bar, and selecting the settings from ‘Appearance’)
    o Zoom in once = Super-key+Right-click
    o Zoom in manually = Super-key+Mouse wheel up
    o Zoom out manually = Super-key+Mouse wheel down
    o Move window = Alt+Left-click
    o Snap move window (will stick to borders) = Ctrl+Shift+Left-click
    o Resize window = Alt+Right-click
    o Bring up the window below the top window = Alt+Middle-click
    o Slow-motion = Shift+F10
    o Water = Hold Ctrl+Super key, and move mouse
    o Rain = Shift-F9

Known Bug - Shift+Backspace equals logout
When you press shift and backspace, XGL will be terminated and you will be logged out, a temporary fix for this problem is entering the following in a terminal.

    # xmodmap /usr/share/xmodmap/xmodmap.us (or your country code)

---

### Post by Jaxilian on 2007-04-24
Rotate cube manually = Ctrl+Alt+Left-click and grab an empty desktop space

This doesn't work for my Ubuntu 7.04 anyway.
Other commands work. I have a fresh default install. Cube-thing is activated though under desktop effects.

---

### Post by exidez on 2007-04-24
im the same as above...
i dont know what the rain one did either..

That desktop effect thing, is that the xgl/compiz or is it ubuntu's own design?

---

### Post by Jaxilian on 2007-04-24
Ubuntu's default desktop effects

I got the cube to rotate, BUT only sometimes and if I did that....well then some of the windows got white. for example I couldn't go in and try to disable the Desktop effects cause the window got all white.

I have an Ati Radeon 7500 chip and the computer is a Compaq Evo N610C

---

### Post by bobbymcsteels on 2007-07-31
sorry to sound like a complete Fidiot but what is the superkey?

---

### Post by andrewsomething on 2007-08-01
> **bobbymcsteels said:**
> sorry to sound like a complete Fidiot but what is the superkey?

The windows key...

---

### Post by ahchong on 2007-08-01
em.. mind using ATi X600 express. i do have crash in the compiz. remember because compiz is Alpha. then is u using AMD 64-bit, there will be crash on the button. the white screen is because of Xgl file problem. i donno how to repaire it. then this happen to me. when i insatlled the ATi restricted driver, my Compiz cannot work!!! failed to start. remove the ATi driver then its ok...

---

### Post by irvken on 2007-10-25
> Arrange and view all windows = Moving the pointer to the top right screen corner turns on or off; clicking a window will zoom it to the front

Anyone know how I enable this one in Gutsy Gibbon? doesn't appear to be in the options.

---

