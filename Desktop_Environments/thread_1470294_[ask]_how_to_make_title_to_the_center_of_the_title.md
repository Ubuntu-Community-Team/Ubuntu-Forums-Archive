---
title: "[ask] how to make title to the center of the title bar on Lynx 10.04"
date: 2010-05-02
forum: Desktop Environments
---

### Post by AbangBoltok on 2010-05-02
hello everyone..

:D

after upgrading from Karmic Koala 9.10 to Lucid Lynx 10.04, i notice something different with title bar on every window opened.

for example:
"Google - Mozilla Firefox" is not at the middle of the window title. and on Lynx it's on the left.

if it's possible, how can i move it to the middle??

btw, i'm using default theme. :D

thanks..

---

### Post by Minsky on 2010-05-02
Just a suggestion, it could be that you're using the Emerald window manager. If so, then you need to go into Emerald Theme Manager and alter the title bar settings in there.

---

### Post by AbangBoltok on 2010-05-03
thanks.

on default theme, the title is aligned to the leftside.
but if i use other theme from Karmic Koala, it's at the center of the title bar.

i just cant find fancy theme for lynx with "close, minimize and maximize" button on the top left hand side.

sorry of my English, it's not my first or second language :D

---

### Post by Chromagnum on 2010-05-03
So basicly you want the button to the left and the center title. Okay, since I don't know how to alter title text position, I'm just gonna give you some ideas. How about this:

1. Choose whatever theme that have center title.

2. To change the button to the left (Lucid style):

[INDENT]Alt + F2

type: gconf-editor

go to: apps > metacity > general

look for button_layout, and change it to this:

```
close,minimize,maximize:
```

if you also want menu button, then change to this:

```
close,minimize,maximize:menu
```[/INDENT]

---

### Post by Sicadastra on 2011-04-28
I'd like to revive this thread if possible. I've updated to 10.10 and my title bar (the upper most part of a window ie. "Ubuntu Start Page - Mozilla Firefox" is also aligned to the left instead of center. I'm not sure where to tweak this as I can't find it on gconf-editor (I'm not that good with it) or Ubuntu Tweak.

If anyone who's using 10.10 already who altered their title bar position, I hope they can help me and others too. 

Thanks.

---

### Post by Copper Bezel on 2011-04-28
It's not a gconf setting; it's a part of the Metacity theme. This bit, in the Metacity theme's .xml, here aligned to the left:

```
<!--
		Title Text
	-->
	<draw_ops name="title-text-focused">
		<title color="#bbbbbb" **x="5"** y="((height - title_height) / 2)"/>
	</draw_ops>

	<draw_ops name="title-text-unfocused">
		<title color="#7b7b7b" **x="5"** y="((height - title_height) / 2)"/>
	</draw_ops>

	<draw_ops name="blank">
	</draw_ops>

	<!--
```

Centered looks more like this:

```
x="(width - title_width) / 2 +1"
```

If you're using Emerald, as noted earlier, it's in the Emerald theme settings.

---

### Post by Sicadastra on 2011-04-28
> **Copper Bezel said:**
> It's not a gconf setting; it's a part of the Metacity theme. This bit, in the Metacity theme's .xml, here aligned to the left:

```
<!--
        Title Text
    -->
    <draw_ops name="title-text-focused">
        <title color="#bbbbbb" **x="5"** y="((height - title_height) / 2)"/>
    </draw_ops>

    <draw_ops name="title-text-unfocused">
        <title color="#7b7b7b" **x="5"** y="((height - title_height) / 2)"/>
    </draw_ops>

    <draw_ops name="blank">
    </draw_ops>

    <!--
```Centered looks more like this:

```
x="(width - title_width) / 2 +1"
```If you're using Emerald, as noted earlier, it's in the Emerald theme settings.

Thank you for this. I don't have Emerald and I don't think I'd bother installing it for a minor, albeit bothering setting.

---

