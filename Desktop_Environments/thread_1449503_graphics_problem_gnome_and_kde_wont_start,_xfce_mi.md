---
title: "graphics problem: gnome and kde wont start, xfce missing panels"
date: 2010-04-07
forum: Desktop Environments
---

### Post by samuelkarush on 2010-04-07
Im having some display issues.
 i use karmic 9.10 and run mythtv.  started with ubuntu desktop. First sign of problem was gedit wouldn't start unless root, fixed by a reinstall of gedit. Then on next reboot I can't get past login screen, just hangs. So I used shell to check some logfiles and nothing jumped out at me. Then uninstall/reinstall ubuntu-desktop didn't help, and then ran into a documented bug trying to apt-get install gnome.
 Sooo, then i installed xubuntu-desktop and was happy for about a day. then mythfrontend wouldnt start, and after a reboot, the panels were gone on the xfce desktop. I can run things from a shell from here, for now.
so, then i tried an install of kubuntu-desktop. This didn't change anything. The only desktop that will get past the login screen is xfce, which im using now to open firefox from a terminal.
 Id like to not do a reinstall, spent a lot of time getting myth to run good. I'm using a nvidia graphics card and driver too. I didnt see anything odd in xorg.log, so dont think thats it. pretty stumped right now. a link to some info on similar problem would be great if someone has seen something.

 xubuntu is working good for me besides the panel thing, trying to add a panel using gui doesnt work. using xfce-panel works though.

---

### Post by micio on 2010-04-08
could you please so kind to post the xorg.conf and .xsession files? 
And please try to issue this line

```
cat /var/log/Xorg.0.log | grep EE
```

and see if some error is reported in log file.

thanks!

Micio

---

