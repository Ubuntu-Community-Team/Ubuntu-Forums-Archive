---
title: "Debian Problems, please help"
date: 2007-12-12
forum: Debian
---

### Post by kevCast on 2007-12-12
Hello. I recently did a Debian Etch install on my system, and during my trek I had a few road blocks. If anyone has any input on how to fix these problems, I'd greatly appreciated it. Thank you.

I can't hear anything when I watch anything. Youtube videos, movies on my PC, music, etc. Could someone please help me with the sound?

When I add a style to ~/.fluxbox/styles, it doesn't show up on the right-click menu.

No torrent programs work. I tried Azureus, rtorrent, and now utorrent in wine. I'm guessing it has to do with my network, although I can surf the net just fine.

When I edit the .gtkrc-2.0 to add "gtk-icon-theme-name = "Buuf," it doesn't show up in Thunar.

I accidently forgot to add SSL encryption to my gmail account through Sylpheed. However, now I can't find how to edit my account in Sylpheed. Does anyone know how?

In Ubuntu, the command to remove unused dependencies is apt-get autoremove. What's the Debian equivilent?

How do I install a working spellchecker that will run with Abiword? I installed aspell, but no luck.

Whenever I start my system, before I login in on the CLI or startx, I get the following message:

```
ACPI: Unable to turn cooling device [dbbb1dec] 'on'
```
Is there anyway I can fix it so that it is on?

Any help is appreciated, thank you.

---

### Post by b9anders on 2007-12-13
> **kevCast said:**
> I can't hear anything when I watch anything. Youtube videos, movies on my PC, music, etc. Could someone please help me with the sound?

Be more specific - is this *only* when you watch something? or also just playing mp3? How do the sound settings in your mixer look?

> In Ubuntu, the command to remove unused dependencies is apt-get autoremove. What's the Debian equivilent?

aptitude is the preferred frontend for apt in debian now. SImply do 'aptitude autoremove <package>'

---

### Post by kevCast on 2007-12-13
> **b9anders said:**
> Be more specific - is this *only* when you watch something? or also just playing mp3? How do the sound settings in your mixer look?



aptitude is the preferred frontend for apt in debian now. SImply do 'aptitude autoremove <package>'

Both the gamix mixer and the alsa mixer are all the way up. The sound doesn't come out at all. There's no sound when I watch something in VLC, or listen to something in XMMS. There's no sound at all.

Alright, I'll try it. Thank you.

---

### Post by CREEPING DEATH on 2007-12-14
Use Deluge for BT, it's fast and GTK.  If it's not in the repos there's a .deb on the site.

CD

---

### Post by kevCast on 2007-12-14
It's not the torrent program. No matter what torrent program I do use, it can't find any seeders or leechers.

---

