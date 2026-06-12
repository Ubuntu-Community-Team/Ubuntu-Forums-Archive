---
title: "vboxgtk won't launch"
date: 2010-07-21
forum: Desktop Environments
---

### Post by clicker4721 on 2010-07-21
So, I fresh installed the Virtualbox GTK interface in 64-bit Ubuntu 10.04 LTS  from the Ubuntu Software Center, and it won't launch from the menu. When I try it from the terminal, this is the error readout:
```

clicker4721@clicker4721d:~$ vboxgtk
Traceback (most recent call last):
  File "/usr/bin/vboxgtk", line 90, in <module>
    vboxgtk.main()
  File "/usr/lib/pymodules/python2.6/vboxgtk/vboxgtk_iface.py", line 790, in main
    VBoxGtk(vboxdao)
  File "/usr/lib/pymodules/python2.6/vboxgtk/vboxgtk_iface.py", line 55, in __init__
    self.vboxdao.vm_states.Discarding: _("Discading"),
  File "/usr/lib/virtualbox/sdk/bindings/xpcom/python/xpcom/components.py", line 143, in __getattr__
    raise AttributeError, "'%s' interfaces do not define a constant '%s'" % (self.name, attr)
AttributeError: 'MachineState' interfaces do not define a constant 'Discarding'

```
Help, please, I'm anxious to use this. #-o

---

### Post by clicker4721 on 2010-08-18
Can't explain it! Uninstalled twice, now just use Virtualbox OSE, works just fine. :)

---

