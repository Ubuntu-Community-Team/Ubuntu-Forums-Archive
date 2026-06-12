---
title: "GUI is gone!"
date: 2009-02-26
forum: General Help
---

### Post by skuttling on 2009-02-26
I'm a Ubuntu beginner, and I was attempting to speed the boot of my laptop. Now it only will boot to a command prompt and won't load the GUI. What can I do?

---

### Post by PurposeOfReason on 2009-02-26
A little more information please. What were you doing exactly? A howto you were following?

---

### Post by skuttling on 2009-02-27
using the command sudo /etc/init.d/gdm start I've been able to enter GNOME environment. But it's not permanent.

I was following [http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491)

the main issue i was having (before not being able to boot into gnome) is after the Ubuntu screen with the loading bar, it would pop back into a dos-esque mode and list off every process it was booting and then it would boot into gnome, instead of loading bar straight to gnome.

Now it boots, brings up splash loading screen, goes to does esque boot mode, then the command prompt to log in pops up, and i have to type in the command to enter gnome.

---

### Post by grndslm on 2009-02-27
- What were you doing before restart?  How long since you last restarted?

- Are there any relevant errors you can notice on boot?

- When you go into text mode... does typing this command help before starting gdm? (make sure to use correct user name)

sudo chown -R skuttling:skuttling /home/skuttling/
sudo /etc/init.d/gdm start

---

### Post by linux_tech on 2009-02-27
Try reinstalling desktop
```
sudo apt-get install ubuntu-desktop
```

---

### Post by skuttling on 2009-02-27
grndslm:

I restart my laptop every day usually twice a day (it's an aspire one with a 3 cell battery so it only lasts 3 hours at best). My last successful reboot was before I followed the forum to speed up my boot, which i'm supposing i somehow turned of Gnome.

As far as i can tell there are no relevant errors. It just appears to skip the part of booting that sends it too gnome.

sudo chown -R skuttling:skuttling /home/skuttling/ (with proper username) did nothing, or appeared to do nothing

sudo /etc/init.d/gdm start boots into gnome as expected and works fine, but isn't a permanent fix.

linux_tech:

I reinstalled the desktop, it says it's already downloaded at the latest version, and remains in text mode. Reboots back to text mode.

---

### Post by krishna1650 on 2009-02-27
try alt+clt+f7.

---

### Post by skuttling on 2009-02-27
> **krishna1650 said:**
> try alt+clt+f7.

when? It does nothing when i do it, all throughout the boot process.

---

### Post by krishna1650 on 2009-02-27
> **skuttling said:**
> when? It does nothing when i do it, all throughout the boot process.

log in time. when you get log-in prompt in text mode. i  know very little. this may not work at all.

---

### Post by internalkernel on 2009-02-27
Perhaps, you turned off GDM as an automatic service... I'm guessing this is the case since it works when you issue the /etc/init.d/gdm start and subsequently doesnt work after reboot. 

The startup order is in the /etc/rc*.d folders. It should look like this: 

```
##:/etc$ ls -al rc*.d/ |grep gdm
lrwxrwxrwx   1 root root    13 2009-02-18 20:04 K01gdm -> ../init.d/gdm
lrwxrwxrwx   1 root root    13 2009-02-18 20:04 K01gdm -> ../init.d/gdm
lrwxrwxrwx   1 root root    13 2009-02-18 20:04 S30gdm -> ../init.d/gdm
lrwxrwxrwx   1 root root    13 2009-02-18 20:04 S30gdm -> ../init.d/gdm
lrwxrwxrwx   1 root root    13 2009-02-18 20:04 S30gdm -> ../init.d/gdm
lrwxrwxrwx   1 root root    13 2009-02-18 20:04 S30gdm -> ../init.d/gdm
lrwxrwxrwx   1 root root    13 2009-02-18 20:04 K01gdm -> ../init.d/gdm

```

The files in rc2,3,4.d should be starting with an S. 

You could also sudo apt-get install sysvconfig, and use that tool to accomplish the same thing much quicker...

---

### Post by zika on 2009-02-27
two ways:

1. in Terminal:```
sudo update-rc.d -f gdm defaults
```reboot to try it out.

2. in Terminal:```
sudo apt-get install sysv-rc-conf
```
in Terminal:```
sudo sysv-rc-conf
```put X in line "gdm" in places numbered with 2, 3, 4, 5 (use Space), press Q and You're done. reboot to try it out.

---

### Post by skuttling on 2009-02-27
Got it working using sysvconfig.

Thanks folks.

Anyone know why it still lists off everything it is loading after the ubuntu splash screen and before loading gdm?

---

### Post by avrilrox on 2009-02-27
Init 5?

---

### Post by internalkernel on 2009-03-02
> **skuttling said:**
> 
Anyone know why it still lists off everything it is loading after the ubuntu splash screen and before loading gdm?

Do you see the splash screen initially? Loads for a bit, then switches to text just before loading GDM? 

I've seen that a couple times too, I just ignore it... You can install Start-up Manager, which will allow you to configure which splash screen is there and all that. I've found that to help with random issues like that...

---

