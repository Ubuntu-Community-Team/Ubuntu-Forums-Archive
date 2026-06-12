---
title: "Playing around with &quot;Pretty Colors&quot; in GRUB..."
date: 2005-05-12
forum: Desktop Environments
---

### Post by Cool_dude_Prav on 2005-05-12
Hi ppl,

I was trying to play around with GRUB and I found out the "pretty colors" part.

I thought maybe I could try out some cool combos with it...

It doesn't support colors like Grey(or is it Gray?) and so on... 

So, here's the big Questions...

:arrow: What colors are supported on GRUB's menu.lst?

:arrow: How to use "other" colors - can RGB colors be used as in HTML?

This sure will make some heads ponder :roll:

---

### Post by Buffalo Soldier on 2005-05-12
From [http://www.gnu.org/software/grub/manual/grub.html#color](http://www.gnu.org/software/grub/manual/grub.html#color)

> **color** *normal* [highlight]

[indent]Change the menu colors. The color normal is used for most lines in the menu (see Menu interface), and the color highlight is used to highlight the line where the cursor points. If you omit highlight, then the inverted color of normal is used for the highlighted line. The format of a color is foreground/background. foreground and background are symbolic color names. A symbolic color name must be one of these:[list][*] black
[*] blue
[*] green
[*] cyan
[*] red
[*] magenta
[*] brown
[*] light-gray[/list]
[indent]These below can be specified only for the foreground:[/indent][list][*] dark-gray
[*] light-blue
[*] light-green
[*] light-cyan
[*] light-red
[*] light-magenta
[*] yellow
[*] white[/list]

But only the first eight names can be used for background. You can prefix blink- to foreground if you want a blinking foreground color.

This command can be used in the configuration file and on the command line, so you may write something like this in your configuration file:```
# Set default colors.
color light-gray/blue black/light-gray
          
# Change the colors.
title OS-BS like
color magenta/blue black/magenta
```[/indent]

---

