---
title: "Nautilus background"
date: 2007-09-05
forum: Desktop Environments
---

### Post by nstiesi on 2007-09-05
Just curious; I set a png image as the nautilus folder background.  The png is partly transparent, and when set as the desktop background, it shows transparency.  However, when set as the window background in nautilus, it is just flat grey.  Is it possible to get nautilus to recognize it?  Is there something I have to do to the picture to make that work?

Nick

Using Ubuntu 7.07

---

### Post by nstiesi on 2007-09-05
upon further review, the png background is being recognized as transparent, but nautilus is also specifying a background color, which is showing through the transparent png.  Is there any way to turn the background color off, so that my desktop background shows through?

---

### Post by spupy on 2007-09-05
You want the background of Nautilus to be semi-transparent, to see the desktop? If that is the case, you need compositing. It most probably it wont happen other way.

---

### Post by nstiesi on 2007-09-05
> **spupy said:**
> You want the background of Nautilus to be semi-transparent, to see the desktop? If that is the case, you need compositing. It most probably it wont happen other way.

Is there a project I should refer to, or is it not a reality right now?

Oh, and I have beryl, but am rather new to it....are there any options I should be looking for to that end.  I guess the root of my problem is that I have a really nice emerald theme with black transparencies, but haven't found a gnome theme to match.  I have the panels and terminal set to black transparent, but windows and menus don't quite match.

---

### Post by spupy on 2007-09-05
Beryl should be able to do it. But i am sorry - i can't help you with beryl. It doesn't run on my PC.

---

### Post by mcduck on 2007-09-06
Nautilus doesn't support window transparency as GTK2 doesn't support it., so you will only be able to see the background color through tranparent images. With Beryl/Compiz or other compositing manager you can make the whole window transparent, but that will also make your icons and text and everything transparent. It works but it's not the same thing and doesn't look as nice.

Some programs add their own tranparency support (like gnome-terminal) but I would not expect Nautilus to do that. We can only hope that GTK will some day get support for transparency.

---

