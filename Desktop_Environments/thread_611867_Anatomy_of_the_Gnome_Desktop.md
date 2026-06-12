---
title: "Anatomy of the Gnome Desktop?"
date: 2007-11-13
forum: Desktop Environments
---

### Post by thelost on 2007-11-13
I'm slightly confused as to what you need to alter to change the appearance of different parts of your system. To me it seems rather fragmented.

GTK themes / Metacity / Emerald - One is a 'toolkit', the next a compositing window manager and the third, well...

So what is the difference?

What is the practical difference of Emerald over GTK?

So basically could someone run down the different decorations. Desktop, Windows, Login, Splash screen etc.

---

### Post by LinuxSoundMan on 2007-11-13
good post. this would answer a lot of my questions regarding gnome.

---

### Post by ericesque on 2007-11-13
Actually, metacity and emerald are probably more akin than emerald and GTK.

GTK handles widgets.  Things like the appearance of tabs, radio buttons, check boxes, scroll bars, and 3d buttons.

Metacity is the classic window border manager.  So that basically covers the title bar on a window and the min,max,close buttons.

Emerald is also a border manager-- but emerald is used with a compositing engine like Compiz Fusion.

I'm sure there's more to it, but that seems to be a basic functional understanding.

You may also want to check out gnome-look.org 
there are links along the left hand side--including GTK, Metacity, and Emerald.  Peruse some of the screenshots for themes that people have created.  It should help emphasize how each fit into the puzzle.

---

### Post by LinuxSoundMan on 2007-11-13
hmmm...i better hit the books on this one. it does seem somewhat fragmented. but i guess  once you do some extensive reading it wont be so hard to understand.

---

### Post by bmccullo on 2007-11-13
I don't really understand this topic, either. Are metacity or emerald used by default?

---

### Post by rundee_f on 2007-11-14
actually emerald can do all if u can configure it in the right way.. and i can't. :lolflag:

---

### Post by thelost on 2007-11-14
> **bmccullo said:**
> I don't really understand this topic, either. Are metacity or emerald used by default?

I believe Metacity is the default window decorator. However Emerald works with Compiz Fusion to give compositing effects (think wobbly windows etc).

You can test this easily if you have the Compiz Fusion Icon in your system tray. Change the Window Decorator to GTK Window Decorator (Metacity) and it will show your current Metacity theme on windows; Switch back to Emerald and it will show the Emerald Theme. This is also useful if you want to run a GTK theme but have all the special FX.

I'm still not sure what the benefits of Emerald themes are over Metacity? Better integration with compositing effects?

---

### Post by mcduck on 2007-11-14
> **bmccullo said:**
> I don't really understand this topic, either. Are metacity or emerald used by default?

Metacity is the default window manager in Gnome. Window manager allows programs to run in windows and makes it possible for you to move those windows around the screen. Window manager also handles window borders, title bars and so on.

Compiz is another window manager, but it also includes compositing engine which allows advanced effects, transparency, drop shadows and so on. It can use different window decorators to draw window borders, one of these is Emerald, but by default it uses CGWD which uses same themes as Metacity does.

GTK is toolkit for creating graphical user interfaces for programs. Changing GTK theme changes how your programs look like.

---

### Post by thelost on 2007-11-14
> **mcduck said:**
> Metacity is the default window manager in Gnome. Window manager allows programs to run in windows and makes it possible for you to move those windows around the screen. Window manager also handles window borders, title bars and so on.

Compiz is another window manager, but it also includes compositing engine which allows advanced effects, transparency, drop shadows and so on. It can use different window decorators to draw window borders, one of these is Emerald, but by default it uses CGWD which uses same themes as Metacity does.

GTK is toolkit for creating graphical user interfaces for programs. Changing GTK theme changes how your programs look like.

I think that for anyone switching it's definitely a bit confusing the way that different things apply under different circumstances. I for one miss msstyles - I feel dirty saying that.

Anyhow, I want go go ahead and port b0se's gui.relax theme from Windows XP as it's hands down the best theme I've seen on any platform and I used it comfortably for a long time when running Windows.

Would it be better/simpler to port it to Compiz or GTK/Metacity?

I assume if I port it to Compiz I still would need to do all the widgets for GTK if I wanted it to be a complete theme.

hrmph, I think I'm confusing myself again! :confused:

ps, for your enjoyment, this is b0se's [gui.relax]("http://b0se.deviantart.com/art/GUI-Relax-45441528"):

[IMG]http://fc03.deviantart.com/fs15/i/2006/361/9/7/GUI_Relax_by_b0se.png[/IMG]

---

### Post by mcduck on 2007-11-14
> **thelost said:**
> I think that for anyone switching it's definitely a bit confusing the way that different things apply under different circumstances. I for one miss msstyles - I feel dirty saying that.

Anyhow, I want go go ahead and port b0se's gui.relax theme from Windows XP as it's hands down the best theme I've seen on any platform and I used it comfortably for a long time when running Windows.

Would it be better/simpler to port it to Compiz or GTK/Metacity?

I assume if I port it to Compiz I still would need to do all the widgets for GTK if I wanted it to be a complete theme.

hrmph, I think I'm confusing myself again! :confused:

You'd still need to port it to both GTK and then some window manager. Compiz is, basically, just a window manager like Metacity is. It doesn't handle your application themes.

So you'd have to port the look of applications to a GTK theme, and then make a window manager theme for either Metacity or Emerald. (Compiz can use both Emerald and Metacity themes, as it has many different Window Decorators, programs that handle the drawing of window borders).

What comes to making window themes, Emerald has a nice program that makes theming easier, whereas both GTK and Metacity themes are mostly created by editing text files by hand.

---

### Post by thelost on 2007-11-15
> **mcduck said:**
> You'd still need to port it to both GTK and then some window manager. Compiz is, basically, just a window manager like Metacity is. It doesn't handle your application themes.

So you'd have to port the look of applications to a GTK theme, and then make a window manager theme for either Metacity or Emerald. (Compiz can use both Emerald and Metacity themes, as it has many different Window Decorators, programs that handle the drawing of window borders).

What comes to making window themes, Emerald has a nice program that makes theming easier, whereas both GTK and Metacity themes are mostly created by editing text files by hand.

By that do you mean the Emerald Theme Manager, or something?

---

