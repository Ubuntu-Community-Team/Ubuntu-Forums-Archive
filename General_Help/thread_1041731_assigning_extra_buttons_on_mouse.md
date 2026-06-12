---
title: "assigning extra buttons on mouse"
date: 2009-01-16
forum: General Help
---

### Post by raghu1111 on 2009-01-16
installed the latest Interpid. I have a five button optical intellimouse. The two side buttons are assigned their defaults (back and forward for Firefox). How do I change that? I am used to assigning them to middle button. Any indirect way to make them behave like middle click?

link for mouse : [http://www.microsoft.com/hardware/mouseandkeyboard/productdetails.aspx?pid=004](http://www.microsoft.com/hardware/mouseandkeyboard/productdetails.aspx?pid=004)

Thanks,
Raghu.

EDIT : An xbindkeys based fix is described below (that mostly works).

---

### Post by raghu1111 on 2009-01-22
will xinput do this job? I trying to use 'xinput set-button-map "device name" ...". But can not figure out what the arguments for map should be. 

I tried things like 'xinput set-button-map "device name" map button 1 2'. Some thing has changed but it seems random. I could not find info on what the arguments for mode should be. I basically need to to map two side buttons to middle click.

Thanks.

---

### Post by raghu1111 on 2009-01-22
I sort of got it to **mostly** work with xbindkeys (help from [http://ubuntuforums.org/showthread.php?t=316441](http://ubuntuforums.org/showthread.php?t=316441) ) :

I have following lines in ~/.xbindkeysrc :```

#bind '8' to middle click :
"/usr/bin/xte 'mouseclick 2' &"
b:8 + Release
```

'8' is the left side extra button I use thumb to press. I say it *mostly* works, since xbindkeys does not always run the xte command (noticed with firefox): A few issues for xbindkeys experts :

[LIST=1]
[*]With firefox, when press '8', it first shows the 'scroll' (as expected for a middle click), but if I press the button multiple times FireFox goes back one page (Alt Left Arrow). For this extra click, output from 'xbindkeys -n -v' does not show that it ran 'xte' application.. as if there there was no xbindkeys config.

[*] In .xbindkeysrc, if I remove "+ Release" it does not work. I wonder why. Is there a better way to configure middle click to button '8' that makes it work just like the middle click?
[/LIST]

---

