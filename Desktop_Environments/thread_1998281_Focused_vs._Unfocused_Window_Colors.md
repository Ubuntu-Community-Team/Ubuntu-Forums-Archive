---
title: "Focused vs. Unfocused Window Colors"
date: 2012-06-06
forum: Desktop Environments
---

### Post by leandromartinez98 on 2012-06-06
I'm using Ubuntu 12.04.

I would like to
be able to more clearly differentiate an active (focused) from an inactive (unfocused) application.
Currently the only difference between them is the darkness of the title and of the buttons, but this difference is too subtle for me to readily glimpse which window is focused, and I keep typing commands in the wrong window.

Is there anyway to, for example, chance the color of the unfocused window to some other color, for example?

Thanks.

---

### Post by traditionalist on 2012-06-06
Depends on what system you are using. You can use this to set up colours;

[[IMG]http://img687.imageshack.us/img687/5117/ubuntusoftwarecenter001.th.png[/IMG]]("http://img687.imageshack.us/i/ubuntusoftwarecenter001.png/")

Here is an example of a "hybrid" theme using it;

[[IMG]http://img809.imageshack.us/img809/1792/39707552.th.png[/IMG]]("http://img809.imageshack.us/i/39707552.png/")

With nautilus;

[[IMG]http://img24.imageshack.us/img24/3011/pictures003.th.png[/IMG]]("http://img24.imageshack.us/i/pictures003.png/")

"hybrid" because I have used a dark basic gtk3 theme and then also modified the colours etc in the gtk2 programs.

Some info on how to do it here;

[http://ubuntuforums.org/showthread.php?t=1912749&page=3](http://ubuntuforums.org/showthread.php?t=1912749&page=3)

scroll down to get the full info.

I am using this on "GNOME Classic" and "GNOME Classic ( No Effects)". But it will work on most desktop environments. I have tried most.

You can set it up so that active windows have a bright red title bar or similar.

---

### Post by leandromartinez98 on 2012-06-06
This seems to be the tool for it. Now I was trying to use this in Mint with Cinnamon, and some of the colors can be changed, but the title bar of the active windows does not change. Any idea?

---

### Post by traditionalist on 2012-06-06
> **leandromartinez98 said:**
> This seems to be the tool for it. Now I was trying to use this in Mint with Cinnamon, and some of the colors can be changed, but the title bar of the active windows does not change. Any idea?

The tool has no effect on components that are built using gtk3.  I customised quite a lot in Cinnamon and a few other desktop environments, basically just to see if I could do it and learn something about it, but for fundamental changes on a lot of new stuff you need to be using gtk3  stuff.  This is much more difficult.

You can usually find a theme which is close to what you want and customise various other things to suit. All depends on what you want and how much time and effort you are prepared to expend in order to achieve it.  For most people, finding a half way suitable theme is probably the best way  to go. You can't be playing around like this on a production machine anyway.

---

### Post by leandromartinez98 on 2012-06-12
Yeah... I thought I could simply find a "color:" classifier in some theme definition file, and that I would be able to change the color of the title of non-focused windows by changing that.

---

