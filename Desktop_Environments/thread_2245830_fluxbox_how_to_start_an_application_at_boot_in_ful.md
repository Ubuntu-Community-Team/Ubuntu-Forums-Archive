---
title: "fluxbox how to start an application at boot in full screen mode"
date: 2014-09-26
forum: Desktop Environments
---

### Post by Leonardvb on 2014-09-26
hello people , 

im looking for a way to boot up a system and directly after login auto starup an aplication in full screen mode. 

but i dont mean kios mode , there are 2 programs that need to be started with hotkey at demand , and kiosk mode dont let me start them 

how can this be done on fluxbox

---

### Post by andrew.46 on 2014-10-11
The standard way is to set a command in *$HOME/.fluxbox/startup*. To run full screen I am not sure, it would be ideal if the application itself had an option for full screen and this could simply be added to the command in *startup*... Otherwise you could specify both size and xy coordinates in *$HOME/.fluxbox/apps*.

---

