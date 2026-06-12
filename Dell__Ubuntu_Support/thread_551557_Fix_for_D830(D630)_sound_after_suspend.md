---
title: "Fix for D830(/D630) sound after suspend"
date: 2007-09-15
forum: Dell  Ubuntu Support
---

### Post by fred168 on 2007-09-15
Just in case noone else has seen this, the method posted at

[https://bugs.launchpad.net/ubuntu/+bug/122025](https://bugs.launchpad.net/ubuntu/+bug/122025)

seems to work on my D830 to give sound after suspend. In detail, create a file via [INDENT]
sudo gedit /etc/acpi/suspend.d/86-d830-sound.sh [/INDENT]
containing:
[INDENT]
#!/bin/sh

killall mixer_applet2
modprobe -r snd_hda_intel
[/INDENT]
then make it executable:
[INDENT]
sudo chmod a+x /etc/acpi/suspend.d/86-d830-sound.sh 
[/INDENT]
Then create another file via
[INDENT]
sudo gedit /etc/acpi/resume.d/66-d830-sound.sh 
[/INDENT]
containing:
[INDENT]
#!/bin/sh

modprobe snd_hda_intel
[/INDENT]
and make it executable:
[INDENT]
sudo chmod a+x /etc/acpi/resume.d/66-d830-sound.sh 
[/INDENT]
Now sound should work after suspend (at least if you exit any music players etc before suspending). On resuming the volume control is restarted and you need to click a dialogue box to allow this. (Does anyone know how to automate this?)

---

