---
title: "xorg? KDE 3.3?"
date: 2004-12-06
forum: Desktop Environments
---

### Post by jlacroix on 2004-12-06
Hello, me again.

I installed kde by APT and everything went fine, except it was KDE 3.2. That was fine and dandy, however, it didn't install correctly and it messed up my installation pretty bad, so I had to do an apt-get remove kde* to get rid of it.

The reason that I got rid of it is because Ubuntu was using KDE where KDE should not be. For example, on the Gnome Foot menu, there were three kde based links that when you opened them, brought up the KDE versions instead of the gnome versions. For example, the KDE "Find Files" was listed in the Gnome menu. What's worse, I set up my wife a user account and when she would go to her home directory under Gnome, it would pull up Konquerer instead of nautilus.

Anyway, that's why I removed KDE after installing it. Everything was back to normal when I removed KDE. However, I really would like KDE though, specifically KDE 3.3 if its possible, and hopefully KDE 3.3 wouldn't mess me up. Is it possible?

Also, how does one remove XFree and replace it with Xorg without any problems?

Thanks!

---

### Post by poofyhairguy on 2004-12-06
[QUOTE=jlacroix]Hello, me again.

I installed kde by APT and everything went fine, except it was KDE 3.2. That was fine and dandy, however, it didn't install correctly and it messed up my installation pretty bad, so I had to do an apt-get remove kde* to get rid of it.

The reason that I got rid of it is because Ubuntu was using KDE where KDE should not be. For example, on the Gnome Foot menu, there were three kde based links that when you opened them, brought up the KDE versions instead of the gnome versions. For example, the KDE "Find Files" was listed in the Gnome menu. What's worse, I set up my wife a user account and when she would go to her home directory under Gnome, it would pull up Konquerer instead of nautilus.

Anyway, that's why I removed KDE after installing it. Everything was back to normal when I removed KDE. However, I really would like KDE though, specifically KDE 3.3 if its possible, and hopefully KDE 3.3 wouldn't mess me up. Is it possible?[/QUOTE]

Honestly, KDE supprt is still lacking in Ubuntu. If you want 3.3, you either have to try to install it from the sid or use Mepis instead.

[QUOTE=jlacroix]Also, how does one remove XFree and replace it with Xorg without any problems?

Thanks![/QUOTE]

Upgrade to Hoary. But that way will give you some problems.

---

### Post by TravisNewman on 2004-12-06
It seems KDE 3.3 is also in hoary. If I go to any help menu and select "about KDE" it tells me it's 3.3.1, but some packages still say 3.2 (of course some Gnome packages still say 2.6)

---

### Post by peterdrucker on 2004-12-10
I upgraded to hoary and thought that X.org would replace XFree by magic. Didn't happened. I'd like to know how can I activate X.org and get transparent windows working :O)

Cheers
Peter

[QUOTE=jlacroix]Hello, me again.

I installed kde by APT and everything went fine, except it was KDE 3.2. That was fine and dandy, however, it didn't install correctly and it messed up my installation pretty bad, so I had to do an apt-get remove kde* to get rid of it.

The reason that I got rid of it is because Ubuntu was using KDE where KDE should not be. For example, on the Gnome Foot menu, there were three kde based links that when you opened them, brought up the KDE versions instead of the gnome versions. For example, the KDE "Find Files" was listed in the Gnome menu. What's worse, I set up my wife a user account and when she would go to her home directory under Gnome, it would pull up Konquerer instead of nautilus.

Anyway, that's why I removed KDE after installing it. Everything was back to normal when I removed KDE. However, I really would like KDE though, specifically KDE 3.3 if its possible, and hopefully KDE 3.3 wouldn't mess me up. Is it possible?

Also, how does one remove XFree and replace it with Xorg without any problems?

Thanks![/QUOTE]

---

### Post by HungSquirrel on 2004-12-10
Sounds like you uninstalled ubuntu-desktop before the upgrade.  Try re-installing it.

---

### Post by macewan on 2004-12-11
I'm currently running Ubuntu Hoary with X.org also at home, Warty at work. Haven't done the true transparent thing yet so if you have luck with it please share how.

---

