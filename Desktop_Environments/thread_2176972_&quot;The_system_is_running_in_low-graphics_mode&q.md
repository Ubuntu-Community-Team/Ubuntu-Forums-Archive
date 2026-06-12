---
title: "&quot;The system is running in low-graphics mode&quot; only with GDM"
date: 2013-09-26
forum: Desktop Environments
---

### Post by javi-brainfull on 2013-09-26
I've been running Ubuntu 13.04 and just today updated to 13.10 (didn't make any difference though, the problem remains the same).

As long as I use LightDM everything works fine, but if I change to GDM it takes me straight to that xFailsafe session with the "The system is running in low-graphics mode" message.
I've tried:


[LIST]
[*]Reinstalling GDM
[*]Running the nvidia-xconfig
[*]Reinstalling the Nvidia proprietary driver (nvidia-current)
[*]Updating the Nvidia proprietary driver (nvdia-current-updates)
[*]Updating GDM with the Gnome Next and Staging PPAs (to GDM 3.10)
[/LIST]

No cigar, I still get that same message every single time.

The thing is I'm running Gnome Shell, and up until 3.8 I've been using LightDM without problems (used GDM for a while, but switched to LightDM when I began getting this error after some update).
Now with the upcoming Gnome Shell 3.10 we can apparently no longer use LightDM, so this becomes again an issue.


Any help will be much appreciated :)

Regards.

---

### Post by Yellow Pasque on 2013-09-26
Do the gdm login and get the /var/log/Xorg.0.log from it.

Post using [ code ][ /code ] tags or just pastebin it.

---

### Post by javi-brainfull on 2013-09-26
There's nothing new in Xorg.0.log, only these logs are updated when I start GDM:

Xorg.1.log: [http://pastebin.com/CZnVXTqN](http://pastebin.com/CZnVXTqN)
Xorg.failsafe.log: [http://pastebin.com/FdPhZCYt](http://pastebin.com/FdPhZCYt)

---

### Post by grahammechanical on 2013-09-27
This is apparently true, 

> [COLOR=#000000]Now with the upcoming Gnome Shell 3.10 we can apparently no longer use LightDM, so this becomes again an issue.[/COLOR]

according to this

[http://www.webupd8.org/2013/09/how-to-install-gnome-310-in-ubuntu-1310.html#more](http://www.webupd8.org/2013/09/how-to-install-gnome-310-in-ubuntu-1310.html#more)

> **LightDM doesn't work so if you plan on using these PPAs, make sure you switch to GDM prior to upgrading;**

I suspect it is a bit of open source ethnic cleansing. As you are using Nvidia drivers this can have nothing to do with xmir which is about to become default in Ubuntu 13.10. From an experiment I know that with open source drivers xmir will load with lightdm but not with gdm.  Both lightdm and gdm do more than manage the login screen. They manage the xserver. In the case of Ubuntu 13.10 lightdm will be managing both xmir and xserver. But gdm will not be modified, I do not think.

I had no problems running Ubuntu Gnome with lightdm or gdm. Only when I wanted to use xmir. And I did not complicated things by installing the PPAs.

I wonder if it will no longer be sensible to install Gnome 3 shell as an alternative desktop on Ubuntu Unity? Am I bored enough to test this out?

Regards.

---

### Post by javi-brainfull on 2013-10-02
Actually if you intend to install Gnome Shell 3.10 along with Unity, forget about it as of now.

Requiring GDM is a minor issue compared with the fact that GS 3.10 will break Unity with no other solution than doing a ppa-purge.

---

