---
title: "Window Title bar looks horrible in Gnome Shell"
date: 2011-11-18
forum: Desktop Environments
---

### Post by blaher on 2011-11-18
I have Ubuntu 11.10 installed with Gnome Shell. I installed the Window/GTK Theme Zukitwo ([http://lassekongo83.deviantart.com/art/Zukitwo-203936861](http://lassekongo83.deviantart.com/art/Zukitwo-203936861)) and Shell Theme Faience ([http://tiheum.deviantart.com/art/Gnome-Shell-Faience-255097456](http://tiheum.deviantart.com/art/Gnome-Shell-Faience-255097456)). I installed this same setup on my laptop at home, and everything works fine. When I installed the same setup on my work computer, I get the following in the attached screen shot.

The window title bar seems to be over written with an old setting back from Compiz/Gnome 2 (when I had 11.04 installed). I can't find any settings, and I'm obviously new to Gnome Shell. Can someone please help me make my windows more beautiful?

---

### Post by Frogs Hair on 2011-11-18
Try to logout and in and see if that changes anything . Zukitwo has been updated many times , so be sure you are running the same versions on both computers .

The area where the tabs appear in the browser will be slightly darker , you can see this when toggling tabs on top.

Hardware differences between the computer may also have something to do with how the theme renders .

---

### Post by blaher on 2011-11-18
I downloaded the theme about 18 hours apart, so hopefully they're not a different version.

The text looks like it has a shadow behind it, which was in my last version of Ubuntu. No matter what theme I pick, it doesn't go away. So I think something else is over riding the themes somewhere.

As for the graphics cards, they are both Nvidia, about a two year version  apart.

---

### Post by cbowman57 on 2011-11-18
You might also want to see if both machines are running the same font & anti-aliasing.

---

### Post by blaher on 2011-11-18
They are both using Ubuntu Bold and rgba anti.

---

### Post by cbowman57 on 2011-11-18
Hmm.., next thing I'd do is transplant the entire theme from one machine to verify they are identical, if things stay the same then we'll know to look elsewhere.

Have you hacked the shell of either machine or run a slightly different set of extensions?

I noticed recently that even disabled extensions can somehow interact with behaviour.

---

### Post by blaher on 2011-11-18
They are both identical, file wise. I even checked them with a diff comparison tool.

I have not added any modifications or extensions to the shell. If I remember correctly, I did make some modifications to Gnome 2.0 a while a go. I don't remember what however.

---

### Post by cbowman57 on 2011-11-18
gtkrc file maybe?

Not really certain if any changes you made to Gnome 2.0 would affect Gnome 3 but the window frame is metacity so that might be affected by gtkrc, but I'm no expert so can't say for certain.

Just trying to brainstorm with you a little bit. :)

Of course this doesn't rule out slight differences in hardware or firmware.

---

### Post by blaher on 2011-11-18
There was no ~/.gtkrc or ~/.gtkrc-2.0 file found.

---

### Post by cbowman57 on 2011-11-18
Will remain a mystery I guess.

---

### Post by Copper Bezel on 2011-11-18
I've only ever seen this problem temporarily. Changing the GTK theme or the window theme can cause the title bars to look weird, but it's always been fixed for me by restarting the Shell (or X.)

Metacity stores some of its settings in gconf still, rather than dconf. That means that some settings really could persist from Gnome 2, and that might pose a problem. Have you tried

```
gconftool-2 --recursive-unset /apps/metacity
```

?

Metacity's settings shouldn't have a bearing on the theme, but it's worth a shot. Of course, you'll need to restart X to see the changes applied.

---

### Post by LarsKongo on 2011-11-22
It looks like there are some color changes to the gtk3 theme. The metacity theme in Zukitwo fetches the color from bg_normal in the gtk.css file.

If you haven't changed any colors - then try reinstalling the theme, or look in ~/gtk-3.0/settings.ini to see if anything is messing with the colors there.

---

### Post by blaher on 2011-11-22
I have restarted several times. And reinstalled the theme in to the shared folder. I also could not find any folder that has gtk in the name.

However, I have reason to believe that has something to do with metacity causing this problem, and not a GTK setting. Could I still be reverting back to using metacity, instead of a gtk window manager?

I have also noticed, when I do fallback mode (classic), the title bar doesn't have that dark gradient on it.

---

### Post by Copper Bezel on 2011-11-22
Under Gnome Shell, you *are* using Metacity, which is the Gnome window manager. You'd be using it under Fallback, too, unless you've switched it to Compiz, in which case it would be gtk-window-decorator, as you say; gtk-window-decorator is a Compiz package that draws Metacity-like titlebars. In that case, yeah, it would be a Metacity problem. Did you try removing Metacity's settings?

---

### Post by blaher on 2011-11-23
I ran "gconftool-2 --recursive-unset /apps/metacity" if that's what your asking? Is there any other specific settings I can try changing? Could I safely remove "gtk-window-decorator", and fix the problem?

---

### Post by Copper Bezel on 2011-11-23
Okay, that's all I was asking, so that's one thing less to check. 

You could safely remove Compiz and its decorators without causing any problems, but I don't know that it would have any effect on the one you're having. 

Instead, try logging into a (Gnome Shell) guest session and applying the theme there, and see if you get the same effect. That'll decide whether it's a config problem or a software problem.

---

### Post by blaher on 2011-11-23
Ignoring the spam that quoted me. I logged in to a guest session, and applied the theme. Everything seems to look fine in the guest session.

---

### Post by Copper Bezel on 2011-11-23
Yeah, those bots are annoying, aren't they?

I don't honestly know. The software and theme are fine, then, and we've cleared your user settings for Metacity, which doesn't leave much.

Hmm. Check that you don't have the theme installed in ~/.themes, too. If there's something wrong in that folder, it'll override the system-shared copy of the theme under your account (but not under others that wouldn't have access to it.)

---

### Post by blaher on 2011-11-29
There's nothing in ~/.themes. I have noticed though, when restarting my computer, the window theme will flash to normal (white) really quick before it logs out.

---

