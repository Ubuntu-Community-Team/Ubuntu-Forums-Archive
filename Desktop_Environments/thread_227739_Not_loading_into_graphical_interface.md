---
title: "Not loading into graphical interface"
date: 2006-08-02
forum: Desktop Environments
---

### Post by dolbinau on 2006-08-02
Hey,

I accidently tripped my power cable (not sure if this had anything to do with this). I restarted. Now it loads into a terminal/dos style thing 'Ubuntu 6.06 LTS dolbinau-linux tty1' ; I can log-in through the 'terminal' using my usual log-in credentials, however I want to get into the Ubuntu GUI. What must I do! Sorry for n00b question.

---

### Post by eXisor on 2006-08-02
```
sudo /etc/init.d/gdm start
```

will start the gui.

---

### Post by dolbinau on 2006-08-02
Hi,

This worked fine - I'm back in Ubuntu HOWEVER; how do I make this now default; instead of just booting to the Terminal each time?

---

### Post by eXisor on 2006-08-02
Hmmm... sounds like something got borked with your rc.local setup.
I suggest you do the following...

```
sudo aptitude update
sudo aptitude install sysv-rc-conf
sudo sysv-rc-conf
```

sysv-rc-conf lets you edit your startup config. Page down to where you see gdm on the left side, and make sure columns 2,3,4,5 have an asterisk in them on the gdm row. Use q to exit and reboot.

Tell us how this went.

---

