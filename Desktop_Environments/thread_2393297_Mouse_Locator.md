---
title: "Mouse Locator"
date: 2018-06-01
forum: Desktop Environments
---

### Post by jsonfn on 2018-06-01
My env is Ubuntu 16.04 LTS. Previously I use Unity so gnome mouse locator setting worked fine for me. 

[https://askubuntu.com/questions/333773/disable-show-position-of-the-mouse-when-the-control-key-is-pressed-in-13-04](https://askubuntu.com/questions/333773/disable-show-position-of-the-mouse-when-the-control-key-is-pressed-in-13-04)

But now I no longer use unity (switching to i3wm), pressing ctrl doesn't locate mouse position any more. Is there any solutions other than the one mentioned above?

---

### Post by again? on 2018-06-02
There is an XLib program to highlight the cursor on git hub that I tested.
It works in i3 on Ubuntu 18.04.

I used git to clone.  (you can just download the zip file, extract and cd to the extracted directory and run "make".)
```
mkdir ~/git
cd git
git clone [https://github.com/Carpetsmoker/find-cursor.git](https://github.com/Carpetsmoker/find-cursor.git)
cd find-cursor
make
```

Then to initiate... 
```
[COLOR="#696969"]~/git/find-cursor/[/COLOR]find-cursor
```

For help
```
[COLOR="#696969"]~/git/find-cursor/[/COLOR]find-cursor -h
```

Example (see pic)...
```
find-cursor -s 150 -d 25 -l 3 -w 500 -g -c orange
```
Click for gif
[ATTACH=CONFIG]279938[/ATTACH]

---

### Post by fyfe54 on 2018-06-02
Install gnome-tweaks from the Ubuntu Software Center.  In the Keyboard and Mouse section there is a setting to locate the mouse pointer by pressing the Ctrl key.

Lots of other settings to play with too.

---

### Post by Dennis N on 2018-06-02
If you don't mind a blinking cursor, it is easier to spot and likely works in any desktop environment. I use one that has 1/2 sec blink time - red to white. I found it sufficient to just modify the left pointer and hand cursors of my existing theme to blinking style. There are instructions elsewhere on this forum if you are interested.

---

