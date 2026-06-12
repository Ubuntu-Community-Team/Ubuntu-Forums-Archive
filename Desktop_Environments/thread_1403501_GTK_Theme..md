---
title: "GTK Theme."
date: 2010-02-10
forum: Desktop Environments
---

### Post by Jefferythewind on 2010-02-10
How do I change gtk themes in 9.10?  

I guess my real question is how do i change the way the content of the windows looks.  For example when i use an Emerald theme from here:
[URL="http://compiz-themes.org/content/show.php/vsv-blackgreen-theme?content=119564"]
http://compiz-themes.org/content/show.php/vsv-blackgreen-theme?content=119564[/URL]

My window does not get completely transparent looking, the border of the window changes but the inside remains the same.

---

### Post by mcduck on 2010-02-10
> **Jefferythewind said:**
> How do I change gtk themes in 9.10?  

I guess my real question is how do i change the way the content of the windows looks.  For example when i use an Emerald theme from here:
[URL="http://compiz-themes.org/content/show.php/vsv-blackgreen-theme?content=119564"]
http://compiz-themes.org/content/show.php/vsv-blackgreen-theme?content=119564[/URL]

My window does not get completely transparent looking, the border of the window changes but the inside remains the same.

You can change the themes in System/PReferences/Appearance.

(and no, Emerald themes are not even supposed to change anything else than the window borders. Emerald is just a window decorator plugin for Compiz window manager, and has nothing to do with how your applications look like. That's defined by the GTK theme you are using).

The theme you linked has a link to a GTK theme, so you'll have to download and install that separately. But even doing that won't make your applicatiosn transparent, the transparent window in the screenshot is Gnome-terminal, which does it's own transparency, defined from Gnome-terminal's settings.

---

### Post by Jefferythewind on 2010-02-10
ooooohhhh,
  Thanks for the info.  I understand now.

  When i try ot change the colors of the gnome theme, there is no adjustment for the transparency (like the adjustment for the panel background color), so does that mean it is impossible to make this background transparent?

---

### Post by mcduck on 2010-02-10
> **Jefferythewind said:**
> ooooohhhh,
  Thanks for the info.  I understand now.

  When i try ot change the colors of the gnome theme, there is no adjustment for the transparency (like the adjustment for the panel background color), so does that mean it is impossible to make this background transparent?

GTK doesn't really have any support for transparency yet (although there is some development towards making that possible in the future).

Murrine-based themes can do transparency, but your applications themselves must support it, simply using a murrine-based theme alone won't make all your programs use transparency. For most programs that emans that you have to either compile the program yourself with a patch toa dd the RGBA support, or if you are lucky the support can be added through a plugin.

[http://www.cimitan.com/murrine/rgba-support/list]("http://www.cimitan.com/murrine/rgba-support/list")

Of course you can just use Compiz (or some other compositing manager) to make your windows transparent, but it won't be able to make any difference between background and actual content like text and images, it will just make everything transparent. Which is usually more annoying than nice looking.. :/

---

### Post by Jefferythewind on 2010-02-10
mcduck,

  thanks for the info.  I don't think I am ready to try to compile all my apps myself yet, just to make them transparent, haha.  But i think that would be a fun and informative project for me some time in the future.  
  I also agree with you that making the entire window transparent is just weird looking, and doesn't add much the the desktop experience.  I think what I have here with background color matching desktop looks pretty close.

---

### Post by kstam28 on 2010-02-11
you can make your windows transparent by using compiz config and clicking on the trailfocus plugin. click over to the appearance tab and under opacity you can change the transparency of focused and unfocused windows.i set my focused at 90 and i can see everything fine and it gives the windows a nice transparent tint. you can also go to the reflection plugin and make the reflection image your desktop image and that way all you see through your window is your desktop image instead of the windows behind it. i've also gone to the move windows plugin and you can change the transparency their alittle more than what you have it set at for the trailfocus is at so when you move the window you *can* see the other windows behind it.

---

