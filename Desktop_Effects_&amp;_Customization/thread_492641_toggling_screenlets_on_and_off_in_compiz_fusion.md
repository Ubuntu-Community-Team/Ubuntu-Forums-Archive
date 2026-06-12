---
title: "toggling screenlets on and off in compiz fusion"
date: 2007-07-04
forum: Desktop Effects &amp; Customization
---

### Post by djrobthaman on 2007-07-04
Hi,

I'm using compiz fusion from Trevino's repo and just installed screenlets.  It looks like a great program but right now I can't toggle it on or off with a mouse gesture or shortcut or something.  I have done a bit of searching and have found that beryl users can use a widget-layer plugin, set the screenlets to behave like widgets and show and hide them easily that way.

Is there any similar plugin for compiz fusion to do this?  Or is there some other method that would allow me to do that?

Thanks

---

### Post by psyopper on 2007-07-19
You're looking for the Window Rules plug-in I believe. There's an entry for Widgets in there.

It's in Trevino's repos but I can't remember the name of the package off the top of my head... I think it's part of compiz-plugins-extras maybe?

---

### Post by djrobthaman on 2007-07-20
Yep,

It's in plugins-extra.  But, do you know what I should type in the text-box for widget?  I have no clue.  

Thanks

---

### Post by psyopper on 2007-07-20
I haven't got a clue. Really makes me want to write user documentation for the app - there's quite a few things that I look at and say "I see it but I have no idea what it is or how to use it."

Take a look at some of the other modal boxes - I think it's (xxx | xxx) where xxx is the name of your apps and the | delinieates multiple apps.

---

### Post by Mr Greencastle on 2007-07-21
Download the: compiz-fusion-plugins-unsupported
and: compiz-fusion-plugins-unofficial

After its done, you should have a widget layer plugin in the compizconfig, should be near the bottom. If you can't find it just search in the box on the left.

Hope that helps!

Mr Green

---

### Post by crazyhunk on 2007-07-21
or u can use vorians repos.... and just do an update to ur existing compiz... and u should actually have the widget plugin installed....

---

### Post by psyopper on 2007-07-21
> **Mr Greencastle said:**
> Download the: compiz-fusion-plugins-unsupported
and: compiz-fusion-plugins-unofficial

After its done, you should have a widget layer plugin in the compizconfig, should be near the bottom. If you can't find it just search in the box on the left.

Hope that helps!

Mr Green

OK, so I downloaded the Widget Layer Plugin from Trevino's repos, and it's in CCSM, but what string value do I enter to identify a window to be treated as a widget?

In my instance I'm trying to get Conky to be treated as a widget so it doesn't appear in my ring switcher. How do I do this? 

Again, user docs would be extremely helpful here!

---

### Post by Mr Greencastle on 2007-07-21
Wouldn't you just put 'conky' in there? I don't have it so I'm not sure what the package is called.

---

### Post by psyopper on 2007-07-21
One would think so but if you look around there seem to be several different methods of listing apps or app types:

In General, Opacity Settings, Opacity Windows:
((type=Menu | PopupMenu | DropdownMenu | Tooltip | Notification | Combo | Dnd | name=sun-awt-X11-XWindowPeer) | (type=Normal & override_redirect=1)) & !(name=sun-awt-X11-XFramePeer | name=sun-awt-X11-XDialogPeer)

In Fading Windows, General, Fade Windows:
any

In Wobbly Windows, General
 - Move Windows:
     Toolbar | Menu | Utility | Dialog | Normal | Unknown
 - Map Windows
     ((type=Unknown | Menu | PopupMenu | DropdownMenu | Tooltip | Notification | Combo | Dnd | name=sun-awt-X11-XWindowPeer) | (type=Normal & override_redirect=1)) & !(name=sun-awt-X11-XFramePeer | name=sun-awt-X11-XDialogPeer)

In Ring Switcher, Misc Options, Ring Windows:
(type=Normal | Dialog | ModalDialog | Utility | Unknown | name=sun-awt-X11-XFramePeer | name=sun-awt-X11-XDialogPeer) & !(type=Normal & override_redirect=1)

There is something approaching consistency - essentially pipe delimited names for window types. I haven't found one that lets you name the application itself.

---

### Post by djrobthaman on 2007-07-21
> **Mr Greencastle said:**
> Download the: compiz-fusion-plugins-unsupported
and: compiz-fusion-plugins-unofficial

After its done, you should have a widget layer plugin in the compizconfig, should be near the bottom. If you can't find it just search in the box on the left.

Hope that helps!

Mr Green

I wish it were that simple.  I have already installed these packages and have the widget plugin enabled but it doesn't work.  As soon as I tell a window to be a widget it disappears never to be seen again.  I have tried inputting screenlets, screenletd, screenletsd add, screenlets-tray as the apps it should display, but still no luck.


Any suggestions?

BTW, also saw that window rule plugin but still don't know what I should type in there either

---

### Post by psyopper on 2007-07-23
> **djrobthaman said:**
> I wish it were that simple.  I have already installed these packages and have the widget plugin enabled but it doesn't work.  As soon as I tell a window to be a widget it disappears never to be seen again.  I have tried inputting screenlets, screenletd, screenletsd add, screenlets-tray as the apps it should display, but still no luck.


Any suggestions?

BTW, also saw that window rule plugin but still don't know what I should type in there either

I think I got it figured out for both of us. [Take a look at this post at the opencompositing.org forum]("http://http://forums.opencompositing.org/viewtopic.php?f=51&t=529") for instruction on how to identify your window attributes. The article is geared towards setting your window opacity attributes, but is specifically looking at including or excluding particular items from the list. 

I was able to get conky out of my ring switcher by adding this to my "ring windows" line:

& !(class=conky | name=$conky)

Maybe a look over this page could net you some decent results! Or at least get you pointed in the right direction!!

---

