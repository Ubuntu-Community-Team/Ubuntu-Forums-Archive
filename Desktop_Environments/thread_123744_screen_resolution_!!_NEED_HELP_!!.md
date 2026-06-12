---
title: "screen resolution !! NEED HELP !!"
date: 2006-01-30
forum: Desktop Environments
---

### Post by cowzzwoc on 2006-01-30
i just got ubuntu (because my windows crashed) and i was fooling around with it yesterday. On accedent i set my screen resolution to something that my laptop's moniter does not support. Whenever i log into my account even using the default settings the screen goes black and i can't see anything. Is there a way for me to changemy resolution back so that i can actually use ubuntu? ALL SUGGESTIONS ARE APPRECIATED

---

### Post by RAOF on 2006-01-30
[QUOTE=cowzzwoc]i just got ubuntu (because my windows crashed) and i was fooling around with it yesterday. On accedent i set my screen resolution to something that my laptop's moniter does not support. Whenever i log into my account even using the default settings the screen goes black and i can't see anything. Is there a way for me to changemy resolution back so that i can actually use ubuntu? ALL SUGGESTIONS ARE APPRECIATED[/QUOTE]
Once you're at the login screen, press Ctrl-Alt-F1.  This should bring you to a text-mode login screen.  Login, and run "sudo dpkg-reconfigure -p high xserver-xorg".  It'll ask a lot of questions about your graphics - the defaults should be fine.  When it asks what resolutions you'd like to use, select only the ones you know work.  Then run "sudo /etc/init.d/gdm restart", and try logging in again.

---

### Post by cowzzwoc on 2006-01-30
thanks alot i knew there was i way to fix it i just didnt know how.

---

### Post by iverylm on 2006-01-30
Had problems with high resolution on my desktop.  I was at 1280...did all the configuring per the post here.  The one item in the reconfigure that I did not do...was on previous attempts to change resolution I highlited "Advanced" which ias a no-no for me.  Last time I...highlited the one above "Advanced"...upon reboot my resolution was 1024.

Attempts to change resolution from the desktop met with no screen at all.  Had to cp the backup in order to see main desktop.

Hope this helps

---

### Post by cowzzwoc on 2006-01-31
idk it hasent been working for my because when i type in my command nothing happens

---

### Post by RAOF on 2006-01-31
[QUOTE=cowzzwoc]idk it hasent been working for my because when i type in my command nothing happens[/QUOTE]
What?  You mean the
```
sudo dpkg-reconfigure xserver-xorg
```command?

---

