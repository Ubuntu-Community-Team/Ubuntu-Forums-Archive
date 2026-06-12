---
title: "How to set a script at startup in command line?"
date: 2009-05-15
forum: General Help
---

### Post by SkyPlooM on 2009-05-15
Hi,
I'm making a script who allows you to enable/disable the mouses and touchpads connected to the pc. This is about I had some troubles with xorg.conf, synaptics, SHMConfig (it is in another post...)

Well, my script creates a script file and it should be runned at startup.
I have to emulate the Aplications -> Preferences -> Startup Applications adding way

the script is like this:
```
header="
#!/bin/bash
### BEGIN INIT INFO
# Provides:          defaultdaemon
# Required-Start:    $remote_fs $syslog
# Required-Stop:     $remote_fs $syslog
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: Start daemon at boot time
# Description:       Enable service provided by daemon.
### END INIT INF
"
command=command_to_be_runned
echo $header > myscript
echo $command >> myscript
sudo chmod +x myscript
sudo mv myscript /etc/init.d/ 
sudo update-rc.d myscript defaults
```I think this should be the way to put it at startup, but it doesn't works.
I restarted and nothing happens.
I also tried doing
```
echo "/usr/bin/"$command >> myscript
```
(The executed program is on /usr/bin/)
I tried adding
```
sudo ln -s /etc/init.d/$raton1 /etc/rcS.d/K20myscript
sudo ln -s /etc/init.d/$raton1 /etc/rcS.d/S20myscript
```If I do in a terminal
```
 sudo sh /etc/init.d/myscript 
```it works, so the generated file works fine
If I type the command on 
Aplications -> Preferences -> Startup Applications and I restart, it works.
But I want to do it automatically with the script.

Any idea??
Thanks a lot.

---

### Post by dcstar on 2009-05-15
> **SkyPlooM said:**
> Hi,
I'm making a script who allows you to enable/disable the mouses and touchpads connected to the pc. This is about I had some troubles with xorg.conf, synaptics, SHMConfig (it is in another post...)
........
Any idea??
Thanks a lot.

Never, ever write scripts without full paths to all files/commands.

Just because something runs in **your** user shell environment does not mean that is will run elsewhere.

If you want scripts to run at boot up, call them from /etc/rc.local.

---

### Post by SkyPlooM on 2009-05-16
Thanks,
the solution was create the script in ~/.config/autostart, like Startup Applications does.

Cheers

---

