---
title: "simulate keypresses with lirc"
date: 2009-03-06
forum: General Help
---

### Post by notatoad on 2009-03-06
i'd like to get my mceusb remote working the same way the media keys on my keyboard do, integrated into the whole system rather than one application.  aka XF86AudioUp increases the system volume, XF86AudioNext skips to the next track in whatever multimedia app is running, etc.

is this possible?

i have the number keys set in .lircrc with 
```
prog = irxevent
remote = *
button = One
config = Key 1 CurrentWindow
```
but setting ```
prog = irxevent
remote = *
button = Play
config = Key XF86AudioPlay CurrentWindow
```
doesn't do anything.

the "grab keystroke" tool in compizconfig-settings-manager tells me i have pressed XF86AudioPlay when i press the play button on my keyboard, but xev spits out this
```

FocusOut event, serial 35, synthetic NO, window 0x3e00001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 35, synthetic NO, window 0x3e00001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 35, synthetic NO, window 0x0,
    keys:  2   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

```

---

### Post by notatoad on 2009-03-06
sort of figured it out.  i didn't figure out how to simulate xf86 keypresses, but i did find shell scripts in /etc/acpi to simulate keypresses, so all is good.  lircrc attached for anybody who wants a (almost) fully functional mceusb remote.  you need to install lirc-x to use it and run "sudo irexec" and "irxevent" on startup.

---

### Post by buntuyu on 2011-04-07
for me, the following ALMOST works:


> begin

  remote = *
  prog = irexec
  button = VolUp
  repeat = 2
  config = /etc/acpi/voldownbtn.sh

end



When I press the VolUp button on my remote, ubuntu volume indicator does not appear right away, nor does the volume change. However, the irexec command(s) start(s) executing as soon as I press any key on the standard keyboard. Pressing the keyboard key seems to remove the holdup somehow. Also, the gnome volume level indicator appears also at that point, too.  All the irexec requests I have made with the remote, up to that point, execute all at once. (The volume settles to the level modified by the cumulative button presses)

Any ideas?

FWIW:  I need superuser privileges to run "/etc/acpi/voldownbtn.sh"

So, I launch "irexec --daemon" as superuser.

---

### Post by Gendron5000 on 2011-10-04
having the same issue.  did you solve the issue?

does anyone else have an idea?

---

### Post by SpiritRC on 2013-04-27
Apparently, those ACPI scripts just put the event in the queue,
but don't notify the kernel of the event.

To send a notification, just find the /dev/input/event* device
that corresponds to your keyboard, and send a new line into it:

sudo sh -c 'echo > /dev/input/event2'

right after executing the acpi key simulation script.

That works for me.

---

### Post by wildmanne39 on 2013-04-27
Thread closed. Please do not post in old threads.

---

