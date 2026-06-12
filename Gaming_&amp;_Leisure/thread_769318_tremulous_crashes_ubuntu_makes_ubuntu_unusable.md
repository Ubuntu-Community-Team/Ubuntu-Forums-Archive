---
title: "tremulous crashes ubuntu makes ubuntu unusable"
date: 2008-04-26
forum: Gaming &amp; Leisure
---

### Post by ekravche on 2008-04-26
Every once in a while tremulous crashes ubuntu. I can't ctrl+alt+backspace to restart gdm, and I can't ctrl+alt+f1 to go into the console. All I get is a black screen with the mouse cursor going between busy and pointer states.

Any help would be appreciated.

---

### Post by Officer Dibble on 2008-04-26
I used to get this now and again, sadly it was never resolved. I don't have the problem now because I don't play the game any more. :(

---

### Post by FrozenFox on 2008-04-26
I've played tremulous for several hours a week for a very long time now, both on ubuntu hardy and now arch dont-panic.. never crashed on me once. Perhaps you should make a log file of your game to help find the issue.

logsave ~/Desktop/tremulous.txt /usr/bin/tremulous   

(assuming you have a /usr/bin/tremulous. if not, put in the appropriate path)

Post it next time your game crashes, if it actually has anything strange at the end.

Btw. would help to know if you both have similar strange specs. 64 bit? ati?

---

### Post by ekravche on 2008-04-26
Mine is an integrated intel 82915G/GV/910GL Integrated Graphics Controller 3Ghz CPU. It's a 2 years old machine

---

### Post by ekravche on 2008-04-26
Here are the last few lines in the log 

> Self-Appointed^7 was bitten by rrrrr^7
dragoon hunter^7 was mauled by JollyAzN^7's Tyrant
(^4AB^9^7ITI^4NO^7): ^5naded babyyyyyyyyyyyyyy
^1G^7O^1O^7N^7 felt the full force of brown^7's lucifer cannon
Cors^7 was zapped by a tesla generator.
[H] ^4AB^9^7ITI^4NO^7: ^2nobosy died?
[B]intelWaitIrq: drmI830IrqWait: -16
/usr/games/tremulous died with exit status 1[/B]

Sat Apr 26 16:56:35 2008
----------------

---

### Post by ekravche on 2008-04-27
It seems to happen when I play tremx. That is all the expansion maps.

---

### Post by FrozenFox on 2008-04-27
Seems to be perhaps a video driver problem with something in tremx (invisibility maybe?) or one of the maps. Note which map youre on when it crashes and try to reproduce it in alone (ie create your own passworded server and load into that map to see if you can find out how to crash it).. i think it keeps that in the log too.

---

### Post by ekravche on 2008-04-27
Actually this happens with any map, not just tremulous x maps. Here is various output that may be helpful. I've used lspci -v and the output of the tremulous error log. I'm not sure what else to attach.

---

### Post by ekravche on 2008-04-27
It's filed as a bug here [https://bugs.launchpad.net/ubuntu/+source/tremulous/+bug/175004](https://bugs.launchpad.net/ubuntu/+source/tremulous/+bug/175004). I'm attaching the output from tremulous as well

---

### Post by ekravche on 2008-05-13
It stopped crashing for me after. I changed the resolution back to 800X600. I was using a non standard resolution before

---

