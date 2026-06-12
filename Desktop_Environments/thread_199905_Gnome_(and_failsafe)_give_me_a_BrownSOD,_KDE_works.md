---
title: "Gnome (and failsafe) give me a BrownSOD, KDE works?"
date: 2006-06-19
forum: Desktop Environments
---

### Post by Maelstrm on 2006-06-19
Hi all,

I'm currently running Ubuntu 6.06 (Dapper), with all the latest updates.

I've got Gnome and KDE installed.

Yesterday I was happily using Gnome, when all of a sudden my apps stopped responding and the taskbar (panel) started flashing. I was pretty confused, so I ended up using ctrl-alt-f2 to do a "shutdown -r -time now".

Booted back up, gdm loaded fine, asking for a username/password is fine, but when I try and log in to gnome or gnome-failsafe I get a brown screen with the panel/taskbar flashing - it looks like it's trying to load and failing - for a minute or so and then it stops trying to do so and I just have the brown screen and cursor.

I can ctrl-alt-functionkey to other shell logins, and top shows that nothing is eating more cpu/ram than it should.

KDE works fine.

I've tried mv-ing .gnome and .gconf then starting a gnome session but it didn't help.

I've searched google and Ubuntuforums, and the "solutions" I found (and tried) were:

-------------------------

esd is causing problems, try killing esd
-- I tried:
ctrl-alt-f2
sudo killall

but ctrl-alt-f7 (back to gnome) showed that I still had brown screen+cursor.

bonobo-activation is causing problems, try killing esd
-- I tried:
ctrl-alt-f2
sudo <bonobo's pid>

but ctrl-alt-f7 (back to gnome) showed that I still had brown screen+cursor.

network interface has issues with localhost
-- I tried:
check /etc/hosts for 127.0.0.1 <hostname>
my hostname existed so that wasn't a problem
sudo ifup lo gives me "ifup: interface lo already configured" so thats not the problem.

My date seems fine (date at commandline gives me today's date, and KDE shows the correct date, so I assume it is ok) which apparently cause this issue.

I've checked ownership in ~ and all seems ok. I did a chown <username> ~ -R for the sake of it to try and help, still no workies.

ps -e gives me:
[http://maelstrm.googlepages.com/now.txt](http://maelstrm.googlepages.com/now.txt)

-----------------------------------

Please help! Not having Gnome is rather annoying, and I can't think of what else to do :(

Any help is appreciated!

---

### Post by Maelstrm on 2006-06-20
Fix for anyone who comes across this (from another forum).

[quote=Col]
This sounds a little like the kde 'supertheme' problem. Did you recently install kubuntu-desktop?

If you did, take a look in KDE's system settings and change GTK Style from "use my KDE style" to something gnome-like (eg 'human'). That should do the trick.
[/quote]

Problem was (I assume) caused by some of the new KDE updates. I run dist-upgrades every few days, so they must be pretty recent ones. I haven't changed any theming options in the last day or so (for KDE or Gnome) and I've had both KDE and Gnome installed for months.

Might be worth a bug report?

---

### Post by shamrock_uk on 2006-06-20
[QUOTE=Maelstrm]Fix for anyone who comes across this (from another forum).



Problem was (I assume) caused by some of the new KDE updates. I run dist-upgrades every few days, so they must be pretty recent ones. I haven't changed any theming options in the last day or so (for KDE or Gnome) and I've had both KDE and Gnome installed for months.

Might be worth a bug report?[/QUOTE]

Hi Maelstrm, 

I've just posted a message to [#36256](https://launchpad.net/distros/ubuntu/+source/gtk-qt-engine/+bug/36256/+index) so we'll see what comes out of that. 

The patch appears to have been committed a while ago, yet if you've been regularly upgrading that's a little puzzling.

---

