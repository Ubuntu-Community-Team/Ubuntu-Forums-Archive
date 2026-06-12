---
title: "key bindings issues.."
date: 2006-06-18
forum: Desktop Environments
---

### Post by chomafin on 2006-06-18
S0 basicaly, I was recently trying t0 get s0me key bindings cust0mized, and seems i b0rked s0mething up.  I was curri0us if there is a way t0 set all keybindings back t0 the default?.  I went thr0ugh the **System > ** 		**Preference > Keyboard** but did n0t n0tice anything askew..

As 0f right n0w the keys i have f0und 3 keys that n0 l0nger resp0nd.  They w0uld be the o, p and DEL keys.

Thanks.

ps, s0rry abu0t the w0nky typing.

---

### Post by aysiu on 2006-06-18
Try opening a terminal and pasting this command in: ```
sudo dpkg-reconfigure xserver-xorg
``` It's important you *paste* the command, as you obviously can't type it.

---

### Post by mscman on 2006-06-18
Are you sure it's not just your keyboard?  Have you tried using another keyboard (or trying that keyboard on another PC?)  

At first I was going to complain about your typing, until I read the last part, then I understood why! ](*,)

---

### Post by chomafin on 2006-06-18
[quote=mscman]Are you sure it's not just your keyboard?  Have you tried using another keyboard (or trying that keyboard on another PC?)  

At first I was going to complain about your typing, until I read the last part, then I understood why! ](*,)[/quote] 
hehe, Yes, i did try a different kb, s0rry f0r n0t menti0ning.  Seems f0r a bit, if i went int0 the kb 0pts, and switched it fr0m 101 back t0 a 104 kb w0uld fix it, but that has st0ped.  It seems it is an issue w/ x0rg as menti0ned, since i can b00t l0gin, as 0 is used.

and ab0ut the typing, crafty 1337ism and c0py/paste f0r the p hehe.  0i, wh0 w0uld have guessed s000 many 0's in n0rmal typing.

trying the x0rg n0w.

Edit : Aysiu, you sir rock :).  Thank you thank you.  Although, Do you know if that is the only way to go about it?.  Seems like I have way too many options that I could have screw up if I was not careful.  But none the less, as you can see in the edit it worked wonderfuly :)  WOOO!!.

---

