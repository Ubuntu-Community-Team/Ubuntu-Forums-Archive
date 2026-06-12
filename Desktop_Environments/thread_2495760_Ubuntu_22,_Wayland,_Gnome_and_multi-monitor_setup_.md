---
title: "Ubuntu 22, Wayland, Gnome and multi-monitor setup after screen lock"
date: 2024-02-29
forum: Desktop Environments
---

### Post by karimarttila on 2024-02-29
I have a Lenovo laptop with three external monitors. I have two thunderbolt cables that connect my laptop to two monitors, and the third monitor is connected via daisy-chain. The three external monitors are Lenovo ThinkVision P27q-10 27" WQHD monitors.
I am using Ubuntu 22.04.4 LTS, Wayland and Gnome 42.9. I have Intel UHD Graphics 630 card with i915 driver.

I am using this setup so that I have a big virtual screen (using Ubuntu Settings / Displays => I drag the four monitors side by side). Scale is 100% and I am not using Fractional scaling. This setup works just fine.

But. After screen lock the windows move from one monitor to another. Sometimes also the order of the monitors has changed. So, after screen lock, I have to reorder the monitors to reflect the physical display setup, and then move the windows to the right monitors. This is rather frustrating.

I am wondering if this behaviour is caused by the monitors waking from sleep at some random order? I am also wondering if there is some configuration option which, at screen lock, would save the multi-monitor setup and the window locations in each monitor, and would restore this setup after screen lock?

---

