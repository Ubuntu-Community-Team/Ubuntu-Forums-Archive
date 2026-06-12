---
title: "Make Screenshot app show date and time."
date: 2016-03-11
forum: Desktop Environments
---

### Post by Rytron on 2016-03-11
Hi.

How can I make the Screenshot app show date and time like in Xubuntu and Linux Mint MATE?

The image shows the Save Screenshot windows for Ubuntu MATE 15.10 (top) and Linux Mint MATE 17.3 (bottom).

Thanks.

---

### Post by v3.xx on 2016-03-11
Maybe you could upgrade the package.

[ATTACH=CONFIG]267758[/ATTACH]

---

### Post by Frogs Hair on 2016-03-11
I can't help with modifying the screen-shot tool, but if you wanted to add text to the image , note the time/date and add it in gimp . There are also many simple conky themes that will display date and time on the desktop rather than the panel. Capturing menu items one at a time such as the calender can be done using the time delay in the screen-shot tool.

---

### Post by QDR06VV9 on 2016-03-11
> **v3.xx said:**
> Maybe you could upgrade the package.

[ATTACH=CONFIG]267758[/ATTACH]
+1... But your using 15.10 it should show the date and time there too..
Maybe there are two apps there, Maybe just guessing here but was XFCE installed also?
The tool that ships with mate is** "mate-screenshot --interactive"**
Take Sceernshot

---

### Post by v3.xx on 2016-03-11
And runrickus scores a +1

Run "mate-screenshot --interactive" in terminal, still the same?

---

### Post by Rytron on 2016-03-12
> **Frogs Hair said:**
> I can't help wit modifying the screen-shot tool, but if you wanted to add text to the image , note the time/date and add it in gimp . There are also many simple conky themes that will display date and time on the desktop rather than the panel. Capturing menu items one at a time such as the calender can be done using the time delay in the screen-shot tool.

Hi FH.

Use GIMP? You misunderstood my post. ;-)

---

### Post by Rytron on 2016-03-12
> **v3.xx said:**
> Maybe you could upgrade the package.

[ATTACH=CONFIG]267758[/ATTACH]

Hi v3.xx.

Ah, so I take it future releases will have the date and time feature incorporated by default? So I take it that Ubuntu MATE 16.04 will have this.

---

### Post by Rytron on 2016-03-12
> **runrickus said:**
> +1... But your using 15.10 it should show the date and time there too..
Maybe there are two apps there, Maybe just guessing here but was XFCE installed also?
The tool that ships with mate is** "mate-screenshot --interactive"**
Take Sceernshot

Hi runrickus.

Just MATE was installed. Both 'mate-screenshot --interactive' and 'mate-screenshot' output only "Screenshot".

---

### Post by Rytron on 2016-03-12
> **v3.xx said:**
> And runrickus scores a +1

Run "mate-screenshot --interactive" in terminal, still the same?

Same.

---

### Post by vasa1 on 2016-03-12
[http://manpages.ubuntu.com/manpages/wily/en/man1/mate-screenshot.1.html](http://manpages.ubuntu.com/manpages/wily/en/man1/mate-screenshot.1.html) doesn't seem to offer the option. Neither does [http://manpages.ubuntu.com/manpages/xenial/en/man1/mate-screenshot.1.html](http://manpages.ubuntu.com/manpages/xenial/en/man1/mate-screenshot.1.html)

If you don't mind, you could try `scrot`: ```
EXAMPLE

       scrot '%Y-%m-%d_$wx$h.png' -e 'mv $f ~/shots/'
       This would create a file called something like 2000-10-30_2560x1024.png
       and move it to your shots directory.


```from [http://manpages.ubuntu.com/manpages/wily/en/man1/scrot.1.html](http://manpages.ubuntu.com/manpages/wily/en/man1/scrot.1.html)

---

### Post by Frogs Hair on 2016-03-12
> **Rytron said:**
> Hi FH.

Use GIMP? You misunderstood my post. ;-)

This what I meant. The dates is wrong though .

---

### Post by Rytron on 2016-03-12
> **Frogs Hair said:**
> This what I meant. The dates is wrong though .

I referred to the date and time format being in the screenshot tool instead of just the word 'Screenshot' -- that way if I take a few screenshots then each one will have a unique name thus none will overwrite the other.

You interpreted something else. Thanks anyway.

---

### Post by v3.xx on 2016-03-12
I'm beginning to think that the easy way out is just to install gnome-screenshot

---

### Post by Rytron on 2016-03-13
> **v3.xx said:**
> I'm beginning to think that the easy way out is just to install gnome-screenshot

That's a quick workaround. The output is as I wanted, i.e. "Screenshot from 2016-03-13 10:13:00.png". Hopefully the next Ubuntu MATE has this format in the default MATE screenshot tool.

Cheers v3.xx.

---

### Post by Rytron on 2016-03-19
> **vasa1 said:**
> [http://manpages.ubuntu.com/manpages/wily/en/man1/mate-screenshot.1.html](http://manpages.ubuntu.com/manpages/wily/en/man1/mate-screenshot.1.html) doesn't seem to offer the option. Neither does [http://manpages.ubuntu.com/manpages/xenial/en/man1/mate-screenshot.1.html](http://manpages.ubuntu.com/manpages/xenial/en/man1/mate-screenshot.1.html)

If you don't mind, you could try `scrot`: ```
EXAMPLE

       scrot '%Y-%m-%d_$wx$h.png' -e 'mv $f ~/shots/'
       This would create a file called something like 2000-10-30_2560x1024.png
       and move it to your shots directory.


```from [http://manpages.ubuntu.com/manpages/wily/en/man1/scrot.1.html](http://manpages.ubuntu.com/manpages/wily/en/man1/scrot.1.html)

Hi vasa1.

How would you add the time so that every screenshot name is unique? Also I'd like to not have the resolution part.

e.g. "Screenshot at 2016-03-19 11:50:12.png" or "2016-03-19 11:50:12.png"

---

### Post by howefield on 2016-03-19
Try something like...

```
scrot '%Y, %B %d, %H:%M:%S - screenshot.png' -e 'mv "$f" ~/Pictures/'
```

---

### Post by vasa1 on 2016-03-19
I was quoting from *man scrot*, but I use the following:
```

# Immediate active window scrot when I press PrntScrn
scrot -b -u ~/Desktop/Screenshots/%b%d%H%M%S.png

# Delayed scrot of full screen when I press Super+PrntScrn (useful for capturing dropdown menus)
scrot -b -d10 ~/Desktop/Screenshots/%b%d%H%M%S.png

# Interactive scrot when I press Shift+PrntScrn
scrot -s ~/Desktop/Screenshots/%Y%m%d%H%M%S.png
```Obviously, you'll prefer your own keyboard shortcuts. I don't like spaces in filenames. And, if you ever want to take more than one screenshot per second, there's *%N* for nano seconds according to *man date* ;)

Scrot, being so light-weight, doesn't have a couple of features other screen capture tools have. It can't paste directly into the clipboard and it can't capture the mouse pointer. But I can live with that ;)

Edit: if you like the shutter sound, you can add```
&& mplayer -really-quiet /home/vasa1/Desktop/MyDesktop/Sounds/camera-shutter.oga
``` to each shortcut. I copied *camera-shutter.oga* from */usr/share/sounds/freedesktop/stereo/camera-shutter.oga*.

Another edit: you may also like to read [Full web-page screenshot with Firefox]("http://ubuntuforums.org/showthread.php?t=2315963") and [Easy Skeezy Date/Time Formatting]("http://www.foragoodstrftime.com/")

---

### Post by Rytron on 2016-03-19
Cheers howefield & vasa1. (:

---

