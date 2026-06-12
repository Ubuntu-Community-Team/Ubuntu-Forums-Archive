---
title: "Cannot Reboot/Shutdown/Logoff from inside KDE"
date: 2009-10-23
forum: Desktop Environments
---

### Post by klemes on 2009-10-23
Since I upgraded to Kubuntu Karmic 9.10 I cannot use any of the Shutdown options in KDE menu or in KShutdown.Clicking on Reboot Shutdown or Logout in the KDE menu simply brings up no options or do anything at all really.It's like I never clicked on the corresponding button at all.
On Kshutdown I get a similar story so the only option is to shutdown from the Konsole by giving 'shutdowwn -h now' or the 'shutdown -r now' commands which I don't think it's a very elegant way of terminating the KDE or the computer session.
Please give me some light in this situation .Any hints will be greatly appreciated!
                                   
                                                              klemes.

---

### Post by klemes on 2009-10-23
[SOLVED!!!]It seems it was some misconfiguration in my KDE user files because when as a last resort I backuped my old .kde directory and started off with a clean sheet everything worked once again.So I think it was all due to some incompatibility when upgrading to Ubuntu 9.10RC between the two versions.

---

### Post by asd090 on 2009-11-06
I have the same problem.
klemes, can you explain how did solve it?

---

### Post by asd090 on 2009-11-06
I have the same problem.
klemes, please, can you explain how did you solve it?

---

### Post by Dansid on 2009-11-08
Puhlease Explain!

---

### Post by depeha on 2009-11-11
Almost same problem here! I can't shutdown or reboot (logout is possible) using any GUI app (lancelot, k(g)shutdown, Kickoff, shutdown/logout plasmoid...), but only inside KDE... everything is OK with GNOME. Shutdown or reboot is possible from KDE, but only using konsole (sudo halt/reboot).
There are no shutdown/reboot options in Kickoff, Lancelot still shows it, but when I press some, I get just "logout" option (image attached).
I've tried remove ".kde" in my home folder, turn off "logout sound", create new user, but nothing worked... :icon_frown:

---

### Post by klemes on 2009-11-11
> **Dansid said:**
> Puhlease Explain!

Dansid I will explain what I did but I don't know if it will work for you as well.
First of all backup your ~/.kde directory:
Note that you will loose all your personal settings in KDE.

```
mv ~/.kde ~/.kde.old
```

then you must reboot by giving:

```
 sudo reboot
```

If it fails you can restore your individual settings that you have previously backed-up by giving:

```
mv ~/.kde.old ~/.kde
```

in the console,and then reboot again.
Good luck!!!!!
Hope it works for you!!!!!!!!

---

### Post by depeha on 2009-11-12
This is impossible!
I have reinstalled ubuntu 2 times in last 24 hours... and? I still cant shutdown my PC with button!
First time I just formated "/" and install ubuntu (I have home folder on another disk part).
Second time I formated WHOLE disk and... Those buttons still missing! wtf?!

---

### Post by neillmitchell on 2009-12-10
Hi.

I'm still having this problem. Tried deleting .kde but it didn't fix it.

Anyone got any ideas about this one? It's driving me absolutely nuts. This was working until about 2 weeks ago. Some update must've broken something.

Thanks.

---

