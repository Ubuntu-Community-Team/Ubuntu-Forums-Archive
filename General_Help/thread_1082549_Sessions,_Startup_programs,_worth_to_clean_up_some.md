---
title: "Sessions, Startup programs, worth to clean up some?"
date: 2009-02-27
forum: General Help
---

### Post by UranUtan on 2009-02-27
Hi,

Is it worth to disable some program in the startup list? For example:
- Bluetooth Manager
- Visual Assistance
- User folder update

Is there a complete description of startup programs somewhere and is it worth to disable some to speed up Ubuntu startup time?

BTW, is it recommended to mess with the startup programs in Sessions? Sorry this is just a "Windows survival" reflex, just want to have a peek on whats running may be to disable unnecessary services (in the Windows world, sometimes this also means unwanted junks)

Thanks in advance for any help.

---

### Post by dcstar on 2009-02-28
> **UranUtan said:**
> Hi,

Is it worth to disable some program in the startup list? For example:
- Bluetooth Manager
- Visual Assistance
- User folder update

Is there a complete description of startup programs somewhere and is it worth to disable some to speed up Ubuntu startup time?

BTW, is it recommended to mess with the startup programs in Sessions? Sorry this is just a "Windows survival" reflex, just want to have a peek on whats running may be to disable unnecessary services (in the Windows world, sometimes this also means unwanted junks)

Thanks in advance for any help.

A lot of the problems in these forums are from people who try to "clean up" things that aren't really causing any real problems, you can also try but it is generally not worth the effort.

---

### Post by entr3p on 2009-02-28
> **UranUtan said:**
> Hi,

Is it worth to disable some program in the startup list? For example:
- Bluetooth Manager
- Visual Assistance
- User folder update

Is there a complete description of startup programs somewhere and is it worth to disable some to speed up Ubuntu startup time?

BTW, is it recommended to mess with the startup programs in Sessions? Sorry this is just a "Windows survival" reflex, just want to have a peek on whats running may be to disable unnecessary services (in the Windows world, sometimes this also means unwanted junks)

Thanks in advance for any help.
Realistically you wont see much if any visible to the eye improvements by disabling those startup programs but it seems if you do then no harm will be done.

---

### Post by UranUtan on 2009-02-28
Thanks for your advice. Normally I won't bother. But currently I am setting up a project where the Ubuntu machine runs two VMs simultaneously. RAM availability becomes critical (Ubuntu 8.10 x32, P4 Prescott 2.8 GHz, 3 GB Ram, two VirtualBox 2.14 VMs each allocated 1280 MB, guest OS = Windows 2008 ).

BTW, from time to times, the application window (could be Firefox, Rhythmbox, VM screen) suddenly "blacks out" and becomes unresponsive for a few seconds. Then the colors come back and the application works again. [COLOR="Red"]Is it a sign of resources strain or what is happening?[/COLOR] 

FYI, System Monitor shows 93% Ram used (2.8 GB / 3 GB), Swap 500 MB used (10%). [COLOR="Red"]Do the figures look bad?[/COLOR]

---

### Post by UranUtan on 2009-02-28
Hi,

Any one can help me about the temporary "black out" screen described above?

Thanks in advance.

---

### Post by oldos2er on 2009-02-28
See this thread: [http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491)

 I prefer to use sysv-rc-conf to disable unneeded services.

---

