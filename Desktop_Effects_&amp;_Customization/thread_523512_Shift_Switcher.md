---
title: "Shift Switcher"
date: 2007-08-12
forum: Desktop Effects &amp; Customization
---

### Post by Ianman on 2007-08-12
Hi all,

I have installed the Shift Switcher plugin for compiz fusion and have seen it working on another machine. It looks really cool so I wanted to use it as my main application siwtcher. I decided to map Alt Tab to it but this doesn't seem to work. I have removed Alt Tab from the other application switchers and disabled them but this doesn't seem to help. In fact, the default key assignment don't seem to work at all. The "super" key doesn't work for this plugin either. I have Expo for instance mapped to Super E which does work but not for the Shift Switcher plugin.

Anyone got any ideas?
Thanks!

---

### Post by Ianman on 2007-08-12
Nevermind! Seems I did leave out a key bind in one of the other switchers....so many key bindings!

---

### Post by icecoldmilk on 2007-08-15
> **Ianman said:**
> Nevermind! Seems I did leave out a key bind in one of the other switchers....so many key bindings!

i got the same problem>_<

any idea how to fix it? i had disable all the keys in ring switcher, and untick the ring switcher, but when i hit Super+Tab key, the ring switcher still working !!!

any ideas :popcorn::popcorn:

---

### Post by Ianman on 2007-09-01
sorry I didn't reply earlier icecoldmilk... :-( Been kinda busy.

Did you manage to solve your issue or is it still plaguing you? I have noticed a similar situation on another system. Even with the ring switcher plugin disabled, Super+Tab still shows the ring switcher 0_o

---

### Post by RSL on 2007-09-19
How the heck do you get the key binding to accept anything with a tab in it? I swear, I can't get to to set the switcher to alt+tab, super+tab, nothing with a tab. What's the secret? Is there a text config file I can edit for this? This is so much more annoying that I'd have guessed it would be.

---

### Post by seismicmike on 2008-01-06
> **RSL said:**
> How the heck do you get the key binding to accept anything with a tab in it? I swear, I can't get to to set the switcher to alt+tab, super+tab, nothing with a tab. What's the secret? Is there a text config file I can edit for this? This is so much more annoying that I'd have guessed it would be.

You actually have to type it in. Double click on "Initialize" for instance and in the field labeled 'Key', if you want it to say Super+Tab you have to actually type:

```
<Super>Tab
```

Same thing with Shift and alt... you have to type it in <>'s... This was confusing to me.... I don't know if there's a way to do it by keying it in, but this did work for me.

The trouble is I can't quite get Shift Switcher to work right. It works, but only for the current desktop (workspace, viewport...). I'm using the standard cube (4 desktops, 1 row), but I can't get Shift Switcher to shift switch between all windows on all four desktops.... I can get Scale to do it. I can get Ring Switcher to do it. I can get Alt Tab to do it..... but can't get Shift Switcher to do it.


Any ideas?

---

### Post by seismicmike on 2008-01-06
OK.I fixed my own problem. Sorry to bother you guys.

Initiate = Disabled
Initiate (All Workspaces) = <Shift><Super>s = Shift+Super+s
Next Window = <Alt><Super>Tab = Alt+Super+Tab
Previous Window = <Shift><Alt><Super>Tab = Shift+Alt+Super+Tab
Next Window (All Workspaces) = <Alt>Tab = Alt+Tab
Previous Window = <Shift><Alt>Tab = Shift+Alt+Tab

How it works:

Use Alt-Tab like you've been trained by Windows to us Alt-Tab. Except in this case it looks like the Vista switcher (that is if you set it to flip... don't know if Vista does cover) and it includes all windows from all desktops on your cube.

You can still use Ring Switcher too. Just set the following Key Bindings in Shift Switcher:

Next Window (All Workspaces): <Super>Tab = Super+Tab
Previous Window (All Workspaces): <Shift><Super>Tab = Shift+Super+Tab

This one works by using Alt-Tab except using the 'Windows' key (known as super in gnome) in place of the Alt key.

I also have Scale working - the Mac-Like app switcher that puts all open and non-minimized windows on the desktop at the same time so you can visually pick from them by clicking on them. And I have Expo working. I bound Expo to the bottom left of the screen and Scale I bound "Initiate Window Picker for All WIndows" to bottom right.

Since I am using AWN (Avant Window Navigator) and have deleted the bottom panel, neither of these conflict with my regular gnome use.

---

### Post by MariusSilverwolf on 2008-01-06
> **seismicmike said:**
>  
The trouble is I can't quite get Shift Switcher to work right. It works, but only for the current desktop (workspace, viewport...). I'm using the standard cube (4 desktops, 1 row), but I can't get Shift Switcher to shift switch between all windows on all four desktops.... I can get Scale to do it. I can get Ring Switcher to do it. I can get Alt Tab to do it..... but can't get Shift Switcher to do it.


Any ideas?

In the Key Bindings for Shift Switcher, there's an option for Initiate (All Workspaces) that is, by default, disabled.  Set the Key Bindings to what you want (replace Initiate if you don't want to ever limit yourself to just the one workspace) and you should be good to go.

Or, from the look of the default bindings, Alt+Super+Tab will scroll between all workgroups.  You can edit the command Next Window (All Workspaces) to get the result you want, I believe.

Or I could be too late and you've had found that already.  Ooops . . .

---

### Post by seismicmike on 2008-01-08
> **MariusSilverwolf said:**
> Or I could be too late and you've had found that already.  Ooops . . .

That's ok. Thanks for your willingness to help.

---

### Post by MariusSilverwolf on 2008-01-09
> **seismicmike said:**
> That's ok. Thanks for your willingness to help.

That's what we're supposed to be all about here, right?  Besides, by trying to help, I learn too.  We all win.

---

