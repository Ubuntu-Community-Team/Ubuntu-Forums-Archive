---
title: "Can't save screen brightness level (HP Compaq 6735s / HD Radeon 3200)"
date: 2013-07-10
forum: Desktop Environments
---

### Post by jrtarsoly on 2013-07-10
Hello & good day to all,

I've just installed and configured Ubuntu 12.04 LTS on a Hp Compaq 6735s machine, and all seems to be fine except for the brightness level which constantly is getting a reset upon each and every reboot of the machine.

I always set it to 100% while on AC (no battery - it's defected), and everytime I reboot the machine, my brightness level is automatically reset to 30% or 40% (can't remember exactly).

My question is why and how do I fix this ? It's getting really annoying.

Thank you,

JrT

---

### Post by Toz on 2013-07-10
Can you open a terminal window, run the following command and post back the results?
```
for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/max_brightness; done
```
This command will identify your backlight interfaces and there current values. With this information we can enter a command in /etc/rc.local to execute on every boot that will set the backlight to maximum.

---

### Post by jrtarsoly on 2013-07-11
Hello and thank you for the interest in my problem,

Yes, ran the command line and here is the result :

```

/sys/class/backlight/radeon_bl
247
255

```

Thank you,

JrT

---

### Post by jrtarsoly on 2013-07-11
Oh, on a sidenote I've ran the command after booting and setting up the brightness level to the maximum level possible. If it's not good, please let me know and I'll redo the command line with a proper reboot without altering the initial brightness setting level.

JrT

---

### Post by Toz on 2013-07-11
Lets add a command to /etc/rc.local that will set the brightness to full on boot.

1. Open the file for editing with root privledges:
```
gksu gedit /etc/rc.local
```

2. Above the *exit 0* command, add:
```
echo 255 > /sys/class/backlight/radeon_bl/brightness
```

3. Save the file.

4. Reboot to test.

---

### Post by jrtarsoly on 2013-07-11
Hello Toz,

I've followed your steps and after a reboot I can say that it worked.

Thank you so much,

JrT

---

