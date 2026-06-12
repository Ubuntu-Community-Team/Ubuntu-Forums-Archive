---
title: "Kcontrol swamp buggy"
date: 2005-04-10
forum: Desktop Environments
---

### Post by Cougaram on 2005-04-10
Seems every time I use Kcontrol, something is always wrong with it. Settings (time in particular) won't save (YES! I DID AS ROOT TOO!). Some things just won't work at all. Setting file associations, for example, are a lost cause ... and on and on and on. Buggier than a Florida swamp marsh in summer. Are these KDE 3.4 problems? Or K/Ubuntu's problems? About the only thing that works flawlessly for me are (LOL!) the nvidia drivers and games. Things look pretty dark at the moment but maybe the next updates will bring some light? I Hope so.

---

### Post by user-jon on 2005-04-10
I can't offer any advice on this..  but I'd just like to confirm the problem.

I tried to use Kcontrol (as root) to configure static IP address, DNS, default gateway etc,,
The static IP and netmask were accepted and saved correctly in /etc/network/interfaces.
However, every time I tried to set the broadcast address or default gateway,
the settings did not get saved (just vanished in a poof of magic dragon dust!)

Kould some of you klever Kubuntu folks kast your eye over this konundrum.. please!!

---

### Post by Jonathan2007 on 2005-04-10
[QUOTE=user-jon]I can't offer any advice on this..  but I'd just like to confirm the problem.

I tried to use Kcontrol (as root) to configure static IP address, DNS, default gateway etc,,
The static IP and netmask were accepted and saved correctly in /etc/network/interfaces.
However, every time I tried to set the broadcast address or default gateway,
the settings did not get saved (just vanished in a poof of magic dragon dust!)

Kould some of you klever Kubuntu folks kast your eye over this konundrum.. please!![/QUOTE]
Have a look at my post in [this](http://ubuntuforums.org/showthread.php?t=25249) thread. I don't know if that really solves the problem but it talks about some of the problems I had. Maybe it will help you.

---

### Post by Coral Sea on 2005-04-28
Manually edit the config file like so:

   sudo vim /etc/network/interfaces

and add a line like:

   gateway 192.168.0.1

---

