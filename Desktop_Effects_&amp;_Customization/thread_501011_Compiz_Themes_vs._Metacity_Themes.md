---
title: "Compiz Themes vs. Metacity Themes"
date: 2007-07-14
forum: Desktop Effects &amp; Customization
---

### Post by Mongoose.wa on 2007-07-14
I'm interested in theming my desktop, and I came across [GNOME-Look.org](http://www.gnome-look.org/). I've got a couple questions:

1. What's the difference between Metacity and Compiz themes? I'm running Compiz Fusion and Emerald.
2. How do you install icon sets, splash screens, and fonts?
3. How exactly do you theme menu panels? I know you have to create a custom background image, but do you create one big image (50x1024 or something?) or can you create a 1x50 gradient and have it repeat? And how do you change the panel font color? When I set the background color to black, Applications, Places, etc become unreadable.

---

### Post by Mongoose.wa on 2007-07-15
Bump

---

### Post by hyperair on 2007-07-15
Metacity themes, if I'm not mistaken, include GTK theming. So, installing a Metacity theme (or Gtk theme) will change the appearance of your panel, and your controls, such as scrollbars, buttons, and whatnot. 

Compiz themes, or more accurately Emerald themes, since Emerald is in charge of theming, only change the window borders. That means that any fancy titlebar that you see, the minimize maximimze, and close buttons, additions of buttons, change of layout of the titlebar, colour of the titlebar, glow or whatnot, that's all Emerald. Anything more than that, Emerald doesn't touch.

---

### Post by Mongoose.wa on 2007-07-15
Ah, OK. So, once you install a metacity theme, you can change it via Applications > Desktop Properties > Themes or w/e?

---

### Post by mcduck on 2007-07-15
1. The difference between Metacity and Compiz themes is about the same as between Metacity and Emerald themes..

2. drag&drop the icon package into System/Preferences/Themes window or extract it yourself into ~/.icons (/usr/share/icons for all users). Font can be just dropped into ~/.fonts (or /usr/share/fonts for all users). It's a bit hard to say anything about splash screens unless you can tell which splash screen you are talking about..

3. Both one big picture and tileable small ones work, it just depends on what kind of picture you want. The panel font colors can be changed by creating a file called .gtkrc-2.0 and adding there some lines to change the color. Search the forum about that, there are endless amounts of threads abut panel font colors here..

---

### Post by eentonig on 2007-07-15
yes,

And installing is as easy as downloading the archived file and dragging it onto to application.

If it doesn't work like that, it might be that the theme is packaged in yet another compressed format. Just unpack once and try again.

If you want to use the theme for all users in your system, you'll have to manually unpack it completely under /usr/share/themes. But you'll need root privileges to save them there.

---

### Post by Mongoose.wa on 2007-07-15
Alright. Thanks for the help. :)

---

### Post by mcduck on 2007-07-15
> **hyperair said:**
> Metacity themes, if I'm not mistaken, include GTK theming. So, installing a Metacity theme (or Gtk theme) will change the appearance of your panel, and your controls, such as scrollbars, buttons, and whatnot. 

Compiz themes, or more accurately Emerald themes, since Emerald is in charge of theming, only change the window borders. That means that any fancy titlebar that you see, the minimize maximimze, and close buttons, additions of buttons, change of layout of the titlebar, colour of the titlebar, glow or whatnot, that's all Emerald. Anything more than that, Emerald doesn't touch.
No. Metacity themes are just themes for Gnome's default window manager, Metacity. So they only change your window borders just like Compiz and Emerald themes do.

(But as Metacity themes are installed into same directory where GTK2 themes go, it's possible to pack both GTK2 and Metacity theme into one archive..)

---

### Post by hyperair on 2007-07-15
Ah that'll explain why I mixed up Metacity and Gtk2 themes.

Anyway, I believe Compiz themes are almost non existent, unless they're just a compressed package which contain a whole bunch of stuff, like cubecaps, emerald themes, snowflakes, and whatnot.

---

### Post by SkiesOfAzel on 2007-07-15
Compiz themes do exist, these are themes for the previous compiz decorator that evolved into emerald. Some of them still work with emerald.

---

### Post by hyperair on 2007-07-15
I'd actually call them CGWD themes, since they actually belong to the decorator, as opposed to Compiz. And I still haven't come across any CGWD theme that doesn't work on Emerald. All you have to do is rename .cgwdtheme to .emerald isn't it? =P

Call me fussy, but I just felt I had to clear up this matter sometime ><

---

### Post by SkiesOfAzel on 2007-07-17
Lol but i have, i just don't remember anymore which ones were that didn't work . As for compiz and themes, although compiz is a wm , it needs a decorator to apply skins for it and gtk-decorator was a metacity emulator . So in my view , cgwd was something like a skinning engine for compiz ;) .

---

### Post by Espreon on 2007-07-17
Emerald themes have transparent window borders, Metacity themes can have them too I think (if they are running in Heliodor [Beryl's GTK decorator] or Compiz GTK Decorator)

---

### Post by hyperair on 2007-07-17
Actually Heliodor and Aquamarine work in both Compiz and Beryl. Emerald didn't work in Compiz, but for Compiz Fusion, it works.

Metacity themes can have translucent window borders using gtk-window-decorator or Heliodor, but the location of the translucency cannot be customized, as opposed to Emerald's themes.

---

