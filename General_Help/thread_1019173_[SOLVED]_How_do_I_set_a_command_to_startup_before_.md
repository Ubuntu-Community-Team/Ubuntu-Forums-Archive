---
title: "[SOLVED] How do I set a command to startup before the GDM service does?"
date: 2008-12-22
forum: General Help
---

### Post by andrewwg94 on 2008-12-22
i want to set this command to automatically start up before gnome display manager does.

[B]sudo fbset -a -xres 1264 -yres 712
[/B]
any help appreciated thanks!

---

### Post by taurus on 2008-12-22
Try putting this line in /etc/rc.local

```
fbset -a -xres 1264 -yres 712
```
before the last line, exit 0.

---

### Post by andrewwg94 on 2008-12-22
> **taurus said:**
> Try putting this line in /etc/rc.local

```
fbset -a -xres 1264 -yres 712
```
before the last line, exit 0.

i've tired that. didn't work. can you show me how the whole file would look? is there any other better way?

---

### Post by taurus on 2008-12-22
What does your /etc/rc.local look like then?

```
cat /etc/rc.local
```

---

### Post by lswb on 2008-12-22
The man page for fbset does suggest using rc.local, but that may not work because  ubuntu has gdm starting up before rc.local runs. So if you log in as soon as the gui login appears it's possible that rc.local hasn't run yet. Just as a test, with the command in your rc.local file as taurus suggests, try rebooting but do not login until all disk activity has stopped, and see if your command then runs OK. If so then you need to get it to run earlier in the boot sequence.

You could take a look here
[http://library.gnome.org/admin/gdm/stable/configuration.html](http://library.gnome.org/admin/gdm/stable/configuration.html)
which seems to suggest using /etc/gdm/Init/Default. If you decide to try that, make sure it is before the "exit 0" line in that file.

Another approach would be to add an initscript but hopefully that won't be necessary.

---

### Post by andrewwg94 on 2008-12-22
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

exit 0

---

### Post by adult swim on 2008-12-23
did you already take it out because its not in there now.  to edit it you can run ```
sudo nano /etc/rc.local
``` then past in sudo fbset -a -xres 1264 -yres 712 right above exit 0 so it would look like ```
sudo fbset -a -xres 1264 -yres 712
exit 0
```  hit ctrl+x then hit y and then enter.  that will exit you out of nano and save the file.

---

### Post by dcstar on 2008-12-23
> **andrewwg94 said:**
> i want to set this command to automatically start up before gnome display manager does.

[B]sudo fbset -a -xres 1264 -yres 712
[/B]
any help appreciated thanks!

The GDM process is run at S30gdm in /etc/rc2.d, you need a file with a lower number to run before that as they are all executed in numerical order. The S99rc.local script is one of the last things executed when run level 2 occurs so using /etc/rc.local will not run things before the GDM startup.

You need to put a script in /etc/init.d and then make a link in the /etc/rc2.d directory with a number lower than S30. Look at the existing files in both places for examples on how to set these up.

---

### Post by andrewwg94 on 2008-12-23
> **dcstar said:**
> The GDM process is run at S30gdm in /etc/rc2.d, you need a file with a lower number to run before that as they are all executed in numerical order. The S99rc.local script is one of the last things executed when run level 2 occurs so using /etc/rc.local will not run things before the GDM startup.

You need to put a script in /etc/init.d and then make a link in the /etc/rc2.d directory with a number lower than S30. Look at the existing files in both places for examples on how to set these up.

yes, yes, i'm trying to do exactly what you said, except i have no idea. i'm sort of new at this stuff. how would i create a file in /etc/init.d/? can you help me out? my problem is that every time fbset runs after GDM has started, which causes a garbled screen. and when i restart X by Ctrl+Alt+Backspace, it seems that the fbset command has been somehow 'un done'.

---

