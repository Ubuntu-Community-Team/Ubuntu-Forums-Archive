---
title: "Any way to make icons/windows smaller?"
date: 2009-01-04
forum: Desktop Environments
---

### Post by Jarm1 on 2009-01-04
Hey everyone,

I just installed Xubuntu on an Eee PC 904HA and chose it over regular ubuntu for its lower minimum system requirements.

My issue is, although I can set the screen resolution and the top and bottom bars scale down with higher resolution all the windows and icons seem to retain their huge/fisher price kind of look. The icons are less of an issue but most windows are cut off at the bottom because they look as if they are being run at a much lower resolution.

Is there any way to scale down the windows and icons?

I'm new to Linux and Ubuntu, and I'm not afraid of the terminal but I really can't make it do anything without step by step instructions.

Thanks!

---

### Post by jesuspresley on 2009-01-04
> **Jarm1 said:**
> 
My issue is, although I can set the screen resolution and the top and bottom bars scale down with higher resolution all the windows and icons seem to retain their huge/fisher price kind of look. The icons are less of an issue but most windows are cut off at the bottom because they look as if they are being run at a much lower resolution.

Is there any way to scale down the windows and icons?
Thanks!

[B]Sorry I posted this before realizing that *Xubuntu* does not run in Gnome. 
Well, so you actually have to find an alternative to the following hints: [/B]

You should use a combination of a more compact theme with some additional configuration of your window manager.
That means for example: 

[LIST]
[*]In *System > Preferences > Appearance*
[*]Choose small fonts for all your applications, docs etc. [8 or 9 pt.] 
[*]Click on the theme you have activated. 
[*]Click on *Customize...*
[/LIST]
[INDENT][LIST]
[*]In the *Control* tab choose Mist
[*]In the *Window border* tab choose Mist [or install SystemG - that's my fave]
[/LIST][/INDENT]

[LIST]
[*]Then install Gnome Color Chooser via Add/Remove or via Synaptic.
[The package is *gnome-color-chooser*]
[*]Start it by System > Preferences > Gnome Color Chooser
[*]There you can also adjust the paddings and sizes of icons and window borders.
[/LIST]

With these settings, my *Samsung NC10* netbook desktop looks like this:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=98702&stc=1&d=1231096704[/IMG]

---

### Post by jrounds on 2009-01-04
> **jesuspresley said:**
> [B]Sorry I posted this before realizing that *Xubuntu* does not run in Gnome. 
Well, so you actually have to find an alternative to the folling hints: [/B]

You should use a combination of a more compact theme with some additional configuration of your window manager.
That means for example: 

[LIST]
[*]In *System > Preferences > Appearance*
[*]Choose small fonts for all your applications, docs etc. [8 or 9 pt.] 
[*]Click on the theme you have activated. 
[*]Click on *Customize...*
[/LIST]
[INDENT][LIST]
[*]In the *Control* tab choose Mist
[*]In the *Window border* tab choose Mist [or install SystemG - that's my fave]
[/LIST][/INDENT]

[LIST]
[*]Then install Gnome Color Chooser via Add/Remove or via Synaptic.
[The package is *gnome-color-chooser*]
[*]Start it by System > Preferences > Gnome Color Chooser
[*]There you can also adjust the paddings and sizes of icons and window borders.
[/LIST]

With these settings, my *Samsung NC10* netbook desktop looks like this:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=98702&stc=1&d=1231096704[/IMG]


What are you using for the date/time status? I like the compact form compared to ubuntu default

---

### Post by Jarm1 on 2009-01-04
Thanks for the input, I also tried regular Ubuntu today to try what you said and it gave me the result I was after.

What I found after some not-so-quick searching around was a file you can create in ~/config/xfce4 and then you simply add a file (the specifics escape right this second) with one line to set the DPI. By default it is something like 120 so I set it to 86 and it's perfect now. The windows/icon/text are all perfectly sized for the tiny eee pc screen.

Now all I'd like to do is figure out how to make the damned wifi work on this thing and I'll be golden - and all this to try to make a more safe environment for my completely computer illiterate mother to start using, LOL.

---

