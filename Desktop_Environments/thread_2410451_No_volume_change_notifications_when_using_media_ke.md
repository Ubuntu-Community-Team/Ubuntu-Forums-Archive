---
title: "No volume change notifications when using media keys"
date: 2019-01-15
forum: Desktop Environments
---

### Post by taitair on 2019-01-15
[COLOR=#242729][FONT=Arial][FONT=inherit][FONT=inherit][COLOR=#242729][FONT=inherit]I am on Ubuntu 18.04 Bionic Beaver with kernel 4.20 from here: [/FONT][/COLOR][https://kernel.ubuntu.com/~kernel-ppa/mainline/v4.20/](https://kernel.ubuntu.com/~kernel-ppa/mainline/v4.20/)
[/FONT][/FONT][/FONT][/COLOR]
[COLOR=#242729][FONT=Arial][FONT=inherit]No idea how this happened. All of a sudden I noticed the notification popups were not producing any popping sound effects when I hit the media keys:
[/FONT]
[FONT=inherit][[IMG]https://i.stack.imgur.com/XUznq.png[/IMG]]("https://i.stack.imgur.com/XUznq.png")
[/FONT]
[FONT=inherit]If I go in the top right menu and click on the sound control or scroll on it with the mousewheel I can hear the popping sound effects:
[/FONT]
[FONT=inherit][[IMG]https://i.stack.imgur.com/b7Uuw.png[/IMG]]("https://i.stack.imgur.com/b7Uuw.png")
[/FONT]
[FONT=inherit]I can listen to audio without any problem. The only problem is volume change notification sounds. Usually people want those gone which is making my research quite difficult.[/FONT]
[FONT=inherit]I reinstalled alsa and pulse today. For a moment I had no sound at all. Still don't know why. Even reinstalled my kernel and graphics drivers. After reinstalling alsa and pulse I managed to get sound back but those pesky notifications are still producing no sound. Tried changing the value of "Event Sounds" to true or false inside org.gnome.desktop.sound with dconf-editor. Still nothing. Alerts volume is at 100%. Nothing is muted inside alsa-mixer. Every other sound works: games, music, video, web, etc.[/FONT]
[FONT=inherit]Small problem but really bugging me. Nice to have feedback when setting volume.[/FONT]
[FONT=inherit]Any ideas?[/FONT]

[/FONT][/COLOR]

---

