---
title: "Messed up UI"
date: 2009-02-28
forum: Desktop Environments
---

### Post by t_ras on 2009-02-28
AMD64 athalon

I had installed on my comp kubutu 8.04 with both KDE4 and KDE3.5.something (yes,yes, I know it is a seen...)
I didnt get ditro update when 8.10 came out (even through it was marked to update to normal version).
So I changes the sources file to point to intrepid and then performed update/upgrade, it got stacked all the time through UI. I decided to do it through terminal. I left it upgrading all night and then when it finished in the morning I rebooted. I could see GDM login screen, but it wasn't responding to neither keyboard nor mouse. I switch to terminal (Ctrl+alt+F1 did work) after some tries I just removed KDE and GDM with autoremove and installed kubuntu-desktop - no use. I reboot and can see the login screen but still not responding.

Any Idea how to solve it? I just want KDE4.2 working...

---

### Post by t_ras on 2009-02-28
I also choosed to keep my configurations whenever pompted for that,

---

### Post by t_ras on 2009-02-28
bump

---

### Post by MarblePanther on 2009-02-28
You can try reconfiguring X.  It may or may not help you, but its worth a shot.

```
sudo dpkg-reconfigure xserver-xorg
```

you can also try

```
sudo apt-get install -f
``` to repair packages

---

### Post by t_ras on 2009-03-01
didn't help :( nor installing ubuntu-desktop.
How can I uninstall all related packages and resintall them?

---

### Post by Monsieur Gonzalez on 2009-03-01
What graphic card are you using? Some problems seem to be related with restricted drivers, such as Nvidia or Ati. 

Could you post the relevant (as in errors) parts of your /var/log/Xorg.0.log?

---

