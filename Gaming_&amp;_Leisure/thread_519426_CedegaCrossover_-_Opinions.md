---
title: "Cedega/Crossover - Opinions?"
date: 2007-08-07
forum: Gaming &amp; Leisure
---

### Post by Sam Liu on 2007-08-07
Anyone try Cedega for Linux? I got version 6.0 and it seems to work decently. CrossOver by Codeweavers seems to run windows games very slowly and inefficiently though.

Anyone else try Cedega or Crossover, or have any suggestions for a different windows gaming utility?

I'm interested in playing RTS games on linux.  Doesnt seem like they're well supported.

Thanks

---

### Post by Sindwiller on 2007-08-07
Wine does normally a better job than Cedega, except when it comes to the latest games...

```
sudo apt-get install wine
```

Or get the latest Wine version from the repositories [here]("http://winehq.org/site/download-deb")

[http://appdb.winehq.org/](http://appdb.winehq.org/) - check if your program/game runs in Wine

---

### Post by Corvo78 on 2007-08-07
I use Crossover.
I use it to play World of Warcraft. It is a supproted game and on my system it runs flawlessly.
I also tried Steam (Crossover supported) and that worked well too, although Crossover only supports Dx8 (so Half-Life 2 looked far less nice then on Windows).

---

### Post by atomkarinca on 2007-08-07
i used all three of them (wine, cedega, crossover) and i should say wine is more than enough for me. when i can't get games working with wine, cedega seems to be helpful *half* of the time. i don't like crossover because i didn't have single game that doesn't work on wine or cedega and it works on crossover. it's waste of money for me.

---

### Post by Eddie Wilson on 2007-08-07
I've used Crossover, Cedega, and Wine. Wine is very good at playing most of the games I want to play. Crossover is very good at all other windows apps I need to run plus gaming support is getting better. Cedega is a waste of money in my op;inion. Most games will not play under Cedega that I want to  play and the ones that will will also play under wine. Also they take and give nothing back to anyone. Each to his own but in my opinion, Wine is great, CrossoverLinux is great, and Cedega is a rip.
Eddie

---

### Post by huangja on 2007-08-07
For some reason, Crossover is the only emulator that runs steam without any problems or bugs for me. I use Cedega for Starcraft and Warcraft 3. Wine seems to be making a lot of improvements, but it has been too buggy when I try to run anything on it.

---

### Post by cogadh on 2007-08-07
Don't like either, Wine works the best. 

Cedega:
[LIST]
[*]It's a rip-off (they charge money to sell you nothing but a GUI and the work that was already done for free by the Wine developers)
[*]Has terrible customer service
[*]Does not have full DirectX support
[*]Does have some support for proprietary copy protection schemes that both Crossover and Wine do not have
[*]Does not contribute back to the source project (it is a based on a pre-GPL version of Wine)
[/list]

Crossover:
[list]
[*]Is more geared towards running office applications (though it does have some game support)
[*]Great customer service 
[*]Based on an earlier version of Wine (does not have full DirectX support)
[*]Primary financial supporter of the Wine project, so using it does contribute to the further development of Wine
[/list]

Wine:
[list]
[*]Free (gratis and libre)
[*]Full DirectX support through DX 9 (DX 10 under development)
[*]Constantly updated (at least monthly)
[*]Excellent community-provided support
[*]Very incomplete copy protection support (but still under development)
[*]Has no GUI, but is still relatively simple to use from the terminal
[/list]

Long story short, if you feel you must pay for a Windows compatibility product, go with Crossover, at least it continues to benefit the source project, the way open source is supposed to be (unlike Cedega). Otherwise, use Wine.

> **huangja said:**
> ...Crossover is the only emulator ...
Wine, Cedega and Crossover are not emulators. They are alternate implementation of the Windows API that allow the Windows executable to run in the Linux environment. Emulators create a virtual representation of a complete operating environment, including the hardware, in order to run proprietary software. That's not what Wine/Crossover/Cedega do.

---

### Post by Corvo78 on 2007-08-08
> **cogadh said:**
> Long story short, if you feel you must pay for a Windows compatibility product, go with Crossover, at least it continues to benefit the source project, the way open source is supposed to be (unlike Cedega). Otherwise, use Wine.

After trying the Crossover Trial with WoW, I knew that using Wine would most likely work as well.
I ended up choosing Crossover because it was A) simple in use and _B) supporting Wine's development_.

---

