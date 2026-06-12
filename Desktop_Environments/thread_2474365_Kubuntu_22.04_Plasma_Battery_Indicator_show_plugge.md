---
title: "Kubuntu 22.04 Plasma Battery Indicator show plugged in when running on battery"
date: 2022-04-27
forum: Desktop Environments
---

### Post by MikeBraxner on 2022-04-27
Hi all.

On a clean install of Kubuntu 22.04 on a Dell XPS 9500, the battery indicator widget keeps showing the status as 'plugged in but still discharging', despite the fact that the laptop is running on battery alone, i.e. no power supply attached. 

While this sometimes happens after a clean boot, it is guaranteed to happen after suspend, hibernate, and hybrid sleep ... and it's driving me up the wall. 'powertop' has no trouble figuring out that the laptop is running on battery, while 'sensors' seem to indicate that a power supply is attached, but not providing any amps.

Any bright ideas how to fix this?

---

### Post by ActionParsnip on 2022-04-27
Do you have the latest BIOS? This can help

---

### Post by MikeBraxner on 2022-04-27
Yap, the Bios is fully up to date. 

But this sort of thing used to happen on an off on 21.10, 21.04, 20.04, ... it's not new, but it didn't used to be this pervasive.

---

### Post by MikeBraxner on 2022-05-05
Turns out, this is a kernel bug that has been around - in various incarnations - for years. 

The current best advice seems to be: 

The effect seems to reliably occur after a ***cold** boot on battery power only*, and remains after subsequent soft restart, suspend, or hibernate.

After a ***cold** boot with power supply plugged in*, the effect does **not** occur, nor after any subsequent soft restart, suspend, or hibernate.

So, **only cold boot with power supply plugged in** ... ;-)

---

