---
title: "Lockups after/during GDM loading"
date: 2006-01-05
forum: Desktop Environments
---

### Post by ScatterBrain on 2006-01-05
I've recently (inside the last two weeks) reinstalled Breezy on my Inspiron 6000d.  I used one of the pressed CDs I recieved from shipit (Canonical) to do so.  In the past I've always used an ISO and my own CD - not that it matters.

Since the reinstallation, this machine locks up better than 95% of the time it boots.  The lock up occurs just as, or just after, GDM loads and I'm able to enter my username in the login line.  Sometimes I get my username entered, sometimes I don't.

This lockup is a hard lock - no activity, no response from mouse, keyboard or network.  All I can do is hold the power switch, wait for the laptop to die and then restart it, hoping the next time it comes up fine.  A good example was yesterday, I had to boot the machine 6 different times before I was actually able to use it.

Once I do get it up and running, it runs fine until I shut it down.

I'm using the stock kernel (2.6.12-10-386) and the ATI drivers from the repositories.  I do use an external USB mouse most of the time, and it does appear (at least this morning and last night) that if I leave the mouse unplugged during boot, that the machine gets up and running on the first go.  But I'm finding it hard to believe that this is the root of my problems.  Previous installations never caused the problem.

I can supply configuration files as needed...I'd supply a snippet from the logs but the lock up prevents anything from getting registered to the logs.

Anyone have a clue?

---

### Post by tpotato on 2006-01-05
Thanks for posting that. I have what sounds like the same problem. 
I installed breezy from the dowload install cd to a Compaq 6220. I was just getting into it when it has started doing that. I had rebooted it many times and logged in and used it before it developed the problem. I can login fine but then I get the gray screen of death. Nothing but a mouse cursor, if I have
the external mouse plugged in, which cursor can move around
but I've not found anything else that can be done except turn off the 
machine. 
Then it occurred that after I reset it once that I got a kernal panic.
Something like:
"..MP-BIOS bug 8254 timer not connected to IO-APIC. kernal panic not syncing IO-APIC + timer doesn't work!" 
It went on to suggest apic=debug or noapic. 
I tried the noapic thing by editting the boot entry (hit e) and lo and behold
I did get stuff on the screen after login. I don't know if this really "fixed"
it but it seems like progress.

---

### Post by ScatterBrain on 2006-01-06
Just a word of confirmation...

It appears as though the lock ups are tied to whether or not I have the USB mouse plugged in during GDM startup.  If I leave the mouse unplugged until after Gnome starts, then I'm fine.  This worked all day yesterday and last night.

Another (possibly related) bit of information.  Several times during the day yesterday - usually after several minutes of inactivity - the USB mouse would be non-responsive.  This non-responsiveness would include the power to the mouse being off...ie, the light for the optical sensor would be out, not dimmed, but out like it was unplugged.  I would unplug the mouse, plug it back in and it would work fine for several hours.  I would step away from my desk and when I came back the mouse would be dead again.

It appears as though the system is aware of when I unplug the device, as I found this snippet in the syslog:

```

Jan  5 16:49:00 enterprise kernel: [4327067.742000] usb 3-2: USB disconnect, address 5
Jan  5 16:49:00 enterprise hal.hotplug[27821]: DEVPATH is not set (subsystem input)
Jan  5 16:49:01 enterprise kernel: [4327069.425000] usb 3-2: new low speed USB device using uhci_hcd and address 7
Jan  5 16:49:02 enterprise kernel: [4327069.588000] input: USB HID v1.10 Mouse [Microsoft Microsoft 5-Button Mouse with IntelliEye(TM)] on usb-0000:00:1d.2-2
Jan  5 16:49:02 enterprise hal.hotplug[27884]: DEVPATH is not set (subsystem input)
Jan  5 16:49:02 enterprise usb.agent[27899]:      usbhid: already loaded Jan  5 16:49:02 enterprise input.agent[27950]:      evdev: already loaded
Jan  5 16:49:02 enterprise input.agent[27885]:      tsdev: already loaded Jan  5 16:49:02 enterprise input.agent[27885]:      mousedev: already loaded
Jan  5 16:49:02 enterprise input.agent[27885]:      evdev: already loaded Jan  5 16:49:02 enterprise input.agent[27960]:      evdev: already loaded
Jan  5 16:49:02 enterprise input.agent[27966]:      evdev: already loaded

```

And the same thing several minutes later when it happened again:

```

Jan  5 16:56:47 enterprise kernel: [4327535.492000] usb 3-2: USB disconnect, address 7 Jan  5 16:56:47 enterprise hal.hotplug[28418]: DEVPATH is not set (subsystem input)
Jan  5 16:56:49 enterprise kernel: [4327536.925000] usb 3-2: new low speed USB device using uhci_hcd and address 8
Jan  5 16:56:49 enterprise kernel: [4327537.012000] usb 3-2: device descriptor read/64, error -71
Jan  5 16:56:49 enterprise kernel: [4327537.275000] input: USB HID v1.10 Mouse [Microsoft Microsoft 5-Button Mouse with IntelliEye(TM)] on usb-0000:00:1d.2-2
Jan  5 16:56:49 enterprise hal.hotplug[28478]: DEVPATH is not set (subsystem input)
Jan  5 16:56:49 enterprise input.agent[28479]:      tsdev: already loaded
Jan  5 16:56:49 enterprise usb.agent[28495]:      usbhid: already loaded
Jan  5 16:56:49 enterprise input.agent[28564]:      evdev: already loaded
Jan  5 16:56:49 enterprise input.agent[28554]:      evdev: already loaded
Jan  5 16:56:50 enterprise input.agent[28571]:      evdev: already loaded
Jan  5 16:56:50 enterprise input.agent[28479]:      mousedev: already loaded
Jan  5 16:56:50 enterprise input.agent[28479]:      evdev: already loaded

```

I'm hoping this is helping with the diagnosis....

**tpotato**: Thanks for responding!  I'll try the "noapic" thing today and see if that has any affect.

---

### Post by ScatterBrain on 2006-01-06
The "noapic" boot option did not help matters.  If the USB mouse is plugged up, then the machine will lockup almost everytime I start the machine.

The "non-reesponsive" mouse issue cotinues today.

Maybe I just have a bad mouse??

---

### Post by ScatterBrain on 2006-01-12
It's not the mouse - I tried a different one and the same thing happened.

Another intresting bit of info - I found that I could work around this issue by simply plugging in the USB mouse *after* Gnome got started.  That has been working for several days.

Well, this morning, I came in powered up the machine - no USB mouse - and it took 6 times to boot before I caould get in.

I remember there was an upgrade that I applied yesterday, but that had to do with textinfo and I wouldn't think that it would hinder me in any way.  Anyway ti looks like I'm going from bad to worse...

---

