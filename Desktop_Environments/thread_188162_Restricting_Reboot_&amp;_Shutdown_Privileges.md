---
title: "Restricting Reboot &amp; Shutdown Privileges"
date: 2006-06-03
forum: Desktop Environments
---

### Post by Jonathan Wiebe on 2006-06-03
I would like to restrict the ability of some users (my children) to hibernate, restart, or shutdown the computer. Is there any way to configure the quit button to only show them the logout, lock screen, and switch users options? I'm running Ubuntu 6.06 (Dapper).

Thanks in advance,

Jonathan Wiebe

---

### Post by bryanlking on 2006-06-03
You can download (with synaptic) pessulus which is a sort of lockdown editor for administrators.  It my do exactly what you want.

BK

---

### Post by Jonathan Wiebe on 2006-06-05
Unfortunately pessalus does not seem to have the options I am looking for.

I suppose that I'll just have to keep searching for another solution.

Thanks anyway,

Jonathan Wiebe

---

### Post by simonn on 2006-07-06
Just sat down and went through the source code to figure out the right way to lockdown the desktop in Ubuntu. 

The patches added by the Ubuntu project to Dapper make this significantly different to most linux distros I have used.

Edit /etc/X11/gdm.conf-custom and add the following to the [greeter] section:

```

SystemMenu=false

```

This turns the reboot and halt options off on the System -> Quit, and removes the halt, reboot and suspend/hybernate options from the gdm login actions menu. It does not, however, remove the hibernate button from System -> Quit.

Adding the following to the [daemon] section of /etc/X11/gdm.conf-custom is probably worth doing also:

```

RebootCommand=
HaltCommand=
HibernateCommand=
SuspendCommand=

```

This assigns no commands for these functions to gdm so that if, somehow, these options magically become available then no action will be taken if they are selected.

To remove the hibernate button from System -> Quit for all users:

```

$ sudo gconftool-2 -s /apps/gnome-power-manager/can_hibernate -t bool "false" --config-source xml:readwrite:/etc/gconf/gconf.xml.mandatory

```

The below is optional. By default halt is only allowed by root anyway, so this is another "just in case":

```

$ sudo chmod 750 /sbin/halt

```

/sbin/reboot is simply a link to /sbin/halt so we do not need to chmod 750 on it.

Finally, edit the files listed below and add an exit after the first line. The first line should be #!/bin/sh.

e.g.:

```

#!/bin/sh
exit
...

```

The files are:

/etc/acpi/hibernate.sh
/etc/acpi/powerbtn.sh
/etc/acpi/hibernatebtn.sh
/etc/acpi/sleepbtn.sh

It is suggested in some howtos on the web to chmod 000 them (or some of them). I think this is a bad idea as it will cause a permission denied error which the calling process may not expect. This is unlikely, but I think allowing the scripts to be called but do nothing is safer. Of course, this is horses for courses.

Now, in theory, the only way to reboot or halt is by using sudo reboot or sudo halt in a terminal and hibernation is not possible.

---

### Post by mtn on 2007-06-21
I'm trying to setup a PC for public web access. One of the things I would like to do is, only allow users the ability to log out. Ideally I would like to have the shutdown button (and functionality) available, but ask for a password before shutting down.

Anyone got any idea how to configure the shutdown button so only the shutdown and log out options are available? and shut down asks for a password? I only want one (guest user) account configured like this.

By the looks of it the post above is a system wide solution for configuring the shutdown options, this would not be appropriate in this instance!

---

