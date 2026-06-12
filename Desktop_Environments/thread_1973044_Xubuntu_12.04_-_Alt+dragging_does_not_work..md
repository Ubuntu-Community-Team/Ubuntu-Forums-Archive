---
title: "Xubuntu 12.04 - Alt+dragging does not work."
date: 2012-05-04
forum: Desktop Environments
---

### Post by Athius on 2012-05-04
I've just installed xubuntu 12.04 and so far I really like it. I've only run into one problem so far: alt + dragging does not work. 
Iam running Xubuntu on a netbook with a 1024*600 resolution and sometimes the windows are to large to properly fit on my screen. Before xubuntu 12.04 I used ubuntu 10.04 and there you had the option to drag these windows by holding down the ALT button and clicking and dragging the window. This way I could move a window even if I could not see the top bar. 

In Xubuntu 12.04 however, this is not working. I read a review of Xubuntu 12.04 where it was stated that this should work, so Iam suspecting there is an error somewhere in my settings (or something like that)

Does anybody know how to enable the alt+drag command? 

Many thanks in advance, 

Jasper

---

### Post by mips on 2012-05-04
Must be a setting/config file somewhere. Works here in 12.04 but with openbox, still waiting for xfce 4.10 before I install xfce.

---

### Post by LewisTM on 2012-05-04
Go to Settings Editor/Window Manager Tweaks/Accessibility and pick the desired key.

Cheers!

---

### Post by Athius on 2012-05-04
Jeeej I solved the problem!

Compiz was causing the problem as it replaced the default compositor. I managed to fix the problem by enabling the "move window" plugin in the compiz settings manager.

---

### Post by dentaku65 on 2012-05-04
[http://ubuntuforums.org/showpost.php?p=11872229&postcount=11](http://ubuntuforums.org/showpost.php?p=11872229&postcount=11)

:guitar:

---

