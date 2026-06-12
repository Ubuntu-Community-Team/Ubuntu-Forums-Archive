---
title: "problem with setting up xrdp on lubuntu 13.04"
date: 2013-06-28
forum: Desktop Environments
---

### Post by necktwi on 2013-06-28
[COLOR=#333333][FONT=UbuntuRegular]After fresh install of Lubuntu 13.04 i did[/FONT][/COLOR]

sudo apt-get install tightvncserver
sudo apt-get install xrdp
[COLOR=#333333][FONT=UbuntuRegular]
now when i login with remoted desktop clien from window or ubuntu, i get black and white mesh screen. i followed various help forums like [http://sourceforge.net/p/xrdp/discussion/389417/thread/64949bc2#](http://sourceforge.net/p/xrdp/discussion/389417/thread/64949bc2#)but nothing worked![/FONT][/COLOR]

---

### Post by claracc on 2013-06-28
Perhaps this link: [http://askubuntu.com/questions/133343/how-do-i-set-up-xrdp-session-that-reuses-an-existing-session](http://askubuntu.com/questions/133343/how-do-i-set-up-xrdp-session-that-reuses-an-existing-session) can help you

---

### Post by Toz on 2013-06-28
There is no need to recompile xrdp. 

To get it to work, simply install xrdp, it will bring in vnc4server (instead of tightvncserver), not sure if that is your problem. If you have a firewall running, make sure you allow port 3389 through. When connecting, make sure to choose the sesman-Xvnc option.

Note: there is a log file located at /var/log/xrdp-sesman.log that might be helpful.

---

### Post by necktwi on 2013-06-28
Thank you @claracc! this working great! but nm-applet says network-manager not working. any solution for nm-applet to work properly?

---

### Post by Toz on 2013-06-28
> **necktwi said:**
> Thank you! this working great! but nm-applet says network-manager not working. any solution for nm-applet to work properly?

You didn't specify whose nm-applet isn't working  - the local or the remote computer. If the nm-applet isn't working on the remote computer _but_ works if you log in locally to the remote computer, then it might be an issue with xrdp.

Otherwise, its probably best to create a new thread since the nm-applet problem isn't related to this one.

---

### Post by necktwi on 2013-07-02
> [COLOR=#000000][INDENT]There is no need to recompile xrdp. 

To get it to work, simply install xrdp, it will bring in vnc4server (instead of tightvncserver), not sure if that is your problem. If you have a firewall running, make sure you allow port 3389 through. When connecting, make sure to choose the sesman-Xvnc option.

Note: there is a log file located at /var/log/xrdp-sesman.log that might be helpful.[/INDENT]
[/COLOR]
that is exactly what i've done. It didn't work.

---

### Post by Toz on 2013-07-02
What does the log file say?

---

### Post by bflance on 2013-08-30
i have managed to make xrdp work on my fleet of ubuntu 12.04 machines.. however what saddens me is that XRDP doesnt work at all on any redhat machine..

---

