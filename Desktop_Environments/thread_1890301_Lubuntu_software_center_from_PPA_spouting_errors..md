---
title: "Lubuntu software center from PPA spouting errors."
date: 2011-12-03
forum: Desktop Environments
---

### Post by casbahdk on 2011-12-03
I have just installed Lubuntu 11.10 on my netbook. There were a number of problems that I sorted, like no sound, but I haven't been able to sort out the errors after having installed the Lubuntu software center:```
$ lubuntu-software-center

(lubuntu-software-center:2962): Gtk-WARNING **: Theme parsing error: gtk-buttons.css:159:10: Expected valid border

(lubuntu-software-center:2962): Gtk-WARNING **: Theme parsing error: gtk-bars.css:102:16: Themeing engine 'adwaita' not found

(lubuntu-software-center:2962): Gtk-WARNING **: Theme parsing error: gtk-bars.css:117:16: Themeing engine 'adwaita' not found

(lubuntu-software-center:2962): Gtk-WARNING **: Theme parsing error: gtk-bars.css:134:16: Themeing engine 'adwaita' not found

(lubuntu-software-center:2962): Gtk-WARNING **: Theme parsing error: gtk-bars.css:153:16: Themeing engine 'adwaita' not found

(lubuntu-software-center:2962): Gtk-WARNING **: Theme parsing error: gtk-bars.css:165:16: Themeing engine 'adwaita' not found

(lubuntu-software-center:2962): Gtk-WARNING **: Theme parsing error: gtk-bars.css:175:16: Themeing engine 'adwaita' not found

(lubuntu-software-center:2962): Gtk-WARNING **: Theme parsing error: gtk-bars.css:186:16: Themeing engine 'adwaita' not found

(lubuntu-software-center:2962): Gtk-WARNING **: Theme parsing error: gtk-bars.css:198:16: Themeing engine 'adwaita' not found

(lubuntu-software-center:2962): Gtk-WARNING **: Theme parsing error: gtk-bars.css:208:16: Themeing engine 'adwaita' not found

(lubuntu-software-center:2962): Gtk-WARNING **: Theme parsing error: gtk-bars.css:218:16: Themeing engine 'adwaita' not found

(lubuntu-software-center:2962): Gtk-WARNING **: Theme parsing error: gtk-bars.css:223:16: Themeing engine 'adwaita' not found

(lubuntu-software-center:2962): Gtk-CRITICAL **: gtk_container_add: assertion `GTK_IS_CONTAINER (container)' failed
Traceback (most recent call last):
  File "/usr/bin/lubuntu-software-center", line 23, in <module>
    import LSC.main
  File "/usr/lib/python2.7/dist-packages/LSC/main.py", line 34, in <module>
    from testnet import testnet
ImportError: No module named testnet
```Any ideas?

---

### Post by marinara on 2011-12-04
I've had a lot of package related problems, and half of them went away when I stopped using Lubuntu software center

---

### Post by casbahdk on 2011-12-04
> **marinara said:**
> I've had a lot of package related problems, and half of them went away when I stopped using Lubuntu software center

So far I haven't experienced any package related problems. I also haven't started using the Lubuntu software center yet, because of the errors it spits out. Maybe I will leave it installed and see if any updates solve the problem. I rarely use the software center, regardless of whether it is in the u,k,x,l iteration, as I usually use Apt or Synaptic. I have found the software centers sometimes useful when I am unsure what software is available for specific areas I am unfamiliar with, such as firewall, games, etc.

---

### Post by MG&amp;TL on 2011-12-04
EDIT: fixed now. a apt-get update && apt-get upgrade should fix.

Sorry again for problems.

---

### Post by casbahdk on 2011-12-04
> **MG&TL said:**
> EDIT: fixed now. a apt-get update && apt-get upgrade should fix.

Sorry again for problems.

Thanks for the quick update. It starts without problems now. I have yet to try to install software via the center.

If only everyone was just as fast at ironing the kinks out of Ubuntu ;)

---

### Post by MG&amp;TL on 2011-12-04
> **casbahdk said:**
> Thanks for the quick update. It starts without problems now. I have yet to try to install software via the center.

If only everyone was just as fast at ironing the kinks out of Ubuntu ;)
No problem, if only the kinks didn't exist to start with. :)

---

