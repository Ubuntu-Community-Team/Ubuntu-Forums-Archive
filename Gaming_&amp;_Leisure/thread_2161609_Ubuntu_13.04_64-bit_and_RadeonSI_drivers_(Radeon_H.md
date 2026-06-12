---
title: "Ubuntu 13.04 64-bit and RadeonSI drivers (Radeon HD 7950)"
date: 2013-07-11
forum: Gaming &amp; Leisure
---

### Post by mmstick on 2013-07-11
Anyone know how to reliably get these Radeon HD 7xxx cards to function with open source drivers? Fglrx is too unstable and unplayable in almost every instance, while also producing a ton of bizarre glitches here and there in various programs.

I found [https://launchpad.net/~cybjit/+archive/ppa-glamor](https://launchpad.net/~cybjit/+archive/ppa-glamor) which finally allows me to use Gallium 0.4 on AMD TAHITI instead of Gallium 0.4 on LLVM, but trying to play a game on Steam will result in an error about installing S3TC texture support, which is already installed.

---

### Post by R33D3M33R on 2013-07-13
What fglrx version are you using and where exactly (which games/apps) do you see problems? The problem might be in Unity. Try to tweak that first by turning off effects, Unity tweak tool might help: [https://launchpad.net/unity-tweak-tool](https://launchpad.net/unity-tweak-tool)

---

### Post by King Dude on 2013-07-13
Open source Radeon drivers don't (fully) work, and hardware acceleration is unavailable. However, Ubuntu 13.10 with the new Linux 3.10 kernel will have improved support, and will allow for hardware acceleration.

Don't worry, support will come. If you don't want to wait for the stable version of Ubuntu 13.10, you could always help bugtest the experimental version.

---

### Post by BlueJayofEvil on 2013-08-12
> **mmstick said:**
> trying to play a game on Steam will result in an error about installing S3TC texture support, which is already installed.
Steam games require the **32-bit** S3TC package.

---

