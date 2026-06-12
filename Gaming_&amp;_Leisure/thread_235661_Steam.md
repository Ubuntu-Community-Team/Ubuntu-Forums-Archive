---
title: "Steam"
date: 2006-08-13
forum: Gaming &amp; Leisure
---

### Post by kbsuperstar on 2006-08-13
Yeah, so I installed Steam with Wine, but whenever I open it I get the "Steam updating..." message and after a few sec (up to about 15%) it just closes. How do I fix this? Are there any manuals on installing Steam + counter-strike games with Wine??

---

### Post by scotty2hott2k on 2006-08-13
please research before posting as it has been asked and answered many times, simple google would have given you [this]("http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Steam&back=HOWTO+INDEX+Wine+Games") page which tells you exactly how and what to do if you get any errors.

good luck :)

---

### Post by kbsuperstar on 2006-08-13
I have already followed [this guide]("http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Steam&back=HOWTO+INDEX+Wine+Games") for installing Steam, but it seems I still need help.

The problem is that when I load Steam, it won't let me type anything into the account name or password boxes. I click the cursor to the text box and type, but nothing happens (the white (ie - cursor) in the box still blinks, so I know it hasn't frozen). I can click the "remember password box," if that means anything. I have the fonts needed (tahoma.ttf). Any suggestions?

---

### Post by scotty2hott2k on 2006-08-13
well not being able to type anything in didnt work for me until i installed the font tahoma.ttf (although you say you already have it). did you install it to the right place?

ie.

/home/user/.wine/drive_c/Windows/fonts

if its in there then the pannel should show all the buttons right and you should be able to type in it.

if it still doesnt work, type winecfg in the commandline and tick the graphics option 'virtual desktop'. then re-run steam and it should allow you to input your login.

---

### Post by kbsuperstar on 2006-08-13
The desktop emulator worked. Thanks!

---

### Post by Jedeye on 2006-08-13
> **kbsuperstar said:**
> The desktop emulator worked. Thanks!
would like to know if the games work well for you

---

### Post by kbsuperstar on 2006-08-13
Eh, I'm getting problems again. I got into counter-strike (Condition Zero) fine after downloading and headed straight for my favorite server. When I got in-game, my mouse wouldn't work, and my mic wouldn't work (I don't think Ubuntu has recognized my microphone yet). I tried to reload Steam with the desktop emulator ('cause my login is saved now), but it just froze up and I had to reboot. I'm going to look back at the tutorial, but if you have suggestions, it'd be a help!

---

### Post by kbsuperstar on 2006-08-13
...

---

