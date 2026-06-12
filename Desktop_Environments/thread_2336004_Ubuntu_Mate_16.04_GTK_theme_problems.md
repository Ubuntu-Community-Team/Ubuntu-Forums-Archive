---
title: "Ubuntu Mate 16.04 GTK theme problems"
date: 2016-09-03
forum: Desktop Environments
---

### Post by leunam12 on 2016-09-03
HI, I recently upgraded from 14.04 to 16.04 (clean install). I installed my Macbuntu Mavericks theme that I was using in 14.04 (just copied the theme folder to /usr/share/themes) and everything looks great with the only exception of the radio buttons and check boxes that before (in 14.04) had a three dimensional look and now they are invisible unless they are selected and when they are selected all I see is a black dot or a black check mark. I have attached a picture of what it is supposed to look like. Thanks in advance for any help. all other themes look right but this one

---

### Post by leunam12 on 2016-09-03
This is what they look like now:

---

### Post by Dennis N on 2016-09-03
Themes for Ubuntu 14.04 support gtk 3.10, while those for Ubuntu 16.04 need to support gtk 3.18 for best compatablity. Check if there is a updated release of the theme that supports gtk 3.18.

---

### Post by leunam12 on 2016-09-03
There is one but I don't like it because it looks all flat. Is there a way to replace the dull, black and white images in the current theme?

---

### Post by Dennis N on 2016-09-03
> **leunam12 said:**
> There is one but I don't like it because it looks all flat. Is there a way to replace the dull, black and white images in the current theme?

I'm not exactly sure what you refer to by "black and white images" but if you mean lack of color (monochrome) for the icons on the panel(s) and some other places, you can experiment with alternate icon themes - maybe even use the same icon theme as you used in Mate 14.04. It should transfer ok to 16.04.

'Flat' is the new style being used in a lot of themes.

---

### Post by leunam12 on 2016-09-03
Check the picture on my second post. that is how my radio buttons and check buttons look now those images are black and white and flat. If a button is not selected it is invisible now, On the other hand if you look at the first picture you will see that the radio button is supposed to be blue with a treedimensional look with a black outline around it. This is not about icons but the GTK widgets. Thanks

---

### Post by leunam12 on 2016-09-03
This is what the widgets for radio buttons and check buttons look like with another theme selected.

---

### Post by Dennis N on 2016-09-03
> This is not about icons but the GTK widgets. Thanks

I agree. It's a theme problem because the 14.04 theme lacks support for the new gtk version used in Mate 16.04. In fact, I remember having the invisible checkboxes in a previous Mate - maybe 15.04? which I noticed when I tried to use a theme I had used previously - I think it was the Mediterranean Theme.

I also have an Ubuntu Mate 16.04, and I created a Gnome metatheme Greybird-Grey which appears as its own icon in the Appearance Preferences window. Here is how it is defined:

```
dmn@Roxanne:~/.themes/Greybird-Grey$ cat index.theme
[Desktop Entry]
Type=X-GNOME-Metatheme
Name=Greybird-Grey
Encoding=UTF-8

[X-GNOME-Metatheme]
GtkTheme=Greybird
MetacityTheme=Zukitwo-Dark
IconTheme=Mint-X-Grey
CursorTheme=FlatbedCursors.White.Large

```

Greybird has no missing checkbox and radio button problems. Possibly you could find a combination of gtk theme, Metacity theme, Icon theme, and cursor theme that suits you and create your own metatheme.

---

### Post by leunam12 on 2016-09-05
Ok, I'm gonna try to do that.

Thanks

---

