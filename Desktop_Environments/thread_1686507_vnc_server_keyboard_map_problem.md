---
title: "vnc server keyboard map problem"
date: 2011-02-12
forum: Desktop Environments
---

### Post by plamen_f on 2011-02-12
Hi

If have strange issue with the following configuration:

1. Installed tightvncserver on Ubuntu desktop. My xstartup is:

> #!/bin/sh


xsetroot -solid grey
vncconfig -iconic &
export XKL_XMODMAP_DISABLE=1
#x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
gnome-session &
# xfce4-session & - FOR XFCE
#x-window-manager &





2. Tightvncviewer on windows XP:

when i switch keyboard to Bulgarian phonetic (1251) i can't see real Cyrillic :

[IMG]http://i860.photobucket.com/albums/ab162/plamenflo/Screenshot.png[/IMG]

Does anyone resolve this problem & how?

---

### Post by sammie12340 on 2011-02-13
hey, i had the same problem so they anwser is 
```
#!/bin/sh


xsetroot -solid grey
vncconfig -iconic &
export XKL_XMODMAP_DISABLE=1
#x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
gnome-session &
# xfce4-session & - FOR XFCE
x-window-manager &
```

Remove the # bevore x-window-mager &

---

### Post by plamen_f on 2011-02-14
HI!

10x for the answer!

Unfortunately this did not resolve my problem. I test it but - nope :(

This situation occurs only if i use vncclinet on Windows, If I use vnc client on Ubuntu - there is no problem...


Thank you again for your assistance!

---

