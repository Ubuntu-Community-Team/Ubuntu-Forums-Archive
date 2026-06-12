---
title: "ctrl alt del in 9.04 gone?"
date: 2009-04-27
forum: General Help
---

### Post by frankwakeman on 2009-04-27
Am I imagining things or is the means of restarting X with ctrl alt delete no longer working/enabled?  Is there an alternative or do we just have to reboot ow where once we'd restart X?

Thanks.

---

### Post by El Zoido on 2009-04-27
You can use Alt + SysR(Print) + K instead.

If you would like the old behaviour (Ctrl+Alt+Backspace) you can try  ```
dontzap --disable
```

---

### Post by Dr_Willis on 2009-04-27
Im used to using alt-ctrl-delete on the CONSOLE to  go to reboot or halt runlevels quickly. by default it reboots.. under the old releases i could edit the /etc/inittab (i think, I may be getting other disrtos confused) to make instead halt/power off.. 

But for some reason under 9.04 I cant seem to find out where. 

Anyone seen the location of this setting?

---

### Post by Dr_Willis on 2009-04-27
Just to answer my  own question - and to help others who may be searching for this info.

To alter what 'alt-ctrl-delete' does at the CONSOLE (not in X) one edits the following file. (such a logical name for it also!)


```
sudo nano /etc/event.d/control-alt-delete
``` 



File contents

```
# control-alt-delete - emergency keypress handling
#
# This task is run whenever the Control-Alt-Delete key combination is
# pressed.  Usually used to shut down the machine.

start on control-alt-delete

exec /sbin/shutdown -r now "Control-Alt-Delete pressed"
```


From the 'shutdown' man pages, use -h for halt, -r for reboot. 


So if i need to shut down the PC right now.. as fast as i can. (like if the dog is on fire), I can hit 'alt-ctrl-backspace' to kill X, (if you used that nozap command to enable alt-ctrl-backspace that is) and get to the console and quickly hit (befor GDM restarts X) 'alt-ctrl-delete'


:P

---

