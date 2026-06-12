---
title: "How to Move Window Buttons to the Right Ubuntu 10.04"
date: 2010-06-19
forum: Desktop Environments
---

### Post by Rajiev on 2010-06-19
Hey guys,

How to move the Windows control button ( Minimize, Maximize , Close) Buttons back to the conventional place; top right corner of the screen ?

I can't imagine why they have changed the place of this button from the conventional place :S

---

### Post by wilee-nilee on 2010-06-19
alt-f2 enter gconf-editor go to apps metacity general button layout right click to edit key and make it this.
```
:minimize,maximize,close
```

Now the key to this is the : it moves it to the right you can move each min, max, close in whatever order you want.

---

### Post by Kimm on 2010-06-19
A faster way of doing it is to paste this command in a terminal (or run it in the alt+f2 dialog): 

```

gconftool-2 --type string --set /apps/metacity/general/button_layout "menu:minimize,maximize,close"

```

---

### Post by cogier on 2010-06-19
You can also just change the Theme in **System>Preferences>Appearance**

---

### Post by Rajiev on 2010-06-20
i found this from the net

```
http://www.howtogeek.com/howto/13535/move-window-buttons-back-to-the-right-in-ubuntu-10.04/
```

Is this the same you are saying?

---

### Post by Westz on 2010-06-20
if you dont want to deal with code, just use the theme manager and click on one of the high contrast themes then go to a theme that doesnt revert it to left side. apply changes with customize. thats how i did it. make sure to save the theme

---

### Post by Rajiev on 2010-06-21
> **Westz said:**
> if you dont want to deal with code, just use the theme manager and click on one of the high contrast themes then go to a theme that doesnt revert it to left side. apply changes with customize. thats how i did it. make sure to save the theme

This seems pretty simple and n00b digestable :p
Gotta try it.
BTW, I got it fixed.
Thanks guys

---

### Post by howefield on 2010-06-21
> **Rajiev said:**
> This seems pretty simple...

It certainly is, but not perhaps the best way, which is described in this sticky.,

[http://ubuntuforums.org/showthread.php?t=1469475](http://ubuntuforums.org/showthread.php?t=1469475)

---

### Post by I got worms. on 2010-06-21
> **Kimm said:**
> A faster way of doing it is to paste this command in a terminal (or run it in the alt+f2 dialog): 

```

gconftool-2 --type string --set /apps/metacity/general/button_layout "menu:minimize,maximize,close"

```

Awesome.

Thank you.:p

---

### Post by Rajiev on 2010-06-22
> **Kimm said:**
> A faster way of doing it is to paste this command in a terminal (or run it in the alt+f2 dialog): 

```

gconftool-2 --type string --set /apps/metacity/general/button_layout "menu:minimize,maximize,close"

```

Ya,

The most easiest and 100% sure method is this.
Thanks

---

### Post by GIRI MURALI on 2010-07-03
1. Press 'alt+f2' keys to open run window
2. In run window type 'gconf-editor' and then click run to open configuration editor window
3. Explore 'apps > metacity > general'

4. Select button-layout on the right-pane double click on the 'close,minimize,maximize:' on it's right side and edit  it as 'menu:minimize,maximize,close'. Now the buttons should be reached on the right side
for pictorial tutorial [http://www.beubuntu.co.cc/2010/06/how-to-move-close-minimize-maximize_30.html](http://www.beubuntu.co.cc/2010/06/how-to-move-close-minimize-maximize_30.html)

---

### Post by jazzman65 on 2010-10-19
Perfect, thanks!

---

### Post by libssd on 2010-10-19
Ubuntu Tweak makes this (and many other things) very easy, no matter what theme you choose.

---

### Post by sky pilot on 2010-10-20
> **wilee-nilee said:**
> alt-f2 enter gconf-editor go to apps metacity general button layout right click to edit key and make it this.
```
:minimize,maximize,close
```

Now the key to this is the : it moves it to the right you can move each min, max, close in whatever order you want.

Thank You! I was almost ready to go back to Mint if I had to keep the buttons on the left, it was a real aggravation. I have come back to Ubuntu more for the community and its mission than the actual operating system, which I like.

---

