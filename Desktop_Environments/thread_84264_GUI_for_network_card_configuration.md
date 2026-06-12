---
title: "GUI for network card configuration"
date: 2005-10-30
forum: Desktop Environments
---

### Post by SadaraX on 2005-10-30
Is there a GUI in Kubunut that will let me change my static IP address or set my system to use DHCP? I am currently editing the files by hand, but is there a nice GUI program in KDE that can do it for me?

---

### Post by shinygerbil on 2005-10-30
Well, you can go to:

KControl -> Internet & Network -> Network Settings
or
System Settings -> Network Settings

depending on which one you use, they're both the same really :P
I don't know how well they work for normal network connections, but they're pretty useless for Wireless, I use a startup script..

Steve

EDIT: You'll need to be root to do this (kdesu kcontrol/kdesu systemsettings)

---

### Post by SadaraX on 2005-10-30
[QUOTE=shinygerbil]Well, you can go to:

KControl -> Internet & Network -> Network Settings
or
System Settings -> Network Settings

depending on which one you use, they're both the same really :P
I don't know how well they work for normal network connections, but they're pretty useless for Wireless, I use a startup script..

Steve

EDIT: You'll need to be root to do this (kdesu kcontrol/kdesu systemsettings)[/QUOTE]

Thank you. I actually did not know that was there (just sort of overlooked it).

I can change things if I run 'kdesu systemsettings' or 'kdesu kcontrol' I can access these fine. But if I go in as a regular user to kcontrol, go to 'Internet & Network -> Network Settings' and then click the "Administrator Mode", it prompts me for my password. 

If I enter my password, it does not enable admin mode, but goes back to the default window for kcontrol (all blue and shows briefly my system info). I cannot become admin through the "adminstrator mode" button. Anyone know why I have this problem?

---

### Post by beefsprocket on 2005-10-30
[quote=SadaraX]I can change things if I run 'kdesu systemsettings' or 'kdesu kcontrol' I can access these fine. But if I go in as a regular user to kcontrol, go to 'Internet & Network -> Network Settings' and then click the "Administrator Mode", it prompts me for my password. 

If I enter my password, it does not enable admin mode, but goes back to the default window for kcontrol (all blue and shows briefly my system info). I cannot become admin through the "adminstrator mode" button. Anyone know why I have this problem?[/quote] 
See this thread -- you are very much not alone: [http://ubuntuforums.org/showthread.php?t=75114]("http://ubuntuforums.org/showthread.php?t=75114")

---

