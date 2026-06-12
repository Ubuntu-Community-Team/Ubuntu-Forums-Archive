---
title: "Kodi Steam addon only launches once"
date: 2017-06-24
forum: Gaming &amp; Leisure
---

### Post by CatKiller on 2017-06-24
Bit of a long shot posting here, but hopefully someone has some experience.

I've installed Ubuntu on a NUC connected to my TV.

The NUC automatically logs in and launches Kodi.

Kodi can be controlled using my TV remote through HDMI-CEC.

There is an addon for Kodi that launches Steam in Big Picture Mode.

Steam BPM can be controlled by the Steam controller.

Exiting Steam goes back to Kodi.

This is all working perfectly.

Unfortunately, having exited Steam and gone back to Kodi, the Kodi Steam addon will not launch for a second time. This is annoying, since I'd hoped to leave the NUC on doing lightweight server things, and switch the telly over to Kodi for films or games as and when the urge hits.

It's possible that there's a log somewhere with useful information, or a script that can be tweaked somewhere, or something. My experience with Kodi started yesterday, though. I'd be grateful for some troubleshooting assistance.

---

### Post by CatKiller on 2017-06-26
It seems that the script doesn't terminate when Steam exits, which is why it can't be launched again. Unfortunately, killing the script remotely relaunches the scripts, which relaunches Steam.

---

### Post by CatKiller on 2017-06-26
I switched to the Kodi Launches Steam addon instead. That seems to work.

---

