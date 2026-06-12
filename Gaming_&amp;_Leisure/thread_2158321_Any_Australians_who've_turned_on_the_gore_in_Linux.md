---
title: "Any Australians who've turned on the gore in Linux L4D2?"
date: 2013-06-28
forum: Gaming &amp; Leisure
---

### Post by Horbo on 2013-06-28
In windows we just edited the steam_appid.txt file from "550" to 510", but I've done that in my Linux version, and it's not working - bodies just disappear as soon as the zombies die.
I also tried changing left4dead2/steam.inf from 550 to 510, but still no difference... :(

Does anyone have the solution for this in Linux?

---

### Post by Horbo on 2013-06-28
Just realised that was a silly question: I forgot that as well as changing that file you also have to start the game directly from its executable, not through Steam...so the same fix most probably will work.

Unfortunately though I'm not sure because I don't know how to run the Linux version without doing it through Steam!  In Windows it was just L4D2.exe, but here....? There's a couple of scripts or binaries in that folder: hl2 and srcds, but neither work (they both fail with error messages).

So I'll change my question to this: how do you run the Linux version of L4D2 directly, without starting it through Steam?

---

### Post by Horbo on 2013-06-29
Ah ha!  I have been given a solution for starting the game directly, instead of through Steam:

```
/your/path/to/SteamApps/common/Left\ 4\ Dead\ 2\ Beta/hl2.sh -game left4dead2
```

Some things to note: 
 - you will still need to have Steam running to play.
 - I could not start playing from the menu, I had to open the console and start playing with the "map" command (enable the console in the Mouse section of Options)
 - combined with the file edit above, this gave me full gore, hooray!

---

### Post by holastickboy on 2013-06-29
Thanks for sharing! I'm an Aussie, and totally hate the censoring of the game. My friends and I usually play L4D1 only because the zombies don't disappear on that (the disappearing bodies is very distracting, and totally detracts from the experience)

---

