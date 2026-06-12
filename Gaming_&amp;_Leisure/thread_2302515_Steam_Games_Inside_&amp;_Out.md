---
title: "Steam Games Inside &amp; Out"
date: 2015-11-11
forum: Gaming &amp; Leisure
---

### Post by david461 on 2015-11-11
Running Ubuntu MATE 64-bit 15.10:

I'm trying to run X3: Albion Prelude outside of Steam (copying the game directory and running the game there).

Is this proper place to ask for advice on fixing the issue? 
My issue is in the above game, **sound doesn't work. **

I'm certain Steam has it's own built in libraries. 
I'm guessing because some library used in Steam doesn't match the library I have installed without Steam,
since the game works proper in Steam and there's no sound without Steam.

This may not mean much but here is the questionable part of the output from the game's executable:

```

AL lib: (WW) alc_initconfig: Failed to initialize backend "pulse"
AL lib: (WW) alc_initconfig: Failed to initialize backend "alsa"
../src/X3/s_linux/init.cpp : Int_OpenAL_Init : 906 : al first err 0

```

Let's just say, there's no help I'll get from the developers, I'm lucky this game's been ported to Linux. Any direction would be greatly appreciated.

---

### Post by oscarivera9 on 2015-11-13
Contact whomever ported the game over to Linux, who BTW is usually a different company than the developers.  You'd be surprised at how many of these people I've contacted and I've usually been helped fairly quick.  For example, last game I asked for support was Middle Earth: Shadow of Mordor and Feral Interactive (the people responsible for the port) responded to my reply within two days and gave me a quick working solution.  I actually contacted them twice with two separate issues and both times they were prompt in their support.  Give it a try.
Also, if the game works under Steam, how come you're trying to run it without Steam?

---

