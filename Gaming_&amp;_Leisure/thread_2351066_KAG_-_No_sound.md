---
title: "KAG - No sound"
date: 2017-01-30
forum: Gaming &amp; Leisure
---

### Post by zohran on 2017-01-30
Hello, sorry if i create second reply for KAG, but it's a different problem.

When i launch game, there is no sound.

I looked on the internet, it lacks the library **li32asound2**. But this bookseller no longer exists in the official depository. I installed **libasound2:i386** thinking it would fix the problem but it does not work.

Is there another 32-bit sound driver replacing **lib32asound2**?

---

### Post by DuckHook on 2017-01-31
It's not as simple as installing another driver. The game is designed with hooks for lib32asound2. It is highly unlikely to work with anything else. lib32asound2 was deprecated as long ago as Ubuntu Precise (12.04) and is no longer available on any current repository. It can likely be installed from an archive repository, but the chances are high that it in turn needs other dependencies and could even end up breaking your system.

Old releases are available on the following site: [http://old-releases.ubuntu.com/releases/](http://old-releases.ubuntu.com/releases/)

**WARNING**

I do ***NOT*** recommend installing old, obsolete, unsupported and insecure releases, especially for the sake of a game. In your case, you may have to go back as far as Lucid (10.04) to find this library. However, if it is that important to you, you might consider installing Lucid in a VM. Make sure you use it for nothing other than this game, disable networking in the VM, apparmor it ten ways to Sunday, and this might serve your needs.

---

### Post by Perfect Storm on 2017-01-31
As DuckHook said, it's on your own risk. Why not find a game on steam that are similar instead? There are loads of game there.

---

### Post by DuckHook on 2017-01-31
> **Artificial Intelligence said:**
> As DuckHook said, it's on your own risk. Why not find a game on steam that are similar instead? There are loads of game there.+1

…and in particular for the OP's needs: [http://store.steampowered.com/app/219830/](http://store.steampowered.com/app/219830/)

FWIW, there's a charm to old games that I find lacking in the slick overproduced newer ones, so I understand the desire to run them. I've got a few oldies still running in a VM of XP, and *that* OS is so awfully security-deficient that it makes Lucid look like an impregnable fortress surrounded by a crocodile-filled moat. If one isolates the OS in a VM and then isolates the VM from both the host and the world, it is safe enough to indulge in the charms of yesteryear.

---

### Post by zohran on 2017-02-01
I have found solution, you must install **libasound2-dev:i386** AND **libasound2-plugins:i386**, and sound finally work !

---

