---
title: "how minimize windows in foreground ?"
date: 2011-10-19
forum: Desktop Environments
---

### Post by jvajda on 2011-10-19
Hi by updating my Ubuntu 11.10 today i noticed that by clicking on minimize button on window, the window will minimize in background what cause that if you have some minimize effect in compiz, you will not see it because it will animate in background all other windows... does somebody know how to fix it ? Thanks in advance.

---

### Post by haqking on 2011-10-19
> **jvajda said:**
> Hi by updating my Ubuntu 11.10 today i noticed that by clicking on minimize button on window, the window will minimize in background what cause that if you have some minimize effect in compiz, you will not see it because it will animate in background all other windows... does somebody know how to fix it ? Thanks in advance.

not quite sure what you mean from your wording.

When you minimize the running app remains on your Unity Dock.

here is a useful chart for shortcuts and how to minimise etc

---

### Post by jvajda on 2011-10-19
look..lets say when you minimize window on your desktop in ubuntu what happends.. the window will minimize in the unity dock... but in Compiz Manager u can add an animation to the minimizing effect ...for example Magic Lamp, so your windows will minimize with nice Magic Lamp effect.. but when you open more windows on your desktop and you minimize a window,you expect to see that Magic Lamp effect...but you DONT, because the minimize effecet will play in behind all other windows and not in foreground..so that minimizing effect should be played in foreground all other windows for you to see the effect and not in background all other windows.. thats what im looking for ;)

---

### Post by jvajda on 2011-10-20
Here is a picture... the window "Documents" was in foreground when i clicked on minimize.. but as you can see the minimizing is playing on the background .. so if you have some maximized window it will play behind them ..so you will actually not see that your window is minimizing...

---

### Post by Copper Bezel on 2011-10-20
That's highly weird. It certainly wasn't the case in 11.04. Can anyone else confirm this? (I'm not on 11.10.) Since it essentially means that the minimize animation is broken, if this is something that happens universally in 11.10, it's definitely a bug.

---

### Post by jvajda on 2011-10-21
when i update from 11.04 -> 11.10 it was ok. The compiz was a bit lagy but for compatibility with 11.10 they made a compiz update and i think that update ****** it up. The day when i wrote this tread came out some updates for 11.10 and there was the one for compiz.. im not sure if its that compiz update or something else ...but the truth is that the minimizing effect is useless now :(

---

### Post by Copper Bezel on 2011-10-21
Huh. If we don't get any more responses, go ahead and start a bug report in Compiz's bug tracker under Ubuntu in Launchpad, _[here]("https://launchpad.net/ubuntu/+source/compiz")_. If it's something unique to your configuration, we'll probably find out that way.

One last thing you might check before filing a bug is to create another login account and see if the problem persists there. That way, we can rule out the possibility of a configuration glitch.

---

### Post by jvajda on 2011-10-21
ok thanks... ill wait till tomorrow and than ill write bug..

---

### Post by jvajda on 2011-10-21
OK.. so i tried it on a different laptop (Virtual Machine) ..fresh install Ubuntu 11.10 + newest updates (compiz also) and it does the same thing... probably it will be compiz  bug.. ill write there tomorrow and ill come back if its something new..

---

### Post by jvajda on 2011-10-23
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/879659](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/879659)

---

