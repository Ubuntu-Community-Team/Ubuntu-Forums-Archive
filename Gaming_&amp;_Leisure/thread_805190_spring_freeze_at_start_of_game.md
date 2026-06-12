---
title: "spring freeze at start of game"
date: 2008-05-23
forum: Gaming &amp; Leisure
---

### Post by zorkerz on 2008-05-23
I just installed spring from launchpad repos for hardy. I also installed the mod BA v6.21. When I try to start a single player game with the map SmallDivide and the BA mod it loads and begins to count down from 3 to start. As soon as the countdown is finished x freezes. 

I can restart x with ctrl+alt+bkspc but login in, loading applications and doing anything is painfully slow. System Monitor shows an interruptable process called spring running.

I have restarted the computer and it is still unbelievably slow. To bring the system back to full speed I must uninstall spring. These problems do not begin until i have attempted to start a game but do not go away until it is uninstalled.

This is a a 64 bit 8.04 hardy install. Does anyone know how i can begin tracking down this potential bug in spring?

---

### Post by zorkerz on 2008-05-23
So I have found that restarting the computer does actually end the spring process and make the computer work at normal speeds again. Uninstalling spring still requires a full restart for the spring process to go away.

---

### Post by Vadi on 2008-05-23
Did you get the OTA content? BA requires it.

[http://spring.clan-sy.com/wiki/Ubuntu_install#OTA_Content](http://spring.clan-sy.com/wiki/Ubuntu_install#OTA_Content)

And btw you can kill processes with "killall <process name>", or the system monitor

---

### Post by zorkerz on 2008-05-23
Thanks for the reply. 
I have the ota content at least I believe I did. I installed it according to the instructions for ubuntu. I think the spring lobby also has a way to install it. 

system monitor does not end the process when i press end process. It ends others just not spring when its uninterruptible.
I have not tried the killall command.

I am starting to think it may be something to do with computer ai.

I have 6 ai options. The system appears to freeze when i use the first one (KAI-0.2).
It does not freez with testglobalai which is essentially no ai. I was just able to play breifly with jcai but steam closed almost as soon as i encountered the ai. 

I was also having the same freezing problem with the CA stable-1929 mod, leading me to belive more strongly that it is an ai problem. 

Finally i have seen a bug report flash up quickly once or twice but it goes away too fast for me to know what it is.

Im starting to think i may have more success with the windows version through wine.

---

### Post by Vadi on 2008-05-23
You won't, because this is a Spring problem. Try using the "kill" option instead of "end" in the system monitor. As for AI, only the RAI works with CA, others freeze / crash it.

---

