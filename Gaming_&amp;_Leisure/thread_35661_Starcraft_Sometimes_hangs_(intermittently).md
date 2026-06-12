---
title: "Starcraft: Sometimes hangs (intermittently)"
date: 2005-05-19
forum: Gaming &amp; Leisure
---

### Post by Neo40 on 2005-05-19
Hi,

I have Cedega 4.3.2-1 (the paid version) installed. I can launch starcraft (or broodwar) and play without problem...even on battle.net! But sometimes, for unknown reason, sc wont start: it hangs on "loading...". I have to CTRL-Alt-Backspace
to exit. 

Anyone else has this problem? Any solution? 

Thanks

---

### Post by skoal on 2005-05-20
Yeah, strange indeed.  It only hangs the first time you launch it.  You kill X-server then try it a second time and it loads right up.  Don't know the cause of it, but launch the game with:

cedega --debugmsg warn+all,err+all starcraft.exe &> /tmp/sc.log and see if the logs show anything.

I don't have an explanation either, but when I get around to it, I'll try and debug it myself.

By the way, I can't get battle.net online to work.  When I type the second character into my account, the game crashes for some reason, and I can't even find the "create new account" button on battle.net login.  However, using the latest cedega, it does show battle.net the best so far (although some of the text looks wonky and shadowed for some reason).

---

### Post by Neo40 on 2005-05-21
[QUOTE=skoal]Yeah, strange indeed.  It only hangs the first time you launch it.  You kill X-server then try it a second time and it loads right up.  Don't know the cause of it, but launch the game with:

cedega --debugmsg warn+all,err+all starcraft.exe &> /tmp/sc.log and see if the logs show anything.

I don't have an explanation either, but when I get around to it, I'll try and debug it myself.

By the way, I can't get battle.net online to work.  When I type the second character into my account, the game crashes for some reason, and I can't even find the "create new account" button on battle.net login.  However, using the latest cedega, it does show battle.net the best so far (although some of the text looks wonky and shadowed for some reason).[/QUOTE]
Hi,

Thanks for your reply.
Happy to know I'm not alone with this problem....I tried the command you said to see if there are errors, but the sc.log is empty. 

On my another HDD, I have another distro installed (Archlinux) and I have installed Winex version 3.2. If I start the game with this old version, sc wont hang. The thing is I can't use it with Ubuntu because it gives me errors...

---

