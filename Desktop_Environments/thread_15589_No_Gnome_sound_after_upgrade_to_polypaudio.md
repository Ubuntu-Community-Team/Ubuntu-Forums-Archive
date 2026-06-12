---
title: "No Gnome sound after upgrade to polypaudio"
date: 2005-02-15
forum: Desktop Environments
---

### Post by nanaban on 2005-02-15
Some facts:
[list=1]
[*]I did a dist-upgrade. It removed esound and installed polypaudio along with other packages.
[*]RealPlayer works now after the upgrade.
[*] Mp3 on xmms works. 
[*]Sound from RealPlayer works (watched trailers online). It won't load before I upgraded.
[*]RealPlayer won't start unless xmms is closed.
[*]Sound from Gaim works.
[*]Sound from Flash works.
[*]Sounds at login screen works.
[*]No sound at gnome startup splash screen.
[*]No gnome sound when clicking on menu items.
[*]Multimedia System Selector points to esound, still.
[*]libesd0 is still installed.
[/list] 

Questions:
[list=1]
[*]To get my gnome sound back, what else need to be installed (didn't install any poplypaudio libs)?
[*]Do I need to change anything in the multimedia system selector?
[*]Do I need to replace libesd0 with anything?
[/list] 

TIA!

---

### Post by nanaban on 2005-02-16
[QUOTE=nanaban]Some facts:
[list=1]
[*]I did a dist-upgrade. It removed esound and installed polypaudio along with other packages.
[*]RealPlayer works now after the upgrade.
[*] Mp3 on xmms works. 
[*]Sound from RealPlayer works (watched trailers online). It won't load before I upgraded.
[*]RealPlayer won't start unless xmms is closed.
[*]Sound from Gaim works.
[*]Sound from Flash works.
[*]Sounds at login screen works.
[*]No sound at gnome startup splash screen.
[*]No gnome sound when clicking on menu items.
[*]Multimedia System Selector points to esound, still.
[*]libesd0 is still installed.
[/list] 

Questions:
[list=1]
[*]To get my gnome sound back, what else need to be installed (didn't install any poplypaudio libs)?
[*]Do I need to change anything in the multimedia system selector?
[*]Do I need to replace libesd0 with anything?
[/list] 

TIA![/QUOTE]
 *bump*

---

### Post by WorLord on 2005-02-16
*bump*, totally.

---

### Post by t.rei on 2005-02-17
now this is still the case for me, too :(

anyone a clue? I followed some suggestions here in the board - nothing helped.

---

### Post by rudiz on 2005-02-17
upgrade libesd0

---

