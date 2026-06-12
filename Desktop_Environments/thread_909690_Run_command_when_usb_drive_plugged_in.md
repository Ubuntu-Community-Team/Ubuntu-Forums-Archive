---
title: "Run command when usb drive plugged in?"
date: 2008-09-03
forum: Desktop Environments
---

### Post by solexious on 2008-09-03
Hello,

I want to run a command (a python script) when a particular usb drive is plugged in.

How can I do it?

Thank you for any help you can give.

Sol

---

### Post by aprominax on 2008-10-14
anybody knows howto do this already, im looking for the same, but just to run an terminal command ..

thnx, aprominax

---

### Post by shortylonglegs on 2010-12-24
I know this is an old post, but I came across it looking for the same thing, so I'll post my answer for anyone else.

The first step is to find the number that identifies your usb device.  I'm not sure what it represents but its consistent across sessions, machines, and reformatting so its somewhere in the drives hardware.
```

$ lsusb
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 1b1c:0a10  
Bus 001 Device 002: ID 0bc2:3101 Seagate RSS LLC

```

My device was the one that didn't have a name, so my ID was "1b1c:0a10"  The easiest way determine which one is which is to either match the name with the manufacterer of the drive or just by running lsusb both with your drive in and out, and look at the difference.

After I had my ID, I made a simple script:
```

#/bin/bash
while :
do
	sleep 5
	if lsusb | grep YOURID
		then
                        WHAT YOU WANT TO HAPPEN
			continue
	fi
done

```

I use mine on a server that doesn't have to do much, so using a while loop with a sleep works well enough for me. If you wanted to have something happen when the device was not attached, just move the 'what you want to happen' between the 'fi' and 'done' but keep the continue in the if statement:
```

#/bin/bash
while :
do
	sleep 5
	if lsusb | grep YOURID
		then
			continue
	fi
	WHAT YOU WANT TO HAPPEN
done

```

---

