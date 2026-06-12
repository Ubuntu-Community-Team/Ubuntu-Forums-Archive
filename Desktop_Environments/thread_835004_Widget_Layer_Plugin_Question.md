---
title: "Widget Layer Plugin Question"
date: 2008-06-20
forum: Desktop Environments
---

### Post by TheZorch on 2008-06-20
I was messing around with System~>Preferences~>Advanced Desktop Effects Preferences and found that Compiz Fusion has a Widget Layer plugin.  I tried it out and it works just like the Widget Layer for Mac OS X, but there weren't any widgets.

I searched on Google and couldn't find anything pertaining to Widgets I could add to this Widget Layer.  So, does anyone know where I can find some.

The Widget for Mac OS X are really neat, a friend of mine has a Mac with Leopard installed and he can make Widgets from web content.  Anyway, please help.

---

### Post by denham2010 on 2008-06-20
Heya TheZorch,

There are several options. I'll list the 2 most commonly used:

1. Download and install screenlets. Screenlets is in the repositories.

```
sudo apt-get install screenlets
```

Screenlets are python applicatons that can sit on your desktop, or, by right clicking on the widget, you can set it's window properties to be a widget and so disappearing, only to appear on the compiz widget layer.

Screenlets comes with a default set of widgets, but doing a google search may find more as people make screenlets (a good place to look may be [www.gnome-look.org](www.gnome-look.org)).

An alternative to screenlets is gdesklets, again in the repositories. Gdesklets will not use the widget layer as default (last time I had it installed - but this may have changed with development) but once set up, you can follow option 2 below to place gdesklets on the widget layer.



2. You can use absolutely any program you wish as a widget. Obviously, you may wish to set the program to launch in your start-up options. Alternatively, you can just launch it as normal, but nothing will appear to have happened, until you go to your widget layer.

To set a program to act as a widget, open the advanced desktop effects preferences (CCSM) and go into the widget layer option. Click on the Behaviour tab.

Now open the program you want to place on the widget layer. Back in CCSM click on the + at the end of the window widgets option. In the dialogue that opens up, set the type to Window Title (for just that instance of the program) or experiment with the other options to see exactly what they do (for example Window Type will make all windows of the same type as the program you select to become widgets, not just that application!)

Now, at the end of the Value line click the grab button, and then click on the title bar of the application you wish to set.

That's it, click ADD and you are done.



Cheers, and happy widgets!

---

