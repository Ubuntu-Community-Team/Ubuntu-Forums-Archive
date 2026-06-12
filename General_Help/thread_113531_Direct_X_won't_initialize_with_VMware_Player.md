---
title: "Direct X won't initialize with VMware Player"
date: 2006-01-06
forum: General Help
---

### Post by GrayMagiker on 2006-01-06
I am trying to run Warcraft 3, not WoW, in a VMware workstation on Ubuntu Breezy.  The install goes fine, but when I try to run the game to play it says
> 
Warcaft III was unable to initialize DirectX.  Please ensure you have DirectX 8.1 or newer installed and that your display drivers are current.  DirectX may be found on your Warcraft III CD under options


It then gives an error about finding my CD drive, I click "Retry" and it shuts down Wc.  

When I run the CD and try to install DirectX 8.1 it says 
> 
Setup has detected that your computer already has DirectX 8.1 or newer


So what do I do?

I do not have a separate graphics card, it is all on the Motherboard.  Could this be the problem?  If so, how would i determine what drivers need to be installed.

My main question however is:

Is there something I need to change in the settings for VMware player so that it can initialize DirectX?

---

### Post by mcman42 on 2006-07-29
same problem here ](*,)

---

### Post by LeChuckThePirate on 2006-08-03
I just saw a page that could help you.. not sure though cause I haven't tried this myself (will do tonight)

[http://www.vmware.com/support/ws5/doc/ws_vidsound_d3d_enabling_vm.html]("http://www.vmware.com/support/ws5/doc/ws_vidsound_d3d_enabling_vm.html")

Good luck!

---

### Post by zaipai on 2006-09-03
Yup that worked. I followed the link and was able to enable Directx direct3d. Not sure how it works, will have to install a game and find out. Thanks for the info! :-D

---

