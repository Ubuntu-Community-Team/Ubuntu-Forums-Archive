---
title: "Ubuntu 9.04 locking up - how do I diagnose the problem?"
date: 2009-05-12
forum: General Help
---

### Post by floweringmind on 2009-05-12
I need help diagnosing my system locking up?

The lockup appears to be random. This didn't happen when I was running the last version. I did a clean install.

I also upgraded to the latest Nvidia drivers which seems to have reduced the lockups. I kinda think Compiz might be the root of the problem.

I have looked in the /var/syslog but not sure what else to do.

Any help is greatly appreciated.

---

### Post by Firepony302 on 2009-05-12
are you using it when it locks up? or is it sitting idle?

---

### Post by floweringmind on 2009-05-12
Well I turned off Compiz and I still have lock ups. It now appears that VMWare is causing some sort of conflict with audio.

---

### Post by MaxIBoy on 2009-05-13
[LIST=1]
[*]Is your computer *totally* locked up? Or could you possibly get in there and have a look at dmesg?
[*]Try finding its IP address and pinging it from another computer to see how badly locked up it is. Verify that you can ping it while it's working normally, then try when it's locked up.
[*]Try running without VMware. Try running without sound. If either of those fix it, you may be onto something with your guess.
[/LIST]

---

### Post by djurny on 2009-05-13
you could also try downgrading nvidia drivers, i had some unexplainable lockups w/nvidia 180.51 on intrepid as well.. looked like downgrading sort of helped.. could not find any cause in any of the logfiles and system was totally unresponsive..

---

