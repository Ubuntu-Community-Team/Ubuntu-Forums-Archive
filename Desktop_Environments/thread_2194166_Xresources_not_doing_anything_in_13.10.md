---
title: "Xresources not doing anything in 13.10"
date: 2013-12-16
forum: Desktop Environments
---

### Post by adamb.infinity on 2013-12-16
[COLOR=#333333][FONT=UbuntuRegular]I'm trying to understand the capabilities of .Xresources yet I cannot get it do do even the most simple of configurations. For instance, I want to be able to change the background color of my terminal.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]In my .Xresources file I have:
[/FONT][/COLOR]
> [COLOR=#333333][FONT=UbuntuRegular]*background: #FFFFFF[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]
I save that and then run
[/FONT][/COLOR]
> [COLOR=#333333][FONT=UbuntuRegular]xrdb -merge ~/.Xresources
[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]I have tried exiting the terminal, logging off then back on, and restarting. No luck.
[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]**I know I could change the background by using Edit-->Profile Preferences-->Colors but I want to understand Xresources**[/FONT][/COLOR]

---

### Post by Toz on 2013-12-16
Which terminal program are you using? The process you list works fine for xterm (and other [Xt library]("http://en.wikipedia.org/wiki/X_Toolkit_Intrinsics")-derived applications). If you're using gnome-terminal or xfce4-terminal, then you're out of luck - neither terminal doesn't use Xresources to set its properties. You have to use the configuration system that the program uses.

---

### Post by adamb.infinity on 2013-12-16
Thank you. I *am* using gnome-terminal. I discovered I will need to use gconftool-2.

---

