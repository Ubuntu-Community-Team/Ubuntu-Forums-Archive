---
title: "Window borders"
date: 2009-11-10
forum: Desktop Environments
---

### Post by Uubnewb on 2009-11-10
When I upgraded to Ubuntu 9.10 I decided to use a simple Metacity theme (New Wave).

I noticed that the window's borders become slightly transparent when not selected.  Up until now I was under the impression that Metacity cannot handle window transparency and that the only way to get said transparency was to use an alternative window manager (such as Emerald).

This immediately raised a number of interesting questions:

1. Does this mean that I had it wrong all along and that Metacity could always make window borders transparent, or did they just implement it recently?

2. Can this window transparency be customised?  Say for instance I want to make the borders of active windows transparent as well, or switch it off altogether.  And if so, how?

3. Does it maybe depend on the theme rather than the windows manager?  If so, how would one go about editing the theme to customise the borders?

4. In the screenshot I have the Calculator selected with the Software Centre behind it.  As you can see the transparency in the window border of the Software Centre reflects the screen behind it (Ubuntu Forums).  As such, the transparency used must be true transparency (not merely reflecting the desktop wallpaper).  Does that also mean that we can finally have true transparency for the desktop panels?  If so, once again, how could I achieve that?

---

### Post by VCoolio on 2009-11-10
One thing I know is: have a look at gconf-editor, at /apps/gwd there are some options for metacity_theme_opacity (unfocused windows) and metacity_theme_active_opacity (focused windows) and some other stuff. Set the value to 1 to make them fully opaque. I think this is a gtk-window-decoration setting, not a theme setting. This was also in Jaunty, but about further history and future developments I know nothing.

---

### Post by Uubnewb on 2009-11-10
Thanks for that tip.  Although I've used gconf-editor once or twice before, I never knew about those settings.

---

### Post by mcduck on 2009-11-10
The explanation is actually simple. It's Compiz that does thew transparency for you, not Metacity. If you have visual effects (Compiz) enabled you are using Compiz as your window manager, not Metacity.

By default Compiz uses GWD as it's window decorator plugin, and GWD uses Metacity's themes. Like VCoolio suggested, GWD's transparency settings can be adjusted through gconf-editor.

(So metacity didn't have compositing capabilities all the time, and this feature doesn't depend on the theme you are using. GWD creates the same linear transparency fades regardless of what your theme looks like, so it might fit well on some themes but can also look quite bad with others.)

---

### Post by Uubnewb on 2009-11-13
I should have realised that Compiz uses another window decorator, but it never even occurred to me.

That must mean that the desktop panels are still handled by Metacity since I can't seem to get true opacity on them.  Do you know if it is possible to let another program handle the panels as well?  I know I can get an object docker and just make it do all the work of a panel, but where's the fun in that?

Thanks for the answers, I find all this quite interesting.

---

### Post by mcduck on 2009-11-14
> **Uubnewb said:**
> I should have realised that Compiz uses another window decorator, but it never even occurred to me.

That must mean that the desktop panels are still handled by Metacity since I can't seem to get true opacity on them.  Do you know if it is possible to let another program handle the panels as well?  I know I can get an object docker and just make it do all the work of a panel, but where's the fun in that?

Thanks for the answers, I find all this quite interesting.

The panels are not handled by the window manager at all (at least not in the sense the window borders are). So neither Compiz nor Metacity. They are a program of their own, Gnome-panel.

Sadly Gnome-panel doesn't have support for true opacity, you can use Compiz to make window type "panel" transparent but that will make not only the panel itself but also all it's contents transparent. So not a good option if you want high transparency as any panel contents would become very hard to read.

In my opinion the best way is to use a PNG or SVG image as your panel's background image, that allows for very nice transparency effects (although it's still just fake transparency).

---

