---
title: "Explanation of the elements that make up the Linux GUI"
date: 2008-04-05
forum: Desktop Effects &amp; Customization
---

### Post by melat0nin on 2008-04-05
Hi all

I've been trying to find out a definitive explanation of this, but I can't seem to find a clear resource which doesn't assume lots of prior knowledge.

In Linux, there are many factors which seem to make up the standard Desktop 'theme' (I mean that in the broad sense).  Lots of acronyms and strange names get bandied about, for example:

GTK+, Qt, Compiz, Metacity, Emerald, window decorators, window managers, cairo, compositors (etc etc).

What I can't get my head around is what role each of these things plays in the construction of the graphical desktop (I realise not all of the above are employed simultaneously - but that is part of the problem.  Once I understand all of the equivalents in each class of element, I will know what choices I can make.)

As far as I can tell, the desktop breaks down into these levels:

1. X server
2. Window manager (e.g. GTK 1.x/2.x, Qt, Emerald, CompizFusion - but CF can work alongside Emerald and GTK?? :confused:)
3. Window decorator (Metacity etc?)
4. Theme
5. Control set
6. Icon set

I'm sure I've got something wrong there, but that's why I'm asking :)

I get really confused about what **type** of element (window manager, theme, control set) controls what I see on my screen, and what category of element all the names go into (e.g. is Metacity a window manager or a decorator?).  To top it all off, I don't know what the differences between them within one class is (i.e. what the difference between the window managers is, and why I should choose one over another).  

Obviously the difference between themes is obvious and it's just a question of aesthetics, but with the background 'machinery' which displays the theme, I'm unsure what I should be looking for when making a choice, because it's not really clear what the difference is (on Gnome-look.org, should I be looking in the Compiz section or the GTK section?  Should I be looking in 1.x or 2.x?  What's the difference?!)

If someone could explain, or point me in the direction of a comprehensive resource on this, I would be very grateful! I just want to understand the relationship between the many individual pieces that seem to make up the linux desktop experience.

 I suspect a lot of new Linux users have trouble getting to grips with all the names which are mentioned in relation to their desktop.  Also, with a bit more background knowledge, I will feel much more comfortable customising my desktop more extensively.

Cheers :)

---

### Post by fgxh298 on 2008-04-05
I too am confused by all the lingo.  I get confused about where to look on gnome-look as well (I know enough not to look in the Gnome 1.x section, that stuff is old).  Someone needs to set this straight once and for all (unfortunetly I'm not the one to do that).  

This: [http://ubuntuforums.org/showthread.php?t=203093](http://ubuntuforums.org/showthread.php?t=203093) offers a good start but is a little dated with regards to all the new compisiting stuff.  It doesn't help that a lot of the projects changed names, forked, and merged more times than Madonna has reinvented her image.

As far as I can help:

GTK+ and Qt are GUI (graphical user interface) toolkits.  Toolkits are a common set of widgets for programmers to make GUIs with (buttons, sliders, scrollbars, etc.) Gnomes uses GTK+ and KDE uses Qt (though GTK+ apps can exist on KDE and vice versa).

Compiz is a compsitor, it adds the special effects or something like that.  I think it is also a window manager though, not sure exactly how that all comes together, especially in ubuntu.

Metacity is the default window manager in Gnome.  It also has some compisiting features though.

Emerald is the window decorator for Compiz.  Window decorators control the borders and title of windows (the title bar including minimize, maximize, and close buttons) .

Cairo is just a drawing engine.  I've seen this used in Murrine, but I'm not exactly sure what is special about Murrine and why I should use that either...

---

### Post by melat0nin on 2008-04-06
> **fgxh298 said:**
> 
This: [http://ubuntuforums.org/showthread.php?t=203093](http://ubuntuforums.org/showthread.php?t=203093) offers a good start but is a little dated with regards to all the new compisiting stuff.  It doesn't help that a lot of the projects changed names, forked, and merged more times than Madonna has reinvented her image.


Thanks for this, I will have a read and see what I can find.  It's pretty bewildering, isn't it?! :lolflag:


Another thing, I have the Appearance applet, something called GL Desktop, and the Emerald Theme Manager.  Running GL Desktop seemed to interfere with my CompizFusion settings, but that wasn't catastrophic (it was annoying though -- what is this program for?  It seems to have some of the CF settings in it).  Also, what is the difference between the theme manager in the Appearance applet, and the Emerald Theme Manager?  Having >1 place to make these choices is very confusing!

---

