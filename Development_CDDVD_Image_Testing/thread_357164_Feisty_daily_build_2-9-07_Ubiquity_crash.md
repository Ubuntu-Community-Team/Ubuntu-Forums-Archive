---
title: "Feisty daily build 2-9-07 Ubiquity crash"
date: 2007-02-09
forum: Development CD/DVD Image Testing
---

### Post by Trespasser on 2007-02-09
Feisty daily build 2-9-07 crashed on Ubiquity install during the opening of the partitioner. The md5 checksum was correct. I had used rsync to update 2-7-07 daily build to 2-9-07.

I've noticed since the introduction of linux-image 2.6.20-6 the development team has done away with /dev/sg0, /dev/sg1, /dev/scd0 and switched back to /dev/hdc. The problem is dma has been turned off for hdc. Also, hdc is listed under group floppy (just like /dev/scd0 was) and thus so is cdrom, dvd, dvdrw, etc.. NeroLinux complains about the lack of dma every time it opens.

Have a good day everyone.

---

### Post by pochu on 2007-02-11
Hi Trespasser:

Could you report a bug in Launchpad? Doing that, you let the devs fix it.

Regards
Pochu

---

### Post by Trespasser on 2007-02-11
Feisty daily builds 2-10-07 and 2-11-07 both crashed at the same place as 2-9-07. The situation seems to have went from bad to worse because after establishing the language and keyboard layout Ubiquity now by-passes the creation of the user, and root password, going directly to the partitioner where it crashes.

Rsync makes updating Feisty daily builds much easier (about 15 to 20 minutes) versus over 2 hours for a fresh download. Kudos to whoever came up with that one.

---

### Post by Trespasser on 2007-02-12
Feisty daily build 2-12-07 crashed as well after skipping step 5 (user creation). Here is a copy of the crash report:

root@ubuntu:~# ubiquity
Feb 12 13:33:39 ubiquity: Starting up '['log-output', '-t', 'ubiquity', '--pass-stdout', '/usr/lib/ubiquity/localechooser/localechooser']' for ubiquity.components.language.Language
Feb 12 13:33:39 ubiquity: Watching for question patterns ^languagechooser/language-name, ^countrychooser/shortlist$
Feb 12 13:34:16 ubiquity: Starting up '['log-output', '-t', 'ubiquity', '--pass-stdout', '/usr/share/ubiquity/tzsetup']' for ubiquity.components.timezone.Timezone
Feb 12 13:34:16 ubiquity: Watching for question patterns ^time/zone$
Feb 12 13:34:23 ubiquity: Starting up '['log-output', '-t', 'ubiquity', '--pass-stdout', '/usr/lib/ubiquity/console-setup/console-setup.postinst', 'configure']' for ubiquity.components.console_setup.ConsoleSetup
Feb 12 13:34:23 ubiquity: Watching for question patterns ^console-setup/layout, ^console-setup/variant
Feb 12 13:34:23 ubiquity: Setting keyboard layout: pc105 us  []
Feb 12 13:34:56 ubiquity: Starting up '['log-output', '-t', 'ubiquity', '--pass-stdout', '/bin/partman']' for ubiquity.components.partman.Partman
Feb 12 13:34:56 ubiquity: Watching for question patterns ^partman-auto/.*automatically_partition$, ^partman-auto/select_disk$, ^partman-partitioning/new_size$, ^partman/choose_partition$, ^partman/confirm.*, type:boolean, ERROR, PROGRESS, ^partman/confirm_new_label$, ^partman/free_space$, ^partman/active_partition$, ^partman-partitioning/new_partition_(size|type|place)$, ^partman-partitioning/confirm_resize$, ^partman-partitioning/new_size$, ^partman-target/choose_method$, ^partman-basicfilesystems/(fat_mountpoint|mountpoint|mountpoint_manual)$, ^partman/exception_handler$, ^partman/exception_handler_note$
Feb 12 13:34:57 ubiquity: Partman: update_partitions = None
Feb 12 13:34:57 ubiquity: Partman: update_partitions = None
Feb 12 13:34:57 ubiquity: Partman: update_partitions = None
Feb 12 13:34:57 ubiquity: Partman: update_partitions = None
Feb 12 13:34:58 ubiquity: Partman: state = [['', None, None]]
Exception in GTK frontend (invoking crash handler):
Traceback (most recent call last):
  File "/usr/lib/ubiquity/ubiquity/frontend/gtkui.py", line 1408, in watch_debconf_fd_helper
    return callback(source, debconf_condition)
  File "/usr/lib/ubiquity/ubiquity/filteredcommand.py", line 176, in process_input
    if not self.process_line():
  File "/usr/lib/ubiquity/ubiquity/filteredcommand.py", line 110, in process_line
    return self.dbfilter.process_line()
  File "/usr/lib/ubiquity/ubiquity/debconffilter.py", line 268, in process_line
    widget.subst(question, key, value)
  File "/usr/lib/ubiquity/ubiquity/components/partman.py", line 209, in subst
    assert state[0] == 'partman/active_partition'
AssertionError

Traceback (most recent call last):
  File "/usr/lib/ubiquity/ubiquity/frontend/gtkui.py", line 1408, in watch_debconf_fd_helper
    return callback(source, debconf_condition)
  File "/usr/lib/ubiquity/ubiquity/filteredcommand.py", line 176, in process_input
    if not self.process_line():
  File "/usr/lib/ubiquity/ubiquity/filteredcommand.py", line 110, in process_line
    return self.dbfilter.process_line()
  File "/usr/lib/ubiquity/ubiquity/debconffilter.py", line 268, in process_line
    widget.subst(question, key, value)
  File "/usr/lib/ubiquity/ubiquity/components/partman.py", line 209, in subst
    assert state[0] == 'partman/active_partition'
AssertionError
root@ubuntu:~# 

Also, I was requested to send a crash report after the crash...so I did.

---

### Post by pochu on 2007-02-12
Please, report this in Launchpad, not here.

Read this to see what you should do:
[http://ubuntuforums.org/showthread.php?t=331123](http://ubuntuforums.org/showthread.php?t=331123)

And please report your bug here ([if it hasn't been reported yet]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bugs?advanced=1")):
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+filebug](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+filebug)

Regards
Emilio

---

