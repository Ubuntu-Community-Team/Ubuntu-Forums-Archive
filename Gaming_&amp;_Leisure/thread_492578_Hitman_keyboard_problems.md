---
title: "Hitman keyboard problems"
date: 2007-07-04
forum: Gaming &amp; Leisure
---

### Post by Mike7171 on 2007-07-04
I installed Hitman (the first one) and it installed without any problems. The game runs perfectly other than a few graphical problems, but it's still completely playable. But for some reason my keyboard wont work in the game. I can still restart Ubuntu with Alt-Cntrl-backspace, and open some kinda menu with Cntrl, but no other keys work. Anyone know how to fix this? Any and all help is appreciated. 

Mike

---

### Post by marq on 2007-07-04
is it a usb or ps/2 keyboard, it might not be recognising it in wine 

can u still use ur mouse?

---

### Post by Mike7171 on 2007-07-04
It is a regular keyboard, and yeah my mouse works.

---

### Post by marq on 2007-07-04
peculiar well im stumped

---

### Post by Mike7171 on 2007-07-05
Nvm, It works now, but now my computer has no sound. Again. It fixed itself before somehow, but does anyone know how to fix this?

---

### Post by cogadh on 2007-07-05
Are you using Wine 0.9.40? The reason I ask is I have had similar problems since I updated to that version. Keyboard functions ceased to work in American McGee's Alice today (worked fine yesterday) and I seem to have random sound issues both in-game and after exiting a game. I know there were some significant changes made to the ALSA driver with this version that may explain the sound issues, but I can't find anything specific in the change log that might have caused the keyboard issues.

It would really suck if 0.9.40 is the reason for the problem, because the DirectX changes they made in this version seem to have corrected a ton of graphics issues I was having.

EDIT - BTW, did you do anything before the keyboard started working again in Hitman? I'm still stuck on Alice and can't seem to get moving again.
EDIT2 - Well, it looks like enabling "Allow the window manager to control the windows" fixed my keyboard issue, but I've never had to run Alice with that enabled before...
EDIT3 - Now it gets interesting. Turning on the window manager option seems to be what lets the keyboard work in Alice (tried it with and without twice now), but now Star Wars Knights of the Old Republic has the same problem and it doesn't matter if I have the option checked or not...
EDIT4 - Ha! Now my sound in KotOR is gone! Somethin' screwy going on here...

---

### Post by cogadh on 2007-07-05
New day, new post (I got sick of editing).

Okay, I removed Wine 0.9.40 and went back to 0.9.39. Guess what... the keyboard still doesn't work in KotOR, but the sound does (that could be random, due to a reboot). Alice continues to work fine with the "Allow window manager..." option checked and still has no keyboard function without it. I Googled for anything about keyboard problems with Wine and found nothing of any significance. I'm stumped, I hope someone else has a better idea, otherwise I'll have to boot back to my Windows XP partition to play games again.

EDIT - Here we go again, I always have to try just one more thing... 
This time I launched KotOR in its own X session, and now both the keyboard and sound work. I updated back to 0.9.40 and tried it again,,, they still work:) I still want to know why they stopped working in the first place, though.
EDIT2 - Also, Alice no longer requires the "Allow window manager..." option when launched in its own X session, the keyboard just works.

---

