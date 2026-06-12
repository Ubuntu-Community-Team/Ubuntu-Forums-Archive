---
title: "Problem with Intel 82865G Graphicscontroller"
date: 2005-12-14
forum: Desktop Environments
---

### Post by mcp_dk on 2005-12-14
I have an IBM Thinkcentre 8187 with an Intel 82865G graphics controller
When i run the Ubuntu Live cd there is no problem with the graphics. But when i do a install to harddrive i can't log in. The login screen is all strange and garbled. 
If i log in anyway (it is possible its just that you cant see all the fields) the desktop is also completely broken and stretches off to the right. I have tried to reconfigure xserver-xorg but to no avail. The 82865 driver is not even available and if i choose the i810 driver it just won't launch X anymore.

Can anybody help me with this rather frustrating problem!?

---

### Post by mcp_dk on 2005-12-18
bumping this back on top (if possible)

---

### Post by Peter76 on 2005-12-18
Had some problems with an i810; solved it by telling how much memory to pass to it in the sudo dpkg-reconfigure xserver-xorg. Try that and post what happens

---

### Post by mcp_dk on 2005-12-26
[QUOTE=Peter76]Had some problems with an i810; solved it by telling how much memory to pass to it in the sudo dpkg-reconfigure xserver-xorg. Try that and post what happens[/QUOTE]
hmm i will try that. except i don't know how much memory to pass to it :-S

How much did you use?

---

### Post by antidrugue on 2005-12-26
Use the amount you want...

Like 8 mb, the number will be 8192.

---

