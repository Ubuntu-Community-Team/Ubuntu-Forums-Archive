---
title: "Where are the THEME files kept?"
date: 2008-10-29
forum: Desktop Environments
---

### Post by w1av on 2008-10-29
I downloaded a few new THEMES. They were .gz files. I unzipped 'em but don't know where they go! /usr/shared/themes???? How do I find the proper folder for things like themes, splash screens, logon screens, wallpapers, etc. They are just text files. Thanks Ubuntu 8.04

---

### Post by damis648 on 2008-10-29
Go to System>Preferences>Appearance. From nautilus, drag in the .tar.gz to the theme tab.

---

### Post by ben2talk on 2008-11-01
> **damis648 said:**
> Go to System>Preferences>Appearance. From nautilus, drag in the .tar.gz to the theme tab.

That's the simplest installation, but it's not that simple - and your 'synaptic' still won't be themed, anythng under 'root' won't be themed by your account.

I keep my compressed files in a Storage partition/backup/linux/themes

I install them first by dropping them onto the Appearance window - that basically unzips and copies them to /ben2talk/.theme (a hidden folder)
There is a /usr/share/theme folder also
Root themes are in /root/theme.

The easiest way to install them to Root is either by finding out how to make a link, or (assuming space isn't tight) run Appearance as administrator, and then simply install them normally. that way, your 'root nautilus' window will be themed. Maybe that isn't clever, you could get confused.

---

