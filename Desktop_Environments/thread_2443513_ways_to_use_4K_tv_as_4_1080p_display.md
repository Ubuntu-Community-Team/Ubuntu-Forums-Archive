---
title: "ways to use 4K tv as 4 1080p display?"
date: 2020-05-16
forum: Desktop Environments
---

### Post by unclesam-xu on 2020-05-16
I know in windows , there are softwares that can split a 4K tv to 4 1080p display. Is there a way to do that in LINUX specially in ubuntu? better have graphic interface.

---

### Post by ericduvic on 2020-05-17
For my 4k TV display I'm connecting via my NVidia graphics card. In the NVidia Settings app, I set advanced settings to ViewPortIn and Panning as 1920x1080, and my ViewPortOut as the native resolution: 3840x2160+0+0

That seems to take the content and scale it out to the equivalent of 1080 display.

> **unclesam-xu said:**
> I know in windows , there are softwares that can split a 4K tv to 4 1080p display. Is there a way to do that in LINUX specially in ubuntu? better have graphic interface.

---

### Post by DuckHook on 2020-05-17
> **unclesam-xu said:**
> I know in windows , there are softwares that can split a 4K tv to 4 1080p display. Is there a way to do that in LINUX specially in ubuntu? better have graphic interface.
You could run a window manager environment that is devoid of launchers, trays or bars of any kind like plain openbox. Then run four containers or VMs within it, each manually tiled to achieve the look you want.

Alternatively, you could run a pure tiling window manager like i3wm, create four tiles and run a container or VM within each of those.

You are not limited to 4 tiles either. You could have as many as you want—6, 8, 10, 12—as many as you can track and juggle. If you combine this with multiple desktops, you could conceivably have over a hundred sessions going at once.

How anyone could multitask among that number of simultaneous feeds is beyond me, but it answers your question.

For a primer on window managers and tiling WMs like i3wm, see the link in my sig: *The Best 'buntu Flavour*.

For a primer on containers, see the link in my sig: *Sandboxing Apps with LXD*.

For a brief intro to virtual machines: [https://help.ubuntu.com/community/VirtualMachines](https://help.ubuntu.com/community/VirtualMachines)

---

