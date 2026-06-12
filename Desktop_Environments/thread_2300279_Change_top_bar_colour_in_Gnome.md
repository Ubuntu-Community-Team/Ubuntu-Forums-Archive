---
title: "Change top bar colour in Gnome"
date: 2015-10-24
forum: Desktop Environments
---

### Post by benjitz on 2015-10-24
Hello

How do I change the colour of the top bar in Gnome please? It's light grey and I would like it to be black (with white text/icons). I've tried all sorts of things with the Gnome Tweak Tool and Gnome Colour Chooser but I can't seem to ever find out how to make it change colour.

Let me know if you need any further info.

Thanks
Ben

---

### Post by buzzingrobot on 2015-10-24
There are some Gnome extensions that can alter the panel a bit, although I can't recall if any can change its color. Visit extensions.gnome.org and take a look (use Firefox and you can install from the site). 

I think one non-obvious extension -- Activities Configurator -- merits a look, too.

Otherwise, I think the panel's attributes are set in the preprocessed CSS Gnome uses.

---

### Post by benjitz on 2015-10-24
Thanks buzzingrobot - YAWL and Taskbar both looked hopeful as you could change the top panel background colour, but YAWL wanted to put a bunch of additional stuff on the taskbar I don't want which I couldn't seem to completely hide or disable, and Taskbar could only seem to change it to a black->grey gradient fade, oddly.  And neither had any way of changing the text colour! I can't seem to find any further extensions that might do this, but will keep looking.. Is there no simple file I can edit with the RGB code in?

---

### Post by buzzingrobot on 2015-10-25
> **benjitz said:**
> g.. Is there no simple file I can edit with the RGB code in?

With Adwaita, the default theme, I don't think so. I think it's more or less baked in.  But, the theme files are in /usr/share/themes and you could have a look there. Other themes, perhaps, may allow it.

---

### Post by benjitz on 2015-10-25
Thanks, will have a dig.

---

### Post by kurt18947 on 2015-10-25
This has worked for me. I've tried extensions in the past but they had undesirable side effects for me.[INDENT]
Edit the panel section in /usr/share/gnome-shell/theme/gnome-shell.css to:

#panel{
color: #ffffff;
/*background color: black;*/
background-color: rgba(0,0,0,0.6);
/*border-image: url("panel-border.svg") 1;*/
}
where rgba(0,0,0,0.6) is the alpha channel
[/INDENT]

I had to type this rather than copy/paste because I didn't keep the source URL. Hope I've had enough coffee :-).

I founds this useful for HTML color codes and names:
[http://html-color-codes.info/color-names](http://html-color-codes.info/color-names)

[INDENT][/INDENT]

---

### Post by Frogs Hair on 2015-10-25
3rd party themes are available also. 

 [http://gnome-look.org/index.php?xcontentmode=191](http://gnome-look.org/index.php?xcontentmode=191)

---

### Post by deadflowr on 2015-10-25
> **kurt18947 said:**
> This has worked for me. I've tried extensions in the past but they had undesirable side effects for me.[INDENT]
Edit the panel section in /usr/share/gnome-shell/theme/gnome-shell.css to:

#panel{
color: #ffffff;
/*background color: black;*/
background-color: rgba(0,0,0,0.6);
/*border-image: url("panel-border.svg") 1;*/
}
where rgba(0,0,0,0.6) is the alpha channel
[/INDENT]

I had to type this rather than copy/paste because I didn't keep the source URL. Hope I've had enough coffee :-).

I founds this useful for HTML color codes and names:
[http://html-color-codes.info/color-names](http://html-color-codes.info/color-names)


I think you meant the ,06 part is the alpha channel, the proceeding 0's are red green blue settings.
With alpha 1 equals opaque, and 0 equals full-transparent, so 0.6 would set it somewhere in the middle.

Overall +1, though there is a method to do this without having to edit the system file directly.
It involves adding the user themes extension, creating a themes folder in your home folder, creating a css file, and using gnome-tweak-tool to use user themes.
Here's a basic rundown:
[http://rlog.rgtti.com/2012/01/29/how-to-modify-a-gnome-shell-theme/](http://rlog.rgtti.com/2012/01/29/how-to-modify-a-gnome-shell-theme/)

Hope it helps.

---

