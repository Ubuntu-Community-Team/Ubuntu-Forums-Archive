---
title: "Diablo II LoD: Unable to verify version"
date: 2007-08-15
forum: Gaming &amp; Leisure
---

### Post by Jimhawk on 2007-08-15
I've been having some recent problems with Diablo II: LoD through WINE. For the past week or so, it ran perfectly both online and offline. Currently, it still works for offline play. However, when I try to connect to Battle.net, I get an error message saying that BNet is unable to verify my application version. I tried reinstalling and repatching and it still gave me the same error message. Any idea of what could be wrong and how to fix it?

---

### Post by Beren Camlost on 2007-08-15
All I can think of is that you need the 1.11b patch. However, it's alot older than a week so I find it strange that you have this issue all of a sudden. Make sure you got the 1.11b patch or just try downloading it again from Blizzard's site and reapply it.

---

### Post by AntiRush on 2007-08-15
Some of the extrawork dlls were updated earlier this week.  You'll now need to run D2 from the Diablo II directory - something that wasn't necessary before.

```

#!/bin/sh
cd ~/.wine/drive_c/Program\ Files/Diablo\ II
wine "Diablo II.exe"

```

---

### Post by vexorian on 2007-08-15
that error appars on battle.net when the .exe is a cracked version

---

### Post by AntiRush on 2007-08-15
> **vexorian said:**
> that error appars on battle.net when the .exe is a cracked version

That may be one reason but I suspect it's not the original poster's problem, as he had it working last week.  There was an update in some of the extrawork dlls (the hack detection first implemented in 1.10).  Even running on true windows with a virgin executable this error will appear if the cwd isn't the Diablo II folder - I believe it runs some checks on files in that folder.

---

### Post by Beren Camlost on 2007-08-15
> **AntiRush said:**
> Some of the extrawork dlls were updated earlier this week.  You'll now need to run D2 from the Diablo II directory - something that wasn't necessary before.

```

#!/bin/sh
cd ~/.wine/drive_c/Program\ Files/Diablo\ II
wine "Diablo II.exe"

```

Oh, I wasn't aware of this. In which case, if the original poster is starting it from a desktop icon; just make sure the working dir is set to the Diablo II folder and he should be good to go. Or if he's running from a terminal, just apply your "fix" :D

---

### Post by disturbedite on 2007-08-15
@ AntiRush
excuse my ignorance, but what are the extrawork dlls?  i mean, i know what a dll is, but specifcally the extrawork ones are the ones i'm referring to...

---

### Post by AntiRush on 2007-08-15
> **disturbedite said:**
> @ AntiRush
excuse my ignorance, but what are the extrawork dlls?  i mean, i know what a dll is, but specifcally the extrawork ones are the ones i'm referring to...

On connecting to battlenet the Diablo II client will download what are known as 'extrawork' dlls - small binary files which are executed and do things such as memory scanning to check for hacks.  It seems that they are turned off and on from time to time - nobody (but blizzard) really knows why.  There are also instances where the extrawork is a dummy that doesn't actually do anything. 

Technical info:
They are send via the 0x4A packet on login and then the client replies with a 0x33 packet.  They are deleted immediately after use. The main things they check are the locations where known hacks are loaded into Diablo's memory space.

Extrawork was implemented in early 2004 I believe - patch 1.10.  With patch 1.11 blizzard added it's much more capable anti-hack system, Warden, to Diablo.  It currently only runs while in game, not on the chat or realm server.  They also still use extrawork from time to time for unknown reasons.

---

