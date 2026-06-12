---
title: "Xgl/Beryl Keyboard Layout"
date: 2006-11-11
forum: Desktop Environments
---

### Post by DimitrisC on 2006-11-11
I installed Xgl/Beryl a few days ago on dapper and it works great.  The only problem is that i have 2 keyboard layouts installed on my computer (one default english, and one for writing greek). Everytime i reboot the computer the keyboard settings are lost. The  keyboard shortcut i have for changing between layouts (ctrl_shift) no longer works.  I also have the keyboard layout applet on my taskbar and when i choose greek the scroll locks lights up (i have it to indicate change of layouts) but i get only english input not greek except fot the character "e" which shows up as "*".  When i go to keyboard settings to the ubuntu menu even without doing any changes (the default settings like ctrl_shift changes layout and scroll lock are there) just by pressing OK everything is back to normal.  My shortcuts work as well as the applet.  I am almost sure that the problem is Xgl/Beryl since the layout worked fine before i installed xgl/beryl.

Any ideas to keep the layout settings in place after reboot?

Thanks!!!

---

### Post by DimitrisC on 2006-11-13
Anyone?

---

### Post by lowracer on 2006-11-16
I use the US-Dvorak layout, and when Beryl/XGL is loaded, the layout reverts in practice back to US-Qwerty.  I say "in practice" because when I bring up the keyboard preferences, it says the keyboard layout is US-Dvorak.  So I'm looking for a resolution to this issue as well.

---

### Post by DimitrisC on 2006-11-17
Well after a lot of search i found something that kind of fixed the problem for me (i say kind of because the keys i have setup for changing layout still dont work and i have to use the keyboard indicator applet).

In gnome settings in sessions xmodmap.us was loaded. So i deleted it and i put in startup under sessions xmodmap.gr (which is for greek - thats what i use as second language) and now i have both us and greek layouts working ok.

Check here: [http://www.ubuntuforums.org/showthread.php?t=270462&highlight=xmodmap.us](http://www.ubuntuforums.org/showthread.php?t=270462&highlight=xmodmap.us)

and here: [http://www.ubuntuforums.org/showthread.php?t=249843&highlight=xmodmap.us](http://www.ubuntuforums.org/showthread.php?t=249843&highlight=xmodmap.us)

Hope it helps!

---

