---
title: "Dual Monitors on a Dell Latitude E6520"
date: 2011-12-05
forum: Dell Ubuntu Support (CLOSED)
---

### Post by CapnKirk on 2011-12-05
I have a question about how best to get dual monitors running on my Dell laptop.

System: Dell Latitude E6520 w/nVidia 4200m card; E-Port; two Samsung SyncMaster 215tw 21" monitors

Using the preinstalled Windows 7 nVidia driver software, I was able to get both monitors and the laptop display running as one big desktop.

I installed Ubuntu 11.10 64 bit as a guest system on a Window 7 host using VMPlayer.

What would be the correct software packages to be able to run all three displays in Ubuntu as I do in Windows? Also, where would the software repositories be?

TIA!

Kirk

---

### Post by aa-hcl on 2011-12-10
I have also E6520.

I currently run 3 displays connected to the laptop as one big X-screen and I still have the option to have a separate X screen on the laptop display.

My setup:

HDMI port -> one display 1920x1080
VGA port -> Matrox DualHead2go -> 2 displays 1920x1200 each.

(note that Nvidia card does NOT allow more than 2 "displays devices" on one X-screen, matrox is counted as one "display")

These 3 monitors give me a very wide single screen (5840x1200 + 1920x1080).

It is nice.

I so far did not bother to get a separate additional X screen on the laptop display.

---

### Post by CapnKirk on 2011-12-12
Thanks for your response!

Question: What repository and packages did you install in order to do this?

Kirk

---

### Post by rmkn85 on 2011-12-12
Did you manage to automatically change resolution (udev + auto-disper / xrandr) when laptop is docked / undocked and external screen is connected and disconnected?

---

