---
title: "How can I remove beryl autostart?"
date: 2007-02-18
forum: Desktop Environments
---

### Post by perrantrevan on 2007-02-18
Please help me! I'm stuck using windows after upgrading beryl today.

I upgraded to kernel 2.6.17-11-generic, along with various other upgrades such as beryl (using adept-notifier)

Had to use envy to upgrade nvidia-glx driver

Now I can log on but as beryl is on autostart. It loads up and the screen goes white.


Tried removing autostart entry in terminal: -

sudo rm ~/.kde/Autostart/beryl-manager


This appeared to work but when I logged on I got the white screen again as beryl continued to autostart.

Can anyone offer some help to stop beryl autostarting?

Is there a way to fix this beryl problem?

I've only been using linux (Kubuntu Dapper and Edgy) for about 6 months. Are updates always so risky? Until today, I had my system pretty much spot on- with WPA, kxdocker and beryl working ok.

Many thanks i advance.

Pepe

---

### Post by anguste on 2007-02-18
that sounds strange,

is it now possible for you to load the older version of kernel (2.6.17-10 or sth. like that) for a while and see what would happen?

---

### Post by perrantrevan on 2007-02-18
Thanks, I tried that but kdm would'nt load so I got dumped at the command line login. 

Since posting I've also tried using the failsafe login and removing beryl using aptitude remove. However, it seemed to want to hold back the packages, removing none. On trying a kde login beryl started again resulting in the white screen.

All my data is on a different partition but I really can't stomach doing a reinstall.

pepe

---

