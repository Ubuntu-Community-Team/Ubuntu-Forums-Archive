---
title: "[SOLVED] Changing the Gnome Panel?"
date: 2007-08-06
forum: Desktop Effects &amp; Customization
---

### Post by isaacj87 on 2007-08-06
**UPDATE:** 
I've included my way of editing "gtkrc" in order to ensure full transparency. You can find it on the second page. 
Thanks for all the help.


Hey guys,

I'm using the Ubuntu Studio Theme and I would like to maintain the current look, but would like to make my top panel transparent. Every time I change the panel to be transparent it seems the theme still seems to cling on...How can change the look of my panel, but not have to use a completely different theme?

I've included a picture to better illustrate my point :)

---

### Post by nichipet on 2007-08-06
Do you mean how at the top you can barely see there is a difference between the wallpaper and the panel? I'm not on Ubuntu right now, but I just did something like this. I think it's right click on the panel, choose Properties (or similar), go to the background part of Properties and there is a slide for transparency. Take it all the way to the left, I think. That's the best you will get without a change of theme or some sort of config file hack.

---

### Post by superbungalow on 2007-08-06
use, a background image (in properties) You can find them on gnome-look.org

---

### Post by isaacj87 on 2007-08-06
> **superbungalow said:**
> use, a background image (in properties) You can find them on gnome-look.org

Tried that, still has part of the system theme left. :(

---

### Post by nichipet on 2007-08-06
Ooh, you mean how the menu bar and icons on the right are not transparent at all. I think the only solution, if a background image does not work, is to hack the theme directly.

---

### Post by isaacj87 on 2007-08-06
> **nichipet said:**
> Ooh, you mean how the menu bar and icons on the right are not transparent at all. I think the only solution, if a background image does not work, is to hack the theme directly.


Ah, okay...will do, as soon as I know how! haha...can someone explain where I need to edit?

---

### Post by Kushkah on 2007-08-09
> **nichipet said:**
> Ooh, you mean how the menu bar and icons on the right are not transparent at all. I think the only solution, if a background image does not work, is to hack the theme directly.

I've been trying to do just that for a theme I downloaded as well, can anyone explain how to go about doing this? I've been looking around for a few days now with no luck.

---

### Post by martin_prince on 2007-08-09
Yes, that is correct, the theme you are using uses a background image for the panel.  You need to modify this image to be somewhat transparent (can easily be done in Gimp) or just choose a different theme that uses a solid color instead of a bg image.

To change the image, you need to browse to the folder in which the image files for your theme are stored.  There's not a standard location, I can tell you mine looks like this:
```
/home/landon/.themes/theme_name/gtk-2.0/Menu-Menubar
```
if you can find the background file, then I think all you need to do is make it a bit transparent, then restart the panel...  Good luck!

---

### Post by isaacj87 on 2007-08-09
thanks! that was helpful, but when I find the image how do I make the original transparent in gimp?

---

### Post by cookieofdoom on 2007-08-09
Adjust the opacity of the layer in the layers tab.

---

### Post by infra_red_dude on 2007-08-10
it doesn't work. no matter what the extreme left (gnome menu) and the extreme right including tray are not transperent. 

seeking help.

---

### Post by isaacj87 on 2007-08-10
what is your current theme called? If you plan on making the entire panel transparent I can help you...is it a downloaded theme or one that came with ubuntu (or the ubuntustudio panel)?

---

### Post by simianstyle on 2007-08-15
Is it possible to get rid of the drop shadow on the top panel using compiz-fusion?

---

### Post by 00l0 on 2007-08-16
> **isaacj87 said:**
> what is your current theme called? If you plan on making the entire panel transparent I can help you...is it a downloaded theme or one that came with ubuntu (or the ubuntustudio panel)?

I would love to do THAT exactly, make my entire panel transparent, i have no idea how to edit my gtkrc file inside the .themes directory. I tried editing the .PNG files for higher transparency (themename/gtk2.0/menu-menubar/ folder) but it just doesn't work, i don't understand it. 

ty!

---

### Post by isaacj87 on 2007-08-17
> **00l0 said:**
> I would love to do THAT exactly, make my entire panel transparent, i have no idea how to edit my gtkrc file inside the .themes directory. I tried editing the .PNG files for higher transparency (themename/gtk2.0/menu-menubar/ folder) but it just doesn't work, i don't understand it. 

ty!

Well, if it's a theme that you installed from gnome-look.org or somewhere similar, you'll find that in your .themes folder (which you found). If you are using a pre-installed theme (clearlooks, crux, ubuntu-studio) than those themes are found in /usr/share/themes.

To edit the gtkrc file, simply open up terminal, navigate to the folder and type "gksudo gedit gtkrc"
(obviously without the quotes!). Here I'll give you an example of how I modified my Ubuntu-Studio theme.

I opened up terminal, went to /usr/share/themes/UbuntuStudio/gtk-2.0, then I did: 

```
gksudo gedit gtkrc
```

I commented out any line calling for the panel background image. I'm not going to paste the entire file because your theme will probably be different and it's a long file.

```

[B]#pixmap_path "/usr/share/themes/UbuntuStudio/gtk-2.0/panel/"
#include "panel/panel.rc"[/B]

#style "panelbg"
#{
#  xthickness        = 0
#  ythickness        = 0
#  bg_pixmap[NORMAL] = "panel.png"
#}

#class "*Panel*" style "panelbg"
#class "*panel*" style "panelbg"
#class "*notif*" style "panelbg"
#class "*Notif*" style "panelbg"
#class "*Tray*"  style "panelbg"
#class "*tray*"  style "panelbg"

#class "PanelMenuBar"   style "panelbg"

```

Basically, anything that was related to the panel or panelbg I commented out using a "#" which tells the file I'm not using those lines. The lines that are bold are *technically *the only lines I needed to comment out, but I decided to go ahead and comment everything related to panel out just to be thorough. Then I saved, and made my panel transparent! 

**Remember, what I pasted above has been copied from my theme and is not complete, merely just pieces of a much longer file and what I pasted is in no particular order. So, don't just copy and paste what I put up there, as your "gtkrc" will most likely be significantly different. Unless, you're using the UbuntuStudio theme.**

I'm not exactly sure if that's how your* supposed* to do it, I'm just following the "if it works, then it works" policy. ;)

 Let me know if you still need help. :)

---

### Post by 00l0 on 2007-08-22
> **isaacj87 said:**
> Well, if it's a theme that you installed from gnome-look.org or somewhere similar, you'll find that in your .themes folder (which you found). If you are using a pre-installed theme (clearlooks, crux, ubuntu-studio) than those themes are found in /usr/share/themes.

To edit the gtkrc file, simply open up terminal, navigate to the folder and type "gksudo gedit gtkrc"
(obviously without the quotes!). Here I'll give you an example of how I modified my Ubuntu-Studio theme.

I opened up terminal, went to /usr/share/themes/UbuntuStudio/gtk-2.0, then I did: 

```
gksudo gedit gtkrc
```

I commented out any line calling for the panel background image. I'm not going to paste the entire file because your theme will probably be different and it's a long file.

```

[B]#pixmap_path "/usr/share/themes/UbuntuStudio/gtk-2.0/panel/"
#include "panel/panel.rc"[/B]

#style "panelbg"
#{
#  xthickness        = 0
#  ythickness        = 0
#  bg_pixmap[NORMAL] = "panel.png"
#}

#class "*Panel*" style "panelbg"
#class "*panel*" style "panelbg"
#class "*notif*" style "panelbg"
#class "*Notif*" style "panelbg"
#class "*Tray*"  style "panelbg"
#class "*tray*"  style "panelbg"

#class "PanelMenuBar"   style "panelbg"

```

Basically, anything that was related to the panel or panelbg I commented out using a "#" which tells the file I'm not using those lines. The lines that are bold are *technically *the only lines I needed to comment out, but I decided to go ahead and comment everything related to panel out just to be thorough. Then I saved, and made my panel transparent! 

**Remember, what I pasted above has been copied from my theme and is not complete, merely just pieces of a much longer file and what I pasted is in no particular order. So, don't just copy and paste what I put up there, as your "gtkrc" will most likely be significantly different. Unless, you're using the UbuntuStudio theme.**

I'm not exactly sure if that's how your* supposed* to do it, I'm just following the "if it works, then it works" policy. ;)

 Let me know if you still need help. :)

hey isaac thank you very much! it really workd as you said, actually that's not the way i was trying to edit the theme, but it works as long as i don't have a menubar in the panel, 
I'd have liked to know how to edit without having to "not include" those .rc but that's fine :]

if you think you or anyone else can figure out how to do it have  a look at the gtk theme, i couldnt remember where i dled it from so i just uploaded to rapidshare,

thank you

[http://rapidshare.com/files/50545827/Mint.tar.gz.html](http://rapidshare.com/files/50545827/Mint.tar.gz.html)

---

