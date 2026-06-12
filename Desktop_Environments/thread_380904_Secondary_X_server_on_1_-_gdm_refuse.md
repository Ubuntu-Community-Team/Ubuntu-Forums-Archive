---
title: "Secondary X server on :1 - gdm refuse"
date: 2007-03-10
forum: Desktop Environments
---

### Post by asipi on 2007-03-10
Hi All,

I am a Kubuntu Edgy user however I decided to use gnome desktop for a while, so I installed ubuntu-desktop and gdm. I often play Enemy Territory and because of the game's fullscreen handling I use it on a separate X that mean on :1.0

This is the script I wrote to start et:
```
ati@atihome:~$ cat /usr/local/bin/x.et
## Start another X server, pipe anything not returned by et to /dev/null (otherwise
## something presses enter until we kill the terminal we executed it from
xinit /usr/local/games/enemy-territory/et $* -- :1 > $HOME/x.et.log 
```

quite simple, isn't it? :)

BUT:
when I switched to gdm, this script has problems... I always receive this error message:
```
AUDIT: Sat Mar 10 14:10:38 2007: 7715 X: client 1 rejected from local host
```
so I could not start it. I tried ***sudo xhost +localhost*** but did not help.

I saw that gdm use a different Xsession script than kdm, I guess this will be the problem, but what should I change/correct/set in it to get this script working?

Ah, ye Xwraperr.config in /etc/X11 has the line ***allowed_users=anybody*** so not that is the problem.

Thanks in advance.

---

### Post by 1/0 on 2007-12-10
Guess you've already solved it but if not (or if others have the same trouble), try to remove .Xauthority

More info:
[http://ubuntuforums.org/showthread.php?t=51486](http://ubuntuforums.org/showthread.php?t=51486)

---

### Post by asipi on 2007-12-10
yep, thank you.
I used another solution, added magic-cookie for display :1 with xauth

but could you explain why kdm do not need this?
I am confused about it :(

---

### Post by 1/0 on 2007-12-13
As far as I know kdm and gdm set their own permissions as soon as you enter run level 5 (instead of run level 3). Gdm in comparison to kdm supports the X Display Manager Protocol (XDMCP) for managing remote displays. The way for gdm to remember the different users choices is by cookies and gdm only supports the MIT-MAGIC-COOKIE-1 authentication system. As far as I understand its an old system with many security problems etc. Kdm probably uses another method.

---

