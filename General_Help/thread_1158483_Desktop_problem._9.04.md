---
title: "Desktop problem. 9.04"
date: 2009-05-13
forum: General Help
---

### Post by johnny9794 on 2009-05-13
not sure where the problem sits.

Am running 9.04 on a dell dimension pentium 3 512 mb mem with a mx440 64mb video card.

Install of OS went smoothly, installed updates, enabled repositories and updated, installed envyNG, selected video driver 96.43.10 oubunto1 to be installed, that went smoothly,
I am stuck on resolution 1024x768, I am trying to succeed with 1280x1024. 
in the terminal I typed in 
sudo nvidia-settings  

so in the nvidia xserver settings, x server display configuration I select 1280x1024 n hit apply, 1280x1024 is my new res, but then when i click on save to x config file i get an 

error: unable to remove old x config backup file /etc/X11/xorg.conf.backup

but now when I reboot I am back to 1024x768 Plus all the borders of any window I open are completely gone "decorations".

I've tried 
alt + F2 metacity --replace 
alt + F2 metacity &

alt + F2 metacity --replace is a temp fix till i reboot again and the same thing, borders are gone again.

alt + F2 metacity & 
then reboot 
does nothing for me either.

any suggestions guys?

---

### Post by WIGGMPk on 2009-05-13
For a workaround you could add that to your startup applications.


Just create a new item to start at login and put that in there:

```
metacity --replace
```

---

