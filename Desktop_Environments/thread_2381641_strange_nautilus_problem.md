---
title: "strange nautilus problem"
date: 2018-01-03
forum: Desktop Environments
---

### Post by monkeybrain20122 on 2018-01-03
Hi, I am experiencing an odd problem with nautilus on one of my machines with Ubuntu 16.04.3 (with unity) and only on one machine, the other one doesn't have the problem. When first boot up or login if open Nautilus immediately it shows two icons on the launcher bar, in addition to the normal icon on top (first screenshot) another one shows up at the bottom (second screenshot) If I then close nautilus (the bottom icon then disappears) and try to open it by clicking again nothing happens for maybe 30 seconds, then click again and everything is normal and it is normal afterwards (only one icon on top and don't have to wait to re-open nautilus after closing) Also, if I wait for a minute or two after login or bootup before launching Nautilus then everything is normal (no double icon and and no waiting immediately after first launch)

This happens only on one machine and i notice this only recently (might be I didn't pay attentions before) Might have messed up some settings, wonder if there is any suggestion as to what I should check. Thanks.

---

### Post by DuckHook on 2018-01-03
When an icon is doubled, try checking contents of /usr/share/applications/ and ~/.local/share/applications/

Examine the contents of nautilus's .desktop file (although it is admittedly arcane).

There is also this: [https://beamtic.com/duplicated-icons-in-launcher](https://beamtic.com/duplicated-icons-in-launcher)

---

### Post by monkeybrain20122 on 2018-01-03
> **DuckHook said:**
> When an icon is doubled, try checking contents of /usr/share/applications/ and ~/.local/share/applications/

Examine the contents of nautilus's .desktop file (although it is admittedly arcane).

There is also this: [https://beamtic.com/duplicated-icons-in-launcher](https://beamtic.com/duplicated-icons-in-launcher)


But it is not always double, it only happens at the first launch after booting up or logging in and only if launching nautilus immediately after booting up or logging in If first launch happens a minute or so after boot or login then there is no double.

---

### Post by DuckHook on 2018-01-03
Did you try solution in link? Aside from trying that, I have no further ideas.

---

### Post by monkeybrain20122 on 2018-01-03
> **DuckHook said:**
> Did you try solution in link? Aside from trying that, I have no further ideas.


I know that procedure but it is for a different kind of problem that doesn't apply in this case. Thanks for trying to help anyway.

---

### Post by ventrical on 2018-01-05
> **monkeybrain20122 said:**
> Hi, I am experiencing an odd problem with nautilus on one of my machines with Ubuntu 16.04.3 (with unity) and only on one machine, the other one doesn't have the problem. When first boot up or login if open Nautilus immediately it shows two icons on the launcher bar, in addition to the normal icon on top (first screenshot) another one shows up at the bottom (second screenshot) If I then close nautilus (the bottom icon then disappears) and try to open it by clicking again nothing happens for maybe 30 seconds, then click again and everything is normal and it is normal afterwards (only one icon on top and don't have to wait to re-open nautilus after closing) Also, if I wait for a minute or two after login or bootup before launching Nautilus then everything is normal (no double icon and and no waiting immediately after first launch)

This happens only on one machine and i notice this only recently (might be I didn't pay attentions before) Might have messed up some settings, wonder if there is any suggestion as to what I should check. Thanks.

Have you buy chance installed another FM?

Can you try ..
```

sudo apt-get remove nautilus

```

logoff, then

```

sudo apt-get install nautilus

```

Regards..

---

### Post by monkeybrain20122 on 2018-01-06
> **ventrical said:**
> Have you buy chance installed another FM?

Can you try ..
```

sudo apt-get remove nautilus

```

logoff, then

```

sudo apt-get install nautilus

```

Regards..

No, just one FM. Tried reinstall already. But as I said, only happens at first launch after boot or login  and only if first launch happens immediately following boot or login. Otherwise it is completely normal.

---

### Post by mc4man on 2018-01-06
I'd probably approach like - 
First see if dbus plugin is enabled in compiz settings, if so disable. (longshot..
If no love there then set up a new user & see if problem exists there. If not,  on new user run
dconf dump / > 1.log
On present user do same to 2.log then see if any differences jump out
(- dconf dump can be targeted more specially by path, e.g. /org or /org/compiz ect.

---

