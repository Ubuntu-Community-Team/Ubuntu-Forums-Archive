---
title: "Just What Is Compiz?"
date: 2009-05-09
forum: General Help
---

### Post by ftabor on 2009-05-09
What is it's real function?  Is it essential or absolutely needed?  Or is it just lipstick on a pig?

---

### Post by hw-tph on 2009-05-09
It is a window manager with support for compositing. While compiz in itself is not essential, you most likely will want a window manager of some sort so you can move windows around and resize them. There are tons of alternatives if you don't like compiz. Some offer really cool features, others are just very fast and simple.

---

### Post by mkvnmtr on 2009-05-09
Compiz is the program that does all the really neet visual effects that so many like. I don't find it required and it is a resource drain on my old under powered computers so I uninstall everything compiz related. I guess for me it is lipstick on a pig but it does some very neat stuff if you like that kind of thing.

---

### Post by CatKiller on 2009-05-09
> **ftabor said:**
>  Is it essential or absolutely needed?

No window manager is essential. You can do anything on your computer that you need to using just the command-line. That's how the server installs work.

But having decided that you'd like to see pretty pictures for doing stuff, you need to pick a window manager that has the features you want. The features that are required differ for each user, which is why there are so many to choose from. Each has a different focus for which features get development priority; some might choose to go for speed at all costs, some might choose to go for integration with a desktop environment, and so on. Compiz focuses on things that can be done with hardware-accelerated compositing, and so has features that other window managers don't. Whether these features are desirable for you is entirely up to you. Personally, I find the live window previews and the Scale plugin really useful. The rest is just shiny icing on the cake.

EDIT:

> **mkvnmtr said:**
> I don't find it required and it is a resource drain on my old under powered computers so I uninstall everything compiz related.

A hardware-accelerated window manager actually **helps** performance because it offloads drawing windows from the processor to specialised hardware. It's the plugins that can't be offloaded because the hardware doesn't accelerate those operations that slow things down again, since those effects have to be calculated by the processor. You should still be able to increase performance using Compiz if you turn off those effects that can't be accelerated by your graphics card.

---

### Post by colau on 2009-05-09
> **ftabor said:**
> What is it's real function?  Is it essential or absolutely needed?  Or is it just lipstick on a pig?
Compiz does have some excellent desktop effects.
[compiz 1]("http://lifehacker.com/software/pretty-and-productive/power-up-your-linux-desktop-with-compiz-fusion-291002.php") 
[compiz 2]("http://chris.pirillo.com/top-five-reasons-to-love-compiz-fusion-in-linux/")

---

### Post by ftabor on 2009-05-09
Appreciate the comments and replies.  It just keeps showing up as #3 on the list for memory usage just behind FireFox and X-Org.  I guess I'll just leave it alone.  The defaults seem to work just fine for me.

---

### Post by MaxIBoy on 2009-05-09
Compiz is just a "drop-in" window manager, intended to replace your Desktop Environment's (DE's) default choice. You can run it without a DE, but it'll be basically useless. If you like, you can pick a different window manager, one without any compositing effects. 


GNOME's (and by extension, Ubuntu's) default window manager is Metacity. KDE's (and by extension, Kubuntu's) default window manager is Kwin, which incidentally also has 3D effects. Xfce (as in Xubuntu) uses Xfwm4. These window managers are part of their respective DEs. On their own, they are useless.


There are "light" window managers, intended to be run independent of a DE. They are incredibly small, some as small as 18 Kb. The ability to launch programs is built into the WM. Examples include blackbox and its ilk (openbox and fluxbox.) Some "light" WMs are "tiling" WMs, like ion3, wmii, and awesomeWM.


Then there are DEs built around a "light" window manager. For example, openbox runs fine without a DE, it has its own little built-in panel and everything. However, LXDE (Lightweight X11 Desktop Environment) uses openbox as its WM, supplying LXpanel as its own panel program.



So yeah, there are plenty of choices besides compiz which will run faster, but compiz has the best graphics, and on anything newer than 2004, it'll run fast enough not to make a difference. Remember: unused memory is wasted memory!

---

### Post by Tipped OuT on 2009-05-09
It's a DWM (Desktop Window Manager) as Windows Aero is to Vista.

---

### Post by MaxIBoy on 2009-05-09
Actually, Desktop Window Manager is the specific name of the WM in Windows (Aero is just a marketing name.) Dynamic Window Manager is the name of the smallest WM I know of, 18 Kb. 

WM is a category, DWM and DWM are both examples. 


Minor detail, but things like that bug me.:P

---

### Post by learningcurb on 2009-05-09
Compiz also makes it easier to navigate multiple desktops.  Being able to grab a window title and drag it to the left or right edge of the screen to move it to another desktop is handy.  As is using the scroll wheel or both mouse buttons to flip between desktops quickly.

---

### Post by DeMus on 2009-05-10
> **ftabor said:**
> What is it's real function?  Is it essential or absolutely needed?  Or is it just lipstick on a pig?

I see it as lipstick on a pig. Why multiple desktops, spinning around on a cube, windows getting smaller and larger instead of having the new size instantly, wobbly windows, and whatever more?
I have experimented with Compiz but uninstalled it immediately. Now I have set all effects to none and my desktop is nice and fast, just as I like it.

Another thing, Jaunty and Compiz don't go together so well. If you read the threads here you find many problems being caused by Compiz.

Just set your effects to none and have a fast desktop. Enjoy.

---

### Post by collinp on 2009-05-10
Compiz is a compositing Window Manager with support for multiple plugins and window decorators. It also improves upon some window manager/desktop environment functions. Compiz Fusion is the union of Beryl and Compiz, some people call it an expansion pack for Compiz. They are both extras, you don't need them. Using them is your choice; I prefer the pretty desktop.

---

