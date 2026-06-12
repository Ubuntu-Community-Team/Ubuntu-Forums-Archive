---
title: "Set CPU scaling governor as early as possible (during bootup)"
date: 2009-03-31
forum: General Help
---

### Post by Andreas1 on 2009-03-31
here's what i used to do:
boot laptop > login to Gnome > Set powersave using the cpufreq-applet in the panel

Now i removed :twisted: my very annoying cpu fan and found that, as long as on powersave, the laptop does not overheat (crash, that is, in my very practical world :)).
The only problem is that when i *re*boot the computer when it's already hot, it overheats and crashes during bootup, because the cpu is not throttled at that moment. (It is no problem if i boot it from cold, since it takes some time to heat up after a cold night).

What i would like to do:
-Set powersave as default governor without having to select it in the panel applet
-Enable powersave governor as soon as possible during bootup or use some other means to throttle cpu at that point

---

### Post by binbash on 2009-03-31
you can write the command (cpufreq-selector -g powersave) to /etc/rc.local

But i don't know if it will fix your issue or not

---

### Post by 3rdalbum on 2009-03-31
Use your computer's BIOS to underclock the CPU to whatever the frequency is when it's on "powersave". You might need to turn off frequency scaling in the BIOS.

---

### Post by Andreas1 on 2009-04-01
> **binbash said:**
> you can write the command (cpufreq-selector -g powersave) to /etc/rc.local

But i don't know if it will fix your issue or not

It's a start, now i don't have to do it manually and the gnome session login is already on powersave.


> **3rdalbum said:**
> Use your computer's BIOS to underclock the CPU to whatever the frequency is when it's on "powersave". You might need to turn off frequency scaling in the BIOS.

my laptop bios does not have any useful options, thanks though. :(


still, is there no way to throttle the cpu sooner?

---

### Post by dcstar on 2009-04-01
> **Andreas1 said:**
> 
........
still, is there no way to throttle the cpu sooner?

The default kernel configuration runs the CPU at maximum at the boot phase (so the system will boot as quickly as possible) before changing to whatever is set in your system.

You can check this for yourself with the following command:
```
grep FREQ /boot/config-$(uname -r)
```
If you want a kernel that boots in power saving mode, you will have to compile your own kernel with that option changed.

---

### Post by Andreas1 on 2009-04-01
> **dcstar said:**
> compile your own kernel

:shock:

---

### Post by sdennie on 2009-04-01
> **Andreas1 said:**
> :shock:

It's a lot easier to compile your own kernel than you think.  However, if you don't want to do that, you can probably add the frequency governor you want to your initrd image and then put a script in your initrd image to load that module very early in the boot phase.  I don't have a way to test that but, I'm almost positive it would work.

---

