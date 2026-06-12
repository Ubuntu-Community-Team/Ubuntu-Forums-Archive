---
title: "ctrl+alt+right key/left key not working in Jaunty[9.04]"
date: 2009-05-13
forum: General Help
---

### Post by harry2006 on 2009-05-13
Hi All,
I installed Ubuntu9.04 last weekend and everthing was working fine until when I tried to install compizconfig-settings-manager and when the  installation finished [installed using apt-get] my workspace switcher stopped working[the ctrl + alt + left arrow/right arrow key combination stopped working] and surprisingly clicking with mouse arrow even doesnot seem to do anything but super/window key with E gives me a view of all the four desktops I 've and I can select from that any desktop and is working fine. But I want to enable the ctrl + alt + arrow comibation...I even removed the compizconfig-settings-manager from my system but to no help. Please help me fix this

---

### Post by Tamlynmac on 2009-05-13
> my workspace switcher stopped working[the ctrl + alt + left arrow/right arrow key combination stopped working 

I believe it's:
Shift+Ctrl+Alt+Left (or Right or Up or Down)
That moves window once workspace to the left,right. etc.

See keyboard shortcut under preferences. You can alter the key combinations in the keyboard shortcut popup.

---

### Post by harry2006 on 2009-05-23
No the shorcut is there but clicking it doesnot give me any response. Even the workspaces 2nd onwards are not even clickable i.e clicking thru mouse gives no response/ no change at all, it will not take you to that workspace. The only option left for me to use is Super + E that gives a view of all the workspaces and moving arrows left/right allows me to select one of them. 
Earlier alt+ctlr+arrow[left/right] used to show 4 boxes for 4 workspaces but thats not working. 
 Whats is the issue??? I'm forced to use the other option which I don't like to use. 

Thank you.

---

### Post by The-ITu on 2009-05-23
open up the compiz config manager (system>preferences>compiz-settings) and under Desktop look for "desktop wall" and click on it.
than at the top press on where it says bindings and then click on the first drop menu(move within wall).
than choose you shortcut key to switch desktops.
hope it helps :)
The-ITu

---

### Post by harry2006 on 2009-05-23
> **The-ITu said:**
> open up the compiz config manager (system>preferences>compiz-settings) and under Desktop look for "desktop wall" and click on it.
than at the top press on where it says bindings and then click on the first drop menu(move within wall).
than choose you shortcut key to switch desktops.
hope it helps :)
The-ITu
Thanks a lot. I've stuck for around a week. When I did as you said what I found is that everything was ok all those key selections were already there but desktop wall itself was not enabled, so i just enabled it and it worked like a charm. Thank you very much @The- ITu

---

### Post by tau88 on 2009-08-29
thank you, i was looking for a solution for this annoyance

---

