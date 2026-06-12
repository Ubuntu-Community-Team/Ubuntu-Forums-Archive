---
title: "2D MMO, ActiveX Errors"
date: 2005-12-15
forum: Gaming &amp; Leisure
---

### Post by Toxicity on 2005-12-15
Yea, the game I am attempting to run is Illutia ([www.illutia.com](www.illutia.com)) I registered one needed ocx and got the basics working, it updates fine, and even runs fine, until Login. After login I am confronted with a 429 ActiveX error now I know by winhoe friends this seems to be a common error for those running Illutia on win98. Yes well, I can't provide you with to much information as wine doesnt really give any specific output for it, but the game isnt that large... if anyone thinking they could give some sort of assistance its not that much of a chore to get it.

---

### Post by Toxicity on 2005-12-16
Anyone? I know it's probably a simple answer, but I'm new to Wine.

---

### Post by Toxicity on 2005-12-16
I hate to keep pushing my topic here, but I realised when I typed this (was very tired) I was really... REALLY vague...

Heres the backstory:

This is a 2D MMO (Obviously designed for windows uh-duh)

It runs on the VB system (VB6 judging by some included dlls)
This problem seems to be common for EVEN windows users playing the game, well not common exactly but a well seen problem, the people reporting this aren't exactly computer literate so asking them for specifics would be futile. but, the general concensus is thatit's a directX problem... with them DLLs rolling back or some other typical m$ prob.

Aaaaanywho, this is a pretty basic game its rendered in 2d squaretile, with directX. Since it's so simple of a game I'm sure its just something to do with DLL files I need to register or whatever. Now, what I did to even make the game run at all was copy the included (shuffling through files) cswsk32.dll to the pseudo-windows system32 directory and register it with winecfg since the patchers automated system had trouble registering it corectly on its own. 

Here lies my problem, when I get through the login and it conects to the gaming server blah blah blah, I recieve ActiveX Error: 429 ActiveX cannot create object (Thanks for that detailed report microsoft I SALUTE YOU!) This ofcourse is after being lazy old me and installing all basic software through WineTools, and finding my own quick work around for making vb6.0 install (deleting oleaut32.dll so it can place the newer one successfuly).

Soooo, yea, I'm left with itchy gaming fingers and a heavy heart. But, with my work drive (ex... well none) I am not compelled to switch to windows after rebooting and such JUST for Illutia (AND damned microsoft in its tempting ways sends me a few invites to the new Live Messenger, and Live*insert cliche internet term here*.)

Anyway hope that clears everything left vague up.

---

### Post by Perfect Storm on 2005-12-16
Never tried the game, I give it a go and see how it goes.

---

### Post by Perfect Storm on 2005-12-16
No go.

---

### Post by Toxicity on 2005-12-16
any specifics? What exactly is it that's failing? Is it a limitation of Wine, or a limitation of er... something else? Is it wines DirectX ability that causes the issue? Or at the very least what could you assume it is if you didnt find any details.

---

### Post by Toxicity on 2005-12-17
Well I'm giving it up since I had no info to go from. If anyone has any thoughts or atleast significant negative replies please do help out.

---

### Post by mcmuffy on 2005-12-17
I tried to install it via Cedega but no dice. I got a 'rich line insertion error' or something along those lines.

---

