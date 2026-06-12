---
title: "repo theme problem: backgrounds not painted"
date: 2018-06-20
forum: Desktop Environments
---

### Post by undecidable on 2018-06-20
After being on Kubuntu since 6.06  (ie 12 years) 
am making the transition to Xubuntu 18.04

I am having a problem I can't solve:

If I use a dark theme 
(set in Settings/Appearance/Style)
such as Adwaita-Dark or Breeze-Dark
(both in the repos)
then sometimes
after reboot I get white text on a white background 
- so obviously I can't read it. 
This happens with, eg:
	the main menu, thunar, and kde apps: such as gwenview, clementine

However some apps seem ok, and give me the expected white text on a black background,
eg:  mousepad, geany, nemo, pluma, firefox.

White themes (eg Adwaita, Breeze) are ok
and as expected show black text on white background.

If I uninstall  breeze-gtk-theme
and then select Adwaita-Dark
it works ok.

But Adwaita-Dark doesn't work well with kde apps
('grayed-out' menu items cant be read - black on black),
whereas the breeze theme does enable them to be read.

Any idea what is causing this
or where there is a config file I can edit / fix?

---

### Post by again? on 2018-06-20
Don't know the actual cause but may I suggest a dark theme I use without problems in Xubuntu 18.04.
[https://launchpad.net/~tista/+archive/ubuntu/adapta](https://launchpad.net/~tista/+archive/ubuntu/adapta)

---

### Post by undecidable on 2018-06-21
thanks guber2, adapta-nokto works well
though I find the sooty black backgrounds a little less than beautiful.
Prefer the clean black of Breeze & Adwaita. 

But It gives me something to use until I solve the problem above
(which might be quite a while!)

---

### Post by undecidable on 2018-07-25
**Solution:**

(The underlying problems are:
1.  I'm using a lot of kde apps in Xubuntu
2.  I hate unreadable menus and ugly windows).


After trying all 12,986 combinations, 7 times each:
the following two work well for both native & kde apps in Xubuntu 18.04:

_Dark Desktop:_
Theme - 	Adapta-Nokto-Eta
Window Style - Adapta-Nokto
Icons - papirus-adapta-nokto

_Light Desktop_
Theme - 	Adwaita
Window Style - Adapta-Nokto
Icons - papirus-light

Breeze also works as a window manager for the Light Desktop, but is not as elegant as Adapta-Nokto.
Reason for papirus icon set is it is the only one I have found with icons for gnome/xfce and kde apps.

---

### Post by kazakore on 2018-07-25
See this thread of mine for a few pointers getting a decent dark theme. I could share the edited one I'm using which is the closest to fully decent I've managed to get so far if you like....

[https://ubuntuforums.org/showthread.php?t=2391601](https://ubuntuforums.org/showthread.php?t=2391601)

Note that there are themes with both dark and light options in one theme and you need "gtk-application-prefer-dark-theme=true" most suitably in your ~/.config/gtk3.0/gtkrc file to get them to use the dark settings.

There's also notes in there on getting qt apps to follow the gtk theme.

---

### Post by undecidable on 2018-07-25
great, thanks kazakore, a lot of useful information in the post.
But also quite complex:  will get to it on the weekend.
Theming and window management are the only things I miss from kde in xfce.

---

