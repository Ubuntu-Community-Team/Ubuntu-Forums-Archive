---
title: "Can't start Chromium snapd.apparmor error"
date: 2023-06-27
forum: Desktop Environments
---

### Post by alan-q on 2023-06-27
> alan@Lubuntu18:/tmp$ chromium
snap-confine has elevated permissions and is not confined but should be. Refusing to continue to avoid permission escalation attacks
Please make sure that the snapd.apparmor service is enabled and started.

*Despite the @ I'm actually on Lubuntu20.04 (upgraded from 18.04)*

The bug occurred after an unfortunate hard shutdown. 

There don't seem to be any recent relevant posts here. 

At [StackOverflow]("https://stackoverflow.com/questions/70053614/snap-confine-has-elevated-permissions-and-is-not-confined-but-should-be-refusin"), the most relevant thread has several answers with plenty of "It doesn't work for me" comments. 

Is there a definitive answer?

---

### Post by guiverc on 2023-06-27
[Lubuntu 20.04 LTS is no longer *supported* by the Lubuntu team]("https://lubuntu.me/lubuntu-20-04-lts-end-of-life-and-current-support-statuses/").

Ubuntu 20.04 LTS Desktop, Server, Cloud and Base have 5 years of *standard support*, with the *desktop flavors* only having three years, eg. the last release of [Ubuntu 20.04.6]("https://fridge.ubuntu.com/2023/03/23/ubuntu-20-04-6-lts-released/") can be seen here where you'll note no mention of *flavors* including Lubuntu (*flavors were all EOL & thus didn't include updated ISOs*).

FYI:  I wouldn't have gone to *stack overflow*, but the *snapcraft *store for clues, eg. [https://forum.snapcraft.io/t/snap-confine-has-elevated-permissions/31589](https://forum.snapcraft.io/t/snap-confine-has-elevated-permissions/31589) etc.  I believe I've had the issue you are experiencing, however I don't recall, and aren't willing to go remind myself as to why.

Also don't forget if you *release-upgraded* a 18.04 LXDE system to 18.10 or later & LXQt, you have other *potential **messy issues* existing on your system, as it wasn't a *supported* upgrade path for valid reasons (*though I acknowledge it did often reliably upgrade & many users seem oblivious to the less than ideal bits*).

---

### Post by alan-q on 2023-06-29
Thank you, @guiverc 

After a normal system update Chromium is working again.  

That said, if I run it from a terminal there are other snapd errors  

> update.go:85: cannot change mount namespace according to change mount (/var/lib/snapd/hostfs/usr/share/gimp/2.0/help /usr/share/gimp/2.0/help none bind,ro 0 0): cannot open directory "/var/lib/snapd": permission denied
update.go:85: cannot change mount namespace according to change mount (/var/lib/snapd/hostfs/usr/share/libreoffice/help /usr/share/libreoffice/help none bind,ro 0 0): cannot open directory "/var/lib/snapd": permission denied
update.go:85: cannot change mount namespace according to change mount (/var/lib/snapd/hostfs/usr/share/xubuntu-docs /usr/share/xubuntu-docs none bind,ro 0 0): cannot open directory "/var/lib/snapd": permission denied


but they don't -- yet ;) -- affect me :)

---

