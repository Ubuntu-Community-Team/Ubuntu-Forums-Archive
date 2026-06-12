---
title: "Multiple x screen issue"
date: 2008-01-01
forum: Desktop Effects &amp; Customization
---

### Post by t3hi3x on 2008-01-01
I have a Nvidia 8600GT hooked up to a 24" LCD and 19" LCD. I have compiz running and used to run great on just the 24". I hooked up the 19" screen and enabled multiple x screens in the nvidia panel.

Compiz still runs just fine, but there is one issue. On screen 0 (the 24) anytime a new object is created, eg. pop-up window, create new windows etc, it lags in creating the object. Note this does not happen on screen 1. I think its a performance issue, but I don't think the 8600 should be struggling. And I also don't understand why more graphic intensive things like the cube or wobbly windows, paint fire, water, eg. has no trouble. Also the benchmark that comes with compiz stays in the green when i create an object.

I dont know if the problem is with compiz or with the x server. I do know with just metacity going it all works fine.

Anybody else experience this problem?

---

### Post by Josentutu on 2008-03-05
This is a known issue.

Compiz will be sluggish on the first screen when multiple X screens are used.

One option is to start Compiz on the first (or second) screen only. This is ok in my case as my second screen is TV-out and do not need it anyway. I do this by editing a line in my /usr/bin/compiz on gutsy (this is the script run by Ubuntu when desktop effects are enabled, it actually starts compiz with the appropriate window decorator).

```
COMPIZ_OPTIONS="--ignore-desktop-hints --replace --only-current-screen"
```

It is so far the cleanest way I found but is brittle on upgrades I guess.

I still get proper decoration (from metacity on the second screen as compiz will replace only on the first one).

If you use two separate X screens, an option would be to launch two instances of Compiz, one for each screen. This is not supported by the /usr/bin/compiz script so you would have to disable effects (to prevent the script from running) and launch the commands in you session or in a terminal.

I did not test it but something like the following might work:

```
DISPLAY=:0.0 compiz --only-current-screen &
DISPLAY=:0.1 compiz --only-current-screen &
```

I will do some testing.

---

### Post by Ozzee on 2008-04-15
Thank You!

You have no idea how long I've been looking for a good solution to that problem.

Working fine now \o/

---

