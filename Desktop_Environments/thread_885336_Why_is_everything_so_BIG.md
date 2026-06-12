---
title: "Why is everything so BIG?"
date: 2008-08-10
forum: Desktop Environments
---

### Post by dreikin on 2008-08-10
I've been using linux for years, and it always strikes me how everything is so large.  Without meaning to be mean, it's like it's designed for blind people.  Big fonts, massive bolds, tons of space around everything.. What's up with that? (and importantly, aside from the fonts, how do you change it?)

---

### Post by mcduck on 2008-08-10
Change your display resolution to higher one. You can do it in System/Preferences/Screen Resolution.

If there's no higher resolutions available you may need to install the correct drivers for yur graphics adapter. But that depends on what adapter your system has..

The fonts can be configured in System/Preferences/Appearance. Although a higher resolution will also make the fonts smaller.

---

### Post by dreikin on 2008-08-10
Alas, I AM at max resolution.  I'm comparing (and pardon me for saying it) to the sizes I get on various versions of windows on the same machine.  I can adjust the fonts, but the titlebars and such stay the same..

---

### Post by roaldz on 2008-08-10
Perhaps you should post a screenshot.

---

### Post by jrocket on 2008-08-10
> **dreikin said:**
> Alas, I AM at max resolution.  I'm comparing (and pardon me for saying it) to the sizes I get on various versions of windows on the same machine.  I can adjust the fonts, but the titlebars and such stay the same..

i know (i think) what you mean.  before anyone asks, im running 1680x1050, and ive always wondered why things have to be so big.  things like title bars, buttons on the taskbar, etc.  im running gnome, so when i go to the menu, and say, internet, it seems like the bar that highlights the word "Internet" is about twice as tall as it needs to be.  sometimes i boot into windows because its almost a relief to be able to fit more things on the screen, because all their buttons and bars arent oversized.

---

### Post by Vorian Grey on 2008-08-10
Mine is the same as when I ran Windows. On some distros that I've tried, the screen resolution hasn't been right and when it's that way everything does appear big.There is a big difference in how things look on 1024 x 768 and 1440 x 900, for me.

---

### Post by the yawner on 2008-08-10
Yeah, that's why I use a compact theme which uses smaller widgets and stuff. I wish there's a graphical way of adjusting the sizes like how we can adjust the panel size.

Edit: Attached screenshots of Human theme and Clearlooks-Compact for comparision. Note that resolution remained unchanged on both images.

---

### Post by mcduck on 2008-08-10
If your resolution is correct, then it's mostly a question of configuring the font size, and which themes you are using. Different GTK2-themes have different amounts of whitespace, and different Metacity/Emerald/Compiz themes have different sizes for window borders and titlebar.

Also configuring the toolbars to use only icons helps a lot. You can do that in System/Preferences/Appearance. On the Interface-tab set the "Toolbar button labels" to "Icons only".

You can also adjust the toolbar icon spacing a bit, press Alt-F2 and run gconf-editor. Then browse to desktop/gnome/interface and set the "toolbar_icons_style" to "small-toolbar".

For Firefox, go to View/Toolbars/Customize and enable the "Use Small Icons"-option & set the toolbar style to "Icons".

Finally, changing the display dpi setting to correct one for your display size & resolution might help to get the result you like.

edit: I almost forgot the importance of Compact Icon Layout in Nautilus (Edit/Preferences and on the Views-tab enable "Use compact layout"), and the possibility of using the Spatial mode in Nautilus which makes file manager windows a lot more compact, if you can live with spatial file management (Behavior-tab & disable "Always open in browser window."). Using spatial mode is much nicer when you know that opening soemthing with a middle-click will close the current window, this helps you to prevent your screen from filling with nautilus windows..

edit-2: Screenshot of smaller icons in toolbars & spatial mode nautilus windows from my laptop, running at 1280x800.

---

### Post by arsenic23 on 2008-08-10
This thread is interesting, because I find the exact opisite to be true.

I've posted pictures with examples from my PC running at 1680x1050 .

[COLOR="DarkRed"]Image 01:[/COLOR]
Ubuntu main menu height 30px
[COLOR="#8b0000"]Image 02:[/COLOR]
Windows main menu height 35px
[COLOR="#8b0000"]Image 03:[/COLOR]
Ubuntu space between icons 78px
[COLOR="#8b0000"]Image 04:[/COLOR]
Windows space between icons 110px

So maybe I have something setup differnt, or I'm not quite following what we're talking about.  Could someone post images of the problem?  ( I mean of Windows being smaller then Human/Clearlooks/other common theme )

---

### Post by mikjp on 2008-08-10
> **dreikin said:**
> I've been using linux for years, and it always strikes me how everything is so large.  Without meaning to be mean, it's like it's designed for blind people.  Big fonts, massive bolds, tons of space around everything.. What's up with that? (and importantly, aside from the fonts, how do you change it?)

And I did not like the default 10 pt fonts of my desktop. I made for example text under desktop icons 12 pt and bold :lolflag:

mikko

---

### Post by woaibbhemm on 2008-08-12
hello~
    nice   to  meet  you   and     thank  you   for   youe   sharing ,  welcome   to   our   website  !












Welcome to usfine for [buy lotro gold](http://www.usfine.com/Lord-of-the-Rings-Online-US-c-93.html)Age Of Conan gold[/url] and 
[buy runescape gold](http://www.usfine.com/runescape-c-68.html)sevise.

---

### Post by gwi on 2008-09-10
I think I understand what the OP means. I have the same feeling. See attached images. Both are 776 x 284 pixels. The Windows explorer shows a lot more information in that area than Nautilus does. Nautilus has more empty space surrounding the items shown, and I think the icons are too big. There is a way to make them smaller, but that changes the font as well.
Windows is set to use 8pt Tahoma, Nautilus uses 8pt FreeSans.
[IMG]http://www.willegers.net/ubuntu.png[/IMG][IMG]http://www.willegers.net/windows.png[/IMG]

---

### Post by dreikin on 2008-09-14
Indeed.  It's not so much the fonts - those are easy enough to change on their own, and obviously subject to preferences - but the spacing.  It's like the entire system is double-spaced, and there's no way to get it to even 1.5x spaced.

And that applies to more than just the text, too - icons in menu bars, eg..  You can resize the icons (sometimes) but it leaves the space around them.  Looking at Firefox, the 'bookmarks toolbar' icons take up only half the height they're given.  And I'm amazed at the amount of space dedicated to all the buttons and such in programs like the Gimp and InkScape - areas where space for the image(s) is always at a premium.

---

### Post by boteeka on 2008-09-16
I guess is the default theme's fault to have too many spacing. It can be changed with a different theme.

It would be nice if the default theme wouldn't be that big-looking, though.

---

