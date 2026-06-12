---
title: "Wireless Mouse lost after suspend"
date: 2009-06-24
forum: General Help
---

### Post by ntbutler on 2009-06-24
Hi all.

I am running the 9.04 NBR on as ASUS EeePC 1000H. I have an E-3LUE wireless usb mouse. When I resume from suspend, the usb dongle indicates it knows there is activity coming from the mouse unit, but ubuntu won't recognise that anything is happening. Once I pull out the dongle and reattach it then everything works fine, I was just wondering if anyone know how to overcome this little inconvenience.

Cheers :)

---

### Post by ntbutler on 2009-06-27
anyone?

---

### Post by QIII on 2009-06-27
It may be a very esoteric issue with eeePCs.

Someone may be able to help.

In the meantime, you might want to check out [http://forum.eeeuser.com/](http://forum.eeeuser.com/)

If you find something, please come back and post the solution to this thread so that a resolution will be available here.

---

### Post by siryuhan on 2009-06-27
You could try modprobe -r usbmouse ; modprobe usbmouse

If this works, you should put the commands in the appropriate script; probably the resume.sh under acpi or something similar.

---

