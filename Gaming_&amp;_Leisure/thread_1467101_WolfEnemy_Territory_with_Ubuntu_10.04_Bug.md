---
title: "Wolf:Enemy Territory with Ubuntu 10.04 Bug"
date: 2010-04-30
forum: Gaming &amp; Leisure
---

### Post by mamous on 2010-04-30
[B]Hello all how are u 2day?...

[SIZE="4"]**I have two big problem with ET in New Ubuntu 10.04**[/SIZE]

1- There is no Servers List... 
Just say in console
> Requesting servers from the master...
Even if i leave it for 2 hours nothing listed
[COLOR="Red"]
But I can connect using IP.Address[/COLOR]

The second bug is...

2- Lest say u went to a server... the server have a mod Like NQ

There is a main menu for that server, when u choose it ET crash.


Any one knows how to Fix it ?


[COLOR="Blue"]Plz plz plz plz Help me... I'm addicted to that game[/COLOR][/B]

---

### Post by Sufiyan786 on 2010-05-01
I'm having the same problem. No servers show up in any game I play:(. I don't know if its because of 10.04 because I didn't try them on 9.10 before I upgraded.

---

### Post by pakerius on 2010-05-01
The problem must be caused by the last update to 10.04, because that's exactly when my ET also started finding list of servers from masterserver impossible. What's interesting when I was on 10.04 RC the ET worked just fine.

---

### Post by ChemicalForce on 2010-05-01
Ummm i don't know if it is a bug in 10.04 or not because i tryed it on my windows 7 machine it did the same thing maybe they're having server issues or something.

---

### Post by pakerius on 2010-05-01
If it was some sort of server issue on their side, then on forums on pages like crossfire.nu ([http://www.crossfire.nu/?x=forum&mode=view&id=1](http://www.crossfire.nu/?x=forum&mode=view&id=1)) there would be at least 10 topics about it :).

---

### Post by mamous on 2010-05-01
[B][COLOR="DarkGreen"]Well if u allow me to say...:P[/COLOR]

the servers thing is not a big deal for me :lolflag:


i want to see [COLOR="Blue"]my clan nq mod (main menu)[/COLOR]  but i can't if i choose it i have this error. i start et with terminal and i copy the error log
[/B]
**[COLOR="Red"]Here is it[/COLOR]**

> 
PIXELFORMAT: color(24-bits) Z(24-bit) stencil(0-bits)
MODE: 4, 800 x 600 windowed hz:N/A
GAMMA: hardware w/ 0 overbright bits
CPU: 
rendering primitives: single glDrawElements
texturemode: GL_LINEAR_MIPMAP_LINEAR
picmip: 0
texture bits: 0
multitexture: enabled
compiled vertex arrays: enabled
texenv add: disabled
compressed textures: enabled
anisotropy: 1.0
NV distance fog: disabled
Initializing Shaders
----- finished R_Init -----
copy /usr/local/games/enemy-territory/etmain/ui.mp.i386.so to /home/mamous/.etwolf/nq/ui.mp.i386.so
Sys_LoadDll(/home/mamous/.etwolf/nq/ui.mp.i386.so)... ok
Sys_LoadDll(ui) found **vmMain** at  0xa4b8f40  
Sys_LoadDll(ui) succeeded!
^3WARNING: Couldn't find image for shader ui/assets/logo_nq
^3WARNING: Couldn't find image for shader ui/assets/logo_ss
^1ERROR: ui/credits_main.menu, line 267: unknown menu keyword {
^1ERROR: ui/credits_main.menu, line 267: unknown menu keyword group
^1ERROR: ui/credits_main.menu, line 267: unknown menu keyword grpCreditsMain
^1ERROR: ui/credits_main.menu, line 267: unknown menu keyword type
^1ERROR: ui/credits_main.menu, line 267: unknown menu keyword 0
^1ERROR: ui/credits_main.menu, line 267: unknown menu keyword text
^1ERROR: ui/credits_main.menu, line 267: unknown menu keyword thanks to Pheno & Quad for the Lua code
^1ERROR: ui/credits_main.menu, line 267: unknown menu keyword textfont
^1ERROR: ui/credits_main.menu, line 267: unknown menu keyword 2
^1ERROR: ui/credits_main.menu, line 267: unknown menu keyword textstyle
^1ERROR: ui/credits_main.menu, line 267: unknown menu keyword 3
^1ERROR: ui/credits_main.menu, line 267: unknown menu keyword textscale
^1ERROR: ui/credits_main.menu, line 267: unknown menu keyword .2
^1ERROR: ui/credits_main.menu, line 267: unknown menu keyword textalign
^1ERROR: ui/credits_main.menu, line 267: unknown menu keyword 0
^1ERROR: ui/credits_main.menu, line 267: unknown menu keyword textalignx
^1ERROR: ui/credits_main.menu, line 267: unknown menu keyword 0.00
^1ERROR: ui/credits_main.menu, line 267: unknown menu keyword textaligny
^1ERROR: ui/credits_main.menu, line 267: unknown menu keyword 8.00
^1ERROR: ui/credits_main.menu, line 267: unknown menu keyword decoration
^1ERROR: ui/credits_main.menu, line 267: unknown menu keyword autowrapped
^1ERROR: ui/credits_quit.menu, line 267: unknown menu keyword {
^1ERROR: ui/credits_quit.menu, line 267: unknown menu keyword group
^1ERROR: ui/credits_quit.menu, line 267: unknown menu keyword grpCreditsQuit
^1ERROR: ui/credits_quit.menu, line 267: unknown menu keyword type
^1ERROR: ui/credits_quit.menu, line 267: unknown menu keyword 0
^1ERROR: ui/credits_quit.menu, line 267: unknown menu keyword text
^1ERROR: ui/credits_quit.menu, line 267: unknown menu keyword thanks to Pheno & Quad for the Lua code
^1ERROR: ui/credits_quit.menu, line 267: unknown menu keyword textfont
^1ERROR: ui/credits_quit.menu, line 267: unknown menu keyword 2
^1ERROR: ui/credits_quit.menu, line 267: unknown menu keyword textstyle
^1ERROR: ui/credits_quit.menu, line 267: unknown menu keyword 3
^1ERROR: ui/credits_quit.menu, line 267: unknown menu keyword textscale
^1ERROR: ui/credits_quit.menu, line 267: unknown menu keyword .2
^1ERROR: ui/credits_quit.menu, line 267: unknown menu keyword textalign
^1ERROR: ui/credits_quit.menu, line 267: unknown menu keyword 0
^1ERROR: ui/credits_quit.menu, line 267: unknown menu keyword textalignx
^1ERROR: ui/credits_quit.menu, line 267: unknown menu keyword 0.00
^1ERROR: ui/credits_quit.menu, line 267: unknown menu keyword textaligny
^1ERROR: ui/credits_quit.menu, line 267: unknown menu keyword 8.00
^1ERROR: ui/credits_quit.menu, line 267: unknown menu keyword decoration
^1ERROR: ui/credits_quit.menu, line 267: unknown menu keyword autowrapped
^1ERROR: ui/credits_nq_1.menu, line 267: unknown menu keyword {
^1ERROR: ui/credits_nq_1.menu, line 267: unknown menu keyword group
^1ERROR: ui/credits_nq_1.menu, line 267: unknown menu keyword grpCreditsNoQuarter
^1ERROR: ui/credits_nq_1.menu, line 267: unknown menu keyword type
^1ERROR: ui/credits_nq_1.menu, line 267: unknown menu keyword 0
^1ERROR: ui/credits_nq_1.menu, line 267: unknown menu keyword text
^1ERROR: ui/credits_nq_1.menu, line 267: unknown menu keyword thanks to Pheno & Quad for the Lua code
^1ERROR: ui/credits_nq_1.menu, line 267: unknown menu keyword textfont
^1ERROR: ui/credits_nq_1.menu, line 267: unknown menu keyword 2
^1ERROR: ui/credits_nq_1.menu, line 267: unknown menu keyword textstyle
^1ERROR: ui/credits_nq_1.menu, line 267: unknown menu keyword 3
^1ERROR: ui/credits_nq_1.menu, line 267: unknown menu keyword textscale
^1ERROR: ui/credits_nq_1.menu, line 267: unknown menu keyword .2
^1ERROR: ui/credits_nq_1.menu, line 267: unknown menu keyword textalign
^1ERROR: ui/credits_nq_1.menu, line 267: unknown menu keyword 0
^1ERROR: ui/credits_nq_1.menu, line 267: unknown menu keyword textalignx
^1ERROR: ui/credits_nq_1.menu, line 267: unknown menu keyword 0.00
^1ERROR: ui/credits_nq_1.menu, line 267: unknown menu keyword textaligny
^1ERROR: ui/credits_nq_1.menu, line 267: unknown menu keyword 8.00
^1ERROR: ui/credits_nq_1.menu, line 267: unknown menu keyword decoration
^1ERROR: ui/credits_nq_1.menu, line 267: unknown menu keyword autowrapped
UI_Alloc: Failure. Out of memory!
Received signal 11, exiting...
Shutdown tty console


---

### Post by Sufiyan786 on 2010-05-01
Another reason why they aren't having server issues is that no servers show up in** *any*** game.

---

### Post by pakerius on 2010-05-01
Ah.. now it seems to work again.. :P

---

### Post by mamous on 2010-05-01
[SIZE="3"][B]yes finally man..
I was dieing over there without ET...[/SIZE]

If u are a gd player come visit us in
[COLOR="Red"]-=CKU=-[Nq-XpSave] server[/COLOR]
[CENTER]217.163.23.27:27960[/CENTER]
u will fine me there -=CKU=-{McMaMoUs}[/B]:guitar:

---

### Post by Sufiyan786 on 2010-05-02
Yes! It's working!!

---

