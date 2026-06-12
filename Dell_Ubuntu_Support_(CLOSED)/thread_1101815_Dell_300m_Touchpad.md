---
title: "Dell 300m Touchpad"
date: 2009-03-20
forum: Dell Ubuntu Support (CLOSED)
---

### Post by pmhauge on 2009-03-20
As I mentioned in a previous post, a friend gave me his Inspiron 300m Dell laptop for free. The touchpad was not working for him after a reinstall of Windows. Just for the hell of it, I bought a new touchpad off Ebay for $7. I installed it, and still the touchpad and buttons are not working. Something is messed up with the firmware, I'm guessing, as the touch pad did not work right under Windows or Ubuntu. The thing is, I haven't the foggiest idea of how to go about fixing this. Is this something I need to tackle from the BIOS? Please help!

---

### Post by pmhauge on 2009-03-20
I booted up to the BIOS to see if the touchpad was enabled/disabled, and everything seemed to be in order. The only option I had was to have the touchpad be disabled when a mouse or other device was plugged in, but I could not find anything specific to turning the touchpad on or off.

---

### Post by pmhauge on 2009-03-22
Any ideas? Any at all?

---

### Post by coffeeaddict22 on 2009-03-22
Hi.
Try  lshal |grep touchpad -A10 -B10 -n
By way of explanation, lshal is the hardware abstraction layer info that the display manager reads.  on its own you get over 1000 lines of info.  grep pattern matches; touchpad found mine, but it might be worth trying the brand name of the pad you put in.  -A and -B respectively add on lines in front of and behind what you've grepped; -n puts in line numbers in case you want to go back to the original output.

If it shows up in that, the Xorg knows about it and it's turned off in software.  If not, you might be looking for a missing bit of wiring...

---

### Post by pmhauge on 2009-03-22
That sounds like a great thing to try... but you'll have to excuse my n00bness and dumb it down just a bit. Is "lshal |grep touchpad -A10 -B10 -n" something I'm typing into terminal? Is this an app I'm downloading? Just a tad more help and I think I'll be on my way...

Thanks!

---

### Post by pmhauge on 2009-03-22
Ok, that was a dumb question. I pasted the command into terminal, but nothing happened. I just typed in only lshal and got the multiple lines of text... still unclear though as to how to proceed from here and get it working.

---

### Post by coffeeaddict22 on 2009-03-22
Sorry.  It was bedtime on this side of the world, and I desperately need beauty sleep- or so my kids tell me (My wife says it's not helping).

the line starting lshal is typed into the terminal.  lshal lists all the hardware that your GUI has to talk to I think- I don't know a huge amount about it but it's replaced the xorg.conf file you will have read about if you googled your problem.  Because it's so long, pipe the output through grep.  The reason you probably got no output is the pipe.  On my keyboard it's above the enter key; you're looking for a vertical line.  The hackers love it; it sends the results of the command/ file before the pipe to the command/ file after it.  I explained the grep stuff earlier so won't bore you again.

On my laptop the result looks like this:  :~$ lshal |grep touchpad -A15
  info.capabilities = {'input', 'input.mouse', 'input.touchpad'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port'  (string)
  info.product = 'AlpsPS/2 ALPS GlidePoint'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port_logicaldev_input_0'  (string)
  input.device = '/dev/input/event12'  (string)
  input.originating_device = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port'  (string)
  input.product = 'AlpsPS/2 ALPS GlidePoint'  (string)
  input.x11_driver = 'synaptics'  (string)
  linux.device_file = '/dev/input/event12'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/platform/i8042/serio1/input/input13/event12'  (string)

and you should see something along those lines.

  
Thinking about it, if you don't get any output it's highly likely the kernel doesn't know your touchpad is there seeing it's a late addition.  

Have a look at [https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad) if you haven't already as well. Typing" xinput list" (without the quote marks) into your terminal may be an easier way of finding out if the pad is recognised by your window manager.

---

### Post by coffeeaddict22 on 2009-03-22
And slightly off topic: if you're not sure about a terminal command, type man xxxx where xxxx is the command and it'll show you some info.  Sometimes it only vaguely resembles English, but usually you can figure out the gist of it if you have enough time.  Every command you can type into a terminal has a man (short for manual) page associated with it.  Unfortunately, the man pages are written by the people who wrote the code, and they occasionally assume a lot of arcane knowledge.

---

