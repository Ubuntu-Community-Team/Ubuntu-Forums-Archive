---
title: "[SOLVED] Automate commands in Terminal?"
date: 2009-01-09
forum: General Help
---

### Post by Jarm1 on 2009-01-09
Hi everyone,

I didn't quite know how to word this so that it made sence to the gurus out there, so the best way to describe my question is; this is what I want to do:

Create a shortcut or some icon to put on the desktop, that will run a few commands in Terminal for me automatically. I would like to do this because the only way I have found to make my onboard LAN work is running the following each time I start the machine:

 sudo su

 rmmod forcedeth

 modprobe forcedeth msi=0 msix=0

 /etc/init.d/networking restart

It would be hugely more convenient to just click and have it execute the commands without having to manually put them in every time.

Thanks to anyone who can help!

---

### Post by heindsight on 2009-01-09
Well, what you could do is create a file containing the following:

```

#!/bin/sh
rmmod forcedeth
modprobe forcedeth msi=0 msix=0
/etc/init.d/networking restart

```

save it as net_restart.sh in your home directory and give yourself permission to execute it.

Next create a launcher on your desktop and put the following in the 'command' field of the create launcher dialog:
```
gksudo /home/Jarm1/net_restart.sh
```

I think there is a better solution though. The purpose of what you're trying to do is to reinsert the forcedeth kernel module with the options msi=0 msix=0. What you can do instead, is the following:
```
echo options forcedeth msi=0 msix=0 | sudo tee /etc/modprobe.d/forcedeth
```
this will create a file called forcedeth in /etc/modprobe.d, containing the single line
```
options forcedeth msi=0 msix=0
```
this will ensure that the forcedeth module is always loaded with those options.

---

### Post by kerry_s on 2009-01-09
> **Jarm1 said:**
> Hi everyone,

I didn't quite know how to word this so that it made sence to the gurus out there, so the best way to describe my question is; this is what I want to do:

Create a shortcut or some icon to put on the desktop, that will run a few commands in Terminal for me automatically. I would like to do this because the only way I have found to make my onboard LAN work is running the following each time I start the machine:

 sudo su

 rmmod forcedeth

 modprobe forcedeth msi=0 msix=0

 /etc/init.d/networking restart

It would be hugely more convenient to just click and have it execute the commands without having to manually put them in every time.

Thanks to anyone who can help!

just put those commands in /etc/rc.local and you wont have to click anything.

example:

```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

rmmod forcedeth
modprobe forcedeth msi=0 msix=0
/etc/init.d/networking restart

exit 0

```

---

### Post by Jarm1 on 2009-01-10
Brilliant! Your second option worked perfectly and does exactly what I was looking for with even less effort.

Thanks!

---

