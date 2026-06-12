---
title: "Problem installing bitmap fonts in Edgy Kubuntu"
date: 2006-11-16
forum: Desktop Environments
---

### Post by effo on 2006-11-16
I am having troubles getting bitmap fonts working in KDE/Xft on my Edgy Kubuntu. The steps I have taken are:

[LIST=1]
[*][FONT="Courier New"]$ sudo dpkg-reconfigure fontconfig-config[/FONT]
and enabled bitmap fonts
[*]Copy pcf-files to to my [FONT="Courier New"].fonts[/FONT] directory
[*][FONT="Courier New"]$ mkfontdir[/FONT] 
[*][FONT="Courier New"]$ sudo fc-cache -vf[/FONT]
[*]reboot (just for sure)
[/LIST]
After rebooting, the fonts are available to the core font system; I see them when I use 
[FONT="Courier New"]$ xfontsel[/FONT]
and 
[FONT="Courier New"]$ xlsfonts[/FONT]
However, the fonts are NOT available in Xft; if I do a 
[FONT="Courier New"]$ fc-list[/FONT]
none of the fonts show up. Neither do they show up in the font installation utility in KDE. 

I think I used this process in Dapper, and then everyghing worked well. But now in Edgy it doesn't seem to work.

Any ideas?

/Fredrik

---

