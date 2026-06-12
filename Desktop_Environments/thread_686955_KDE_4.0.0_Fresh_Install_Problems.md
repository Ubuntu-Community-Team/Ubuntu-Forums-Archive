---
title: "KDE 4.0.0 Fresh Install Problems"
date: 2008-02-03
forum: Desktop Environments
---

### Post by jlacroix on 2008-02-03
Today I decided to install Ubuntu, and KDE4 as a secondary desktop.

I did not install kubuntu-desktop, because all I wanted was Ubuntu and an install of KDE4.

Here are the problems I'm facing.

1.) I am using a laptop wireless connection which works under Gnome. In order for my wireless connection to work in KDE, I first have to log in to Gnome, log out, and then log in to KDE. If I start my laptop and then log straight into KDE the connection won't work.

2.) At least 70% of the icons are missing in the kickoff menu. The oxygen package is indeed installed. Icons for Firefox, Thunderbird, KDiskFree, KUser, Juk, Kmix, and many more are just question marks. If I try to open up the menu editor to change them back manually, it won't find the appropriate icons. However, Gnome shows all of the icons that KDE4 doesn't.

3.) In the kickoff menu, the applications are sorted alphabetically by the description, not the name of the program. It was like that too in KDE3 but at least I could change it. Is there a configuration item somewhere that will let me update that?

I'm rather frustrated, but I still love KDE4. It does everything else perfect. 

Any help is appreciated. Please note in advance that I have no intention of installing KDE3 on this machine.

---

### Post by kugn on 2008-02-03
I don't know about (2) and (3), but for (1), you could install KNetworkManager which hasn't been ported to KDE 4 yet, so it'll pull in quite a bit of KDE3 stuff.

Not sure if you could run just run the gtk nm-applet though. you might want to try that first.

---

### Post by jlacroix on 2008-02-03
That works, but how do I make that run on startup? I can't find the autostart folder in KDE4.

---

### Post by PatheticMoFo on 2008-02-16
Try ~/.kde4/Autostart

---

### Post by idipous on 2008-04-30
I have also installed knetworkmanager from kde 3.5 but my internet conncetion sets up only when I disable and re-enable the wireless card through knetworkmanager. Also if I stay idle for let's say a second the connection is lost. Also when I try to connect automatically with dhcp it fails to get an ip. 

Any help?
idipous

---

