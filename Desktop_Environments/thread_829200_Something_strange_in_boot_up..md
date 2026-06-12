---
title: "Something strange in boot up."
date: 2008-06-14
forum: Desktop Environments
---

### Post by LeoSolaris on 2008-06-14
Ok, Yes, I am aware that I am in "Desktop Environments and the title says "boot up." No I am not crazy...   well ok maybe I am by that is beside the point.

Anyways, here is the issue.

I had a minor issue with the 64-bit update breaking compiz recently, and the fix was to reinstall the nvidia drivers. Not too hard, had a few issues, and had to restart more than a few times as well as break my display and use the real terminal, CLI.

Not normally a big deal, but I noticed something in the boot sequence (when viewed from CLI login) that puzzled me. A while back, I experimented with KDE4 and decided that I didn't like it yet, but that it looks promising, so I removed it. Well, it went looking for KDM in the KDE4 path before loading GDM.

I know it is minor, but I am rather annoyed that it is there. It there any way to tell the boot sequence to stop looking for a program that does not exist, then defaulting to the one that does?

Leo

---

### Post by Ub1476 on 2008-06-14
Remember to remove with --purge.

```
sudo apt-get remove --purge kde4
```

I'm not exactly which file to edit, but it's around in /etc, I think.

Try:

```
gksudo gedit /etc/rc.conf
gksudo gedit /etc/init.conf
```

On Archlinux, I edit to rc.conf to decide with deamons/modules to load on startup.

---

### Post by LeoSolaris on 2008-06-14
> **Ub1476 said:**
> Remember to remove with --purge.

```
sudo apt-get remove --purge kde4
```I'm not exactly which file to edit, but it's around in /etc, I think.

Try:

```
gksudo gedit /etc/rc.conf
gksudo gedit /etc/init.conf
```On Archlinux, I edit to rc.conf to decide with deamons/modules to load on startup.

I am learning about arch and have a base system installed on my laptop. 

Anyways, I tried the purge and it said nothing to remove. I looked for either of them in the /etc folder and nada, but I found a folder labeled KDE4 with a couple of folders in it, that ultimately came to a config file that basically said to ignore this config file.

I did delete that string of folders within folders.

I'll reprofile my boot up next start to see if it helps.

I have my boot time down to 32 - 33 seconds according to bootchart, and thats with VMware, ufw and more than a few non-standard boot up daemons starting.

Leo

---

### Post by p_quarles on 2008-06-14
Typically, you would find the startup script that is looking for this nonexistent program in 
```
/etc/rc2.d/
```
It is most likely named something such as "S24kdm" -- you can change the "S" to a "D" to prevent it from running that script on startup. Or, if you want kdm, but don't want it to look for the KDE 4 version, you could try editing the script by hand.

---

