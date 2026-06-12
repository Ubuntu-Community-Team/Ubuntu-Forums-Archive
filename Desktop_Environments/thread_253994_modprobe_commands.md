---
title: "modprobe commands"
date: 2006-09-09
forum: Desktop Environments
---

### Post by JurB on 2006-09-09
To get sound working in tvtime i have to execute the following commands in a terminal each time i boot:
```
sudo modprobe -r bt878 bttv
```
```
sudo modprobe snd_bt87x
```
```
sudo modprobe bt878
```
I would like the modules to be unloaded/loaded automatically at startup.
I know that i can add the snd_bt87x and bt878 to /etc/modules, but i can't seem to figure out how i can unload bt878 and bttv first.
Tried to add them to /etc/modprobe.d/blacklist but that didn't work.
Any ideas?

Tnx

---

### Post by JurB on 2006-09-29
Humpy Bumpy.

---

### Post by skymt on 2006-09-29
Just put the commands you need to run in "/etc/rc.local". It runs at the end of the boot process.

---

### Post by Hallavej on 2006-09-29
Not sure if it is the "correct" way but you could use a cronjob:
```
export EDITOR=gedit
sudo crontab -e
```
and then put in the command
```
@reboot modprobe -r bt878 bttv >/dev/null 2>&1
```
Save and exit gedit.

obvioulsly @reboot means that the command is done every time the computer is started. >/dev/null 2>&1 means that any output of that command is not written anywhere.

---

### Post by Hallavej on 2006-09-29
oops. Skymt was faster (and his answer better I think)

---

### Post by fragos on 2006-09-29
> **skymt said:**
> Just put the commands you need to run in "/etc/rc.local". It runs at the end of the boot process.
Is sudo required within this script?

---

### Post by skymt on 2006-09-29
> **fragos said:**
> Is sudo required within this script?

No, it runs as root anyway.

---

### Post by JurB on 2006-10-14
> **skymt said:**
> Just put the commands you need to run in "/etc/rc.local". It runs at the end of the boot process.

Thank you, works great!:)

---

