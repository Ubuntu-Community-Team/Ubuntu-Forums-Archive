---
title: "grub installer stops with error 2"
date: 2009-01-18
forum: General Help
---

### Post by rickycodie on 2009-01-18
i built this iso with remastersys on mint, and whenever i try to install ubiquity hangs and exits at the grub installation stage. i know that remasystersys has it's own forums but they are down and i need this fixed as fast as i can so i can stop using windows. :x so i am including my debug file that i got from running sudo ubiquity --debug.

so i've tried to install grub through the normal means (root, setup, exit) setup hits error 17, cannot mount partition, hd0,0. also if i reboot i get error 15 or grub just doesn't even start. supergrubdisk don't work, and i am throughly frustrated. i need help.

let me know if you guys need anything else from me

uhhhhh......i can't upload the file so here's the copy and paste. sorry it's long.
[HTML]Ubiquity 1.10.10
partition: ('1', '32256-53011929599', '53011897344', 'primary', 'ntfs', '/dev/sda1', '')
partition: ('2', '53011929600-484008376319', '430996446720', 'primary', 'ext3', '/dev/sda2', '')
partition: ('3', '484008376320-497884423679', '13876047360', 'primary', 'ext3', '/dev/sda3', '')
partition: ('4', '497884423680-500105249279', '2220825600', 'primary', 'linux-swap', '/dev/sda4', '')
Exception in GTK frontend (invoking crash handler):
Traceback (most recent call last):
File "/usr/lib/ubiquity/bin/ubiquity", line 229, in <module>
main()
File "/usr/lib/ubiquity/bin/ubiquity", line 224, in main
install(args[0])
File "/usr/lib/ubiquity/bin/ubiquity", line 68, in install
ret = wizard.run()
File "/usr/lib/ubiquity/ubiquity/frontend/gtk_ui.py", line 437, in run
self.progress_loop()
File "/usr/lib/ubiquity/ubiquity/frontend/gtk_ui.py", line 825, in progress_loop
(ret, realtb))
RuntimeError: Install failed with exit code 1
Traceback (most recent call last):
File "/usr/share/ubiquity/install.py", line 2112, in <module>
install.run()
File "/usr/share/ubiquity/install.py", line 428, in run
self.configure_bootloader()
File "/usr/share/ubiquity/install.py", line 1599, in configure_bootloader
"GrubInstaller failed with code %d" % ret)
InstallStepError: GrubInstaller failed with code 2

a little stuff in the middle and


Jan 18 06:16:47 debconf (filter): <-- INPUT low grub-installer/password
debconf (developer): <-- METAGET grub-installer/password Type
debconf (developer): --> 1 password
debconf (developer): <-- INPUT low grub-installer/password
debconf (developer): --> 30 question skipped
Jan 18 06:16:47 debconf (filter): <-- GO
debconf (developer): <-- GO
debconf (developer): --> 0 ok
Jan 18 06:16:47 debconf (filter): <-- GET grub-installer/password
debconf (developer): <-- GET grub-installer/password
debconf (developer): --> 1
Jan 18 06:16:48 debconf (filter): <-- GET debian-installer/add-kernel-opts
debconf (developer): <-- GET debian-installer/add-kernel-opts
debconf (developer): --> 1
Jan 18 06:16:48 debconf (filter): <-- GET grub-installer/bootdev_directory
debconf (developer): <-- GET grub-installer/bootdev_directory
debconf (developer): --> 1
Jan 18 06:16:48 debconf (filter): <-- PROGRESS STOP
Jan 18 06:16:48 debconf (filter): widget found for grub-installer/progress/title
Jan 18 06:16:48 debconf (filter): --> 0 OK
Jan 18 06:16:48 ubiquity: ['log-output', '-t', 'ubiquity', '--pass-stdout', '/usr/share/ubiquity/install.py'] exited with code 1
Exception in GTK frontend (invoking crash handler):
Traceback (most recent call last):
File "/usr/lib/ubiquity/bin/ubiquity", line 229, in <module>
main()
File "/usr/lib/ubiquity/bin/ubiquity", line 226, in main
install()
File "/usr/lib/ubiquity/bin/ubiquity", line 68, in install
ret = wizard.run()
File "/usr/lib/ubiquity/ubiquity/frontend/gtk_ui.py", line 437, in run
self.progress_loop()
File "/usr/lib/ubiquity/ubiquity/frontend/gtk_ui.py", line 825, in progress_loop
(ret, realtb))
RuntimeError: Install failed with exit code 1
Traceback (most recent call last):
File "/usr/share/ubiquity/install.py", line 2112, in <module>
install.run()
File "/usr/share/ubiquity/install.py", line 428, in run
self.configure_bootloader()
File "/usr/share/ubiquity/install.py", line 1599, in configure_bootloader
"GrubInstaller failed with code %d" % ret)
InstallStepError: GrubInstaller failed with code 2



Traceback (most recent call last):
File "/usr/lib/ubiquity/bin/ubiquity", line 229, in <module>
main()
File "/usr/lib/ubiquity/bin/ubiquity", line 226, in main
install()
File "/usr/lib/ubiquity/bin/ubiquity", line 68, in install
ret = wizard.run()
File "/usr/lib/ubiquity/ubiquity/frontend/gtk_ui.py", line 437, in run
self.progress_loop()
File "/usr/lib/ubiquity/ubiquity/frontend/gtk_ui.py", line 825, in progress_loop
(ret, realtb))
RuntimeError: Install failed with exit code 1
Traceback (most recent call last):
File "/usr/share/ubiquity/install.py", line 2112, in <module>
install.run()
File "/usr/share/ubiquity/install.py", line 428, in run
self.configure_bootloader()
File "/usr/share/ubiquity/install.py", line 1599, in configure_bootloader
"GrubInstaller failed with code %d" % ret)
InstallStepError: GrubInstaller failed with code 2[/HTML]

---

