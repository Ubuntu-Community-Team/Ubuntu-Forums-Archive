---
title: "hibernate is ok, but suspend to ram not"
date: 2006-06-03
forum: Desktop Environments
---

### Post by ElMarcel on 2006-06-03
Hi everyone,
I am quite new to ACPI, so I didn't been able to make "suspend to ram" working.
I have a desktop pc (i.e. not a laptop) and a personally compiled kernel.
Everything is ok when I hibernate (it shutdown and then restarts properly), but I even don't know where to start to suspend (has anybody a standby button??? ](*,) )

I set in /etc/defaults/acpi-support
```
ACPI_SLEEP=true
```
that was commented out

In the ACPI howto is written:
> 
Make sure you have ACPI enabled in the BIOS and the kernel, and that you have the CONFIG_ACPI_SLEEP option set.
Then:
```
echo mem > /sys/power/state
```


The kernel is ok, but I don't know if the BIOS is ok too (the BIOS software is up-to-date, but my motherboard is quite old).
Anyway, on windows I can standby (but "windows standby" sets the "ACPI S1" state, while "suspend to ram" sets "ACPI S3").

When I try:
```
echo mem > /sys/power/state
```
I got
```
bash: /sys/power/state: Permission denied
```
even if I try as root

This is quite confusing... :-k 

So I found the /etc/acpi/sleep.sh script... but it terminates with no output...
the reason is:
```

# If gnome-power-manager or klaptopdaemon are running, let them handle policy
if [ x$1 != xforce ] && [ x$1 != xsleep ] && [ `CheckPolicy` = 0 ]; then
    exit;
fi

```

I also tried to remove this damned gnome-power-manager, but gnome-session depends on it... without it, I cannot login :-x 

The thing that I don't understand is: what does gnome-power-manager do to manage the sleep requests? How do I make this requests? (I do not have any "standby" button...)

At least, I tried to run:
```

/etc/acpi/sleep.sh force

```

If I run without being root I get this output:
```

/etc/acpi/suspend.d/55-down-interfaces.sh: line 3: pccardctl: command not found
ifdown: failed to open statefile /var/run/network/ifstate: Permission denied
SIOCSIFFLAGS: Permesso negato
ifdown: failed to open statefile /var/run/network/ifstate: Permission denied
SIOCSIFFLAGS: Permesso negato
Couldnt get a file descriptor referring to the console
Couldnt get a file descriptor referring to the console
open /dev/mem: Permission denied
Failed to initialise LRMI (Linux Real-Mode Interface).
/etc/acpi/suspend.d/80-video-vesa-state.sh: line 7: [: !=: unary operator expected
 * Shutting down ALSA...  * warning: 'alsactl store' failed with error message 'alsactl: save_state:1190: Cannot open /var/lib/alsa/asound.state for writing'...                  [fail]
open /dev/mem: Permission denied
Failed to initialise LRMI (Linux Real-Mode Interface).
/etc/acpi/suspend.d/90-framebuffer-stop.sh: line 11: /sys/class/graphics/fb0/state: Permesso negato
/etc/acpi/sleep.sh: line 39: /sys/power/state: Permesso negato
open /dev/mem: Permission denied
Failed to initialise LRMI (Linux Real-Mode Interface).
/etc/acpi/resume.d/17-video-restore.sh: line 5: /var/lib/acpi-support/vbestate: Nessun file o directory
/etc/acpi/resume.d/17-video-restore.sh: line 6: [: !=: unary operator expected
FATAL: Module dmfe not found.
/etc/acpi/resume.d/35-modules-load.sh: line 21: pccardctl: command not found
/etc/acpi/resume.d/50-framebuffer-enable.sh: line 6: /sys/class/graphics/fb0/state: Permesso negato
Spiacente, solamente il superuser può modificare il clock hardware.
open /dev/mem: Permission denied
Failed to initialise LRMI (Linux Real-Mode Interface).
ifup: failed to open statefile /var/run/network/ifstate: Permission denied
ifup: failed to open statefile /var/run/network/ifstate: Permission denied
chvt: Wrong number of args
 * Setting up ALSA...                                                    [ ok ]
FATAL: Module button not found.
FATAL: Module button not found.
FATAL: Module fan not found.
FATAL: Module thermal not found.
FATAL: Module fan not found.
FATAL: Module thermal not found.
grep: /proc/acpi/fan/*/state: Nessun file o directory
FATAL: Module acpi_sbs not found.
FATAL: Module ac not found.
FATAL: Module ac not found.
FATAL: Module battery not found.
FATAL: Module battery not found.
FATAL: Module acpi_sbs not found.

```

About all this stuff I know that I don't have "pccardctl" because I don't have the pcmciautils package (I don't have a laptop) and that all my ACPI modules are statically compiled in the kernel.

I will post the output of the same command runned as root later (it could blank my screen)

Thank you everybody for support!!!

---

### Post by ElMarcel on 2006-06-03
I'm back, I tried to run sleep.sh as root, and I got an instant reboot...
I also tried to run it with ACPI_SLEEP_MODE=standby instead of ACPI_SLEEP_MODE=mem. This cause ACPI to set the S1 state (simple standby).
My computer went in standby, but it cannot wake up.

Thats all!

---

### Post by mahalram on 2006-06-06
Sleep didnt work for me too - turned out to be a no brainer. Just had to set proper options (when lid closed etc.) in the gnome-power-manger

But in my case nothing was commented out in the config files. The second line in the sleep.sh script is to let the gnome-power-manager or klaptopd override policies.

---

### Post by mahalram on 2006-06-06
forgot to add that mine's Sony Vaio, TR3

I have been running Ubuntu since Warty - upgraded to hoary and now to dapper.
Everything works like a charm - except ofcourse the motioneye camera.

---

### Post by ElMarcel on 2006-06-20
The problem was in the BIOS... now everything is ok!!

---

### Post by desiboston on 2006-08-02
Did u try motioneye in Repos?

---

