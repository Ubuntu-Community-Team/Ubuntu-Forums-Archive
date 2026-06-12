---
title: "how to uninstall previous driver"
date: 2008-12-30
forum: General Help
---

### Post by icejack_outlaw on 2008-12-30
hi all guys.... today i just install ubuntu ibex in my laptop... the installation is success.. but when i install nvidia third party driver that pop up at desktop and reboot my laptop......the laptop now not displaying anything(blank).... when i log to terminal(ctrl+alt+f1) and type starx..... error that appear is "Fatal server error: server is already active for display 0, If this server is no longer running, remove /tmp/.XO-lock and start again."
and i dont know to fix it.

Please help me to fix it guys.... coz im newbee in ubuntu ibex, for advance, thanks for ur helps

---

### Post by sdibias on 2008-12-30
try running the following

```

sudo apt-get install --reinstall xserver-xorg-core

```

Not sure if this will fix or not but it's worth a shot

---

### Post by icejack_outlaw on 2008-12-30
> **sdibias said:**
> try running the following

```

sudo apt-get install --reinstall xserver-xorg-core

```

Not sure if this will fix or not but it's worth a shot



i just follow ur guide... and reboot.. but same probs happen... no display for log in..... is there like restore point in windows that can use the good condition status.... owh i dont want to reinstall back...oowhh no...somebody please help me

---

### Post by sdibias on 2008-12-30
Ok try running 

```

sudo rm /tmp/.XO-lock

```

and then run

```

startx

```

Anything?

---

### Post by icejack_outlaw on 2008-12-30
> **sdibias said:**
> Ok try running 

```

sudo rm /tmp/.XO-lock

```

and then run

```

startx

```

Anything?

nothing happen... still blank

---

### Post by sdibias on 2008-12-30
Ok we will figure this out... Let's see if xserver is running

```

ps aux | grep `cat /tmp/.X0-lock`

```

If it is there kill it first before starting another

```

kill PID#

```

---

### Post by umechanism on 2008-12-30
I think you will have to boot into safe mode to execute the above commands.  You'll see safe mode as one of the options when you reboot your computer.

Good luck.

---

### Post by sdibias on 2008-12-31
The firs number after root is the PID you need to kill mine looks like this

```

root      4926  8.0  3.5  70880 73900 tty7     Ss+  20:30   2:26 /usr/X11R6/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7

```

If you run

```

ps -A

```

you will be able to match that PID to verify

```

4926 tty7     00:02:19 Xorg

```

then I could run the following 

```

kill 4926

```

now run startx again, anything?

---

### Post by icejack_outlaw on 2008-12-31
ah haaa......i just follow what umechanism said.... i boot in recovery mood... the i select fix X SERVER.... and reboot..... taaadaaa... now i can continue to play with my new ubuntu ibex..... thanks to sdibias and umechanism.... u are the best.... thanks alot guy.... i love u muaaahh

---

