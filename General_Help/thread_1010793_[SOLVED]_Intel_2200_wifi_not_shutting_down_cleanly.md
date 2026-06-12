---
title: "[SOLVED] Intel 2200 wifi not shutting down cleanly"
date: 2008-12-14
forum: General Help
---

### Post by Paqman on 2008-12-14
My girlfriend has a laptop with an Intel2200 wifi card in it. Recently she's noticed that Intrepid has started spamming this error message up onto the screen on shutdown:

```
ipw2200: Failed to send SYSTEM_CONFIG: Already sending a command.

```

This kills the splash screen and stalls the shutdown procedure for some time while this error repeatedly times out. Based on some Googling I disabled SSID broadcast on the wireless router. This cleared the problem on the laptop, but has lead to very unreliable connecting at login, which is obviously no good either.

Any clues about how to configure the 2200 so that it will shut down more gracefully? This problem has only popped up recently, so i'm assuming it's an update that has chucked a spanner in the works.

---

### Post by Paqman on 2008-12-15
Right, managed to dig up a solution to this. The problem is related to this bug: 

[ipw2200 driver no longer works with wpa2 network]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/264104")

And can be rectified with the simple solution found in that bug's comments.
[LIST=1]
[*]Create a file at /etc/modprobe.d/ipw2200
[*]Insert into file: options ipw2200 hwcrypto=1 associate=0
[/LIST]

Some people report that the hwcrypto=1 entry is superfluous. I haven't had a moment to try that yet myself.

---

