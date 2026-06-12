---
title: "Power Statistics (estimating) forever"
date: 2011-04-02
forum: Desktop Environments
---

### Post by pcar916 on 2011-04-02
My search provided no answers that I can find on this specific topic. Up front I don't know if this is a Ubuntu or a Gnome issue.

The environment:
1. Toshiba Satellite Turion 64x2  (dual processor) 
2. Dual-boot with Windows 7 Ultimate
3. 32 bit Maverick Meerkat 10.10 (fully up to date, recently upgraded from Lucid Lynx 10.04)
4. Gnome 2.32
5. New battery and old battery act the same

Fact: 
- 10.04 did not have this problem.  When clicking on the Power Statistics  icon in Lucid Lynx I got a power percentage readout immediately. 

The Problem:

- Since installing 10.10 clicking on the icon gives me Power Statistics (estimating)
- Going into the applet I have to go to the second tab to get a graph of my power usage and read the current power level from there.
- Preferences don't allow me to change the display.

The effect:
- When the window pops up to tell me that the power is critically low, it's too late. Even when I have the power cord ready and it's at most a few seconds before plugging back in, the computer shuts down.
- The "red" range on the icon display is too large

Suggestion: Most critical first.
1. Insert a preference that allows the user to choose at which percentage to display the critical power level window and have enough time to plug in the power cable.
2. Put a numeric power percentage readout on the icon one click away and get rid of the "estimating" readout.
3. Make the "red" range on the icon start at 10% rather than so high one has to watch it be red too long to mean anything critical.

Any help here would be appreciated. I like 10.10 and spend most of my time in it rather than Windows.

Thanks in advance.
Ron

---

### Post by kio_http on 2011-04-02
In terminal, type 

```
sudo acpi
```

and produce output.

Does the power monitor work in other os's currently e.g windows?

---

### Post by nealmcb on 2011-04-02
I see the same "estimating", forever, after several full discharge/recharge cycles.   For me, acpi says this now: 

 Battery 0: Charging, 89%, rate information unavailable

This is on a new System76 lemu2

---

### Post by nealmcb on 2011-04-02
A workaround is described at the launchpad bug for this:

 Power applet never shows batterly level - always shows "estimating"
 [https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/672770](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/672770)

---

### Post by pcar916 on 2011-04-02
> **kio_http said:**
> In terminal, type 

```
sudo acpi
```and produce output.

Does the power monitor work in other os's currently e.g windows?

The power monitor works fine in Windows 7 and did in 10.04 as well.   The command sudo acpi reports "command unavailable" so now I'll figure out where ti is, how to install it and report back.

Thanks!

---

### Post by pcar916 on 2011-04-02
> **nealmcb said:**
> I see the same "estimating", forever, after several full discharge/recharge cycles.   For me, acpi says this now: 

 Battery 0: Charging, 89%, rate information unavailable

This is on a new System76 lemu2

It's been at least 50 complete cycles and the behavior hasn't changed yet.

Thanks!

---

### Post by pcar916 on 2011-04-02
> **nealmcb said:**
> A workaround is described at the launchpad bug for this:
Power applet never shows batterly level - always shows "estimating"
 [https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/672770](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/672770)


Problem fixed with this solution. Thanks!

---

