---
title: "hibernate stand by/suspend does come back with blank Gnome screen"
date: 2008-01-16
forum: Desktop Environments
---

### Post by mvdberg112 on 2008-01-16
Ubuntu 7.10 Gutsy
Quite default with some extra applications
Choose Hibernate or Resume (Standby)

Turn computer back on and screen of the X terminal (Gnome) is blank, with a cursor blinking in the top left corner. Kill Gnome and restart gdm works.

On other occasion, I assumed that Gnome was still working, so carred out the right keystroke sequence to restart the system without seeing anything on the scrren, and that worked; Conclusion: Gnome still runnning, but not restoring or updating the screen.

Any suggestions why this happens?

---

### Post by sonofusion82 on 2008-01-16
try this [http://ubuntuforums.org/showthread.php?t=596666](http://ubuntuforums.org/showthread.php?t=596666)

---

### Post by mvdberg112 on 2008-01-16
Thanks for referring me to this page. I understand now that hibernate and suspend is controlled by packages acpi and acpi-support. However:
1. The solution did not work (see /etc/default/acpi-support file below)
2. cannot find good documentation is on acpi

Log file after selecting 'suspent from the Gnome 'power button' menu (system goes into suspend or standby), then pressing a key on the keyboard (system wakes up again); blank screen, only option is to press the power button a few times, and system closes nicely - it seems that the software and the kernel are still running, but that and/or the keyboard and/or screen do not work. It is not possible to goto a TTY1 with CTRL-ALT-F1 - in that case the the monitor goes off, as if there is no signal from the graphics adapter; when CTRL-ALT-F7 again, then monitor comes on, but with black screen and sometimes a cursus in the top-right.
/var/log/acpid
```
[Wed Jan 16 10:18:28 2008] starting up
[Wed Jan 16 10:18:28 2008] 72 rules loaded
[Wed Jan 16 10:18:30 2008] client connected from 4613[107:116]
[Wed Jan 16 10:18:30 2008] 1 client rule loaded
[Wed Jan 16 10:18:46 2008] client connected from 7383[0:0]
[Wed Jan 16 10:18:46 2008] 1 client rule loaded
[Wed Jan 16 10:32:28 2008] client connected from 8230[0:0]
[Wed Jan 16 10:32:28 2008] 1 client rule loaded
[Wed Jan 16 10:32:37 2008] client connected from 8258[0:0]
[Wed Jan 16 10:32:37 2008] 1 client rule loaded
[Wed Jan 16 10:33:18 2008] client connected from 8258[0:0]
[Wed Jan 16 10:33:18 2008] 1 client rule loaded
[Wed Jan 16 10:35:37 2008] client connected from 8258[0:0]
[Wed Jan 16 10:35:37 2008] 1 client rule loaded
[Wed Jan 16 10:36:11 2008] client connected from 8258[0:0]
[Wed Jan 16 10:36:11 2008] 1 client rule loaded
[Wed Jan 16 10:36:19 2008] client connected from 9216[0:0]
[Wed Jan 16 10:36:19 2008] 1 client rule loaded
[Wed Jan 16 10:36:28 2008] client connected from 9216[0:0]
[Wed Jan 16 10:36:28 2008] 1 client rule loaded
[Wed Jan 16 10:36:43 2008] client connected from 9216[0:0]
[Wed Jan 16 10:36:43 2008] 1 client rule loaded
[Wed Jan 16 10:37:49 2008] client connected from 9555[0:0]
[Wed Jan 16 10:37:49 2008] 1 client rule loaded
[Wed Jan 16 10:38:21 2008] client connected from 9783[0:0]
[Wed Jan 16 10:38:21 2008] 1 client rule loaded
[Wed Jan 16 11:05:42 2008] received event "button/power PWRF 00000080 00000001"
[Wed Jan 16 11:05:42 2008] notifying client 4613[107:116]
[Wed Jan 16 11:05:42 2008] notifying client 7383[0:0]
[Wed Jan 16 11:05:42 2008] client has disconnected
[Wed Jan 16 11:05:42 2008] notifying client 8230[0:0]
[Wed Jan 16 11:05:42 2008] client has disconnected
[Wed Jan 16 11:05:42 2008] notifying client 8258[0:0]
[Wed Jan 16 11:05:42 2008] client has disconnected
[Wed Jan 16 11:05:42 2008] notifying client 8258[0:0]
[Wed Jan 16 11:05:42 2008] client has disconnected
[Wed Jan 16 11:05:42 2008] notifying client 8258[0:0]
[Wed Jan 16 11:05:42 2008] client has disconnected
[Wed Jan 16 11:05:42 2008] notifying client 8258[0:0]
[Wed Jan 16 11:05:42 2008] client has disconnected
[Wed Jan 16 11:05:42 2008] notifying client 9216[0:0]
[Wed Jan 16 11:05:42 2008] client has disconnected
[Wed Jan 16 11:05:42 2008] notifying client 9216[0:0]
[Wed Jan 16 11:05:42 2008] client has disconnected
[Wed Jan 16 11:05:42 2008] notifying client 9216[0:0]
[Wed Jan 16 11:05:42 2008] client has disconnected
[Wed Jan 16 11:05:42 2008] notifying client 9555[0:0]
[Wed Jan 16 11:05:42 2008] client has disconnected
[Wed Jan 16 11:05:42 2008] notifying client 9783[0:0]
[Wed Jan 16 11:05:42 2008] client has disconnected
[Wed Jan 16 11:05:42 2008] executing action "/etc/acpi/powerbtn.sh"
[Wed Jan 16 11:05:42 2008] BEGIN HANDLER MESSAGES
[Wed Jan 16 11:05:42 2008] END HANDLER MESSAGES
[Wed Jan 16 11:05:42 2008] action exited with status 0
[Wed Jan 16 11:05:42 2008] completed event "button/power PWRF 00000080 00000001"
[Wed Jan 16 11:05:44 2008] received event "button/power PWRF 00000080 00000002"
[Wed Jan 16 11:05:44 2008] notifying client 4613[107:116]
[Wed Jan 16 11:05:44 2008] executing action "/etc/acpi/powerbtn.sh"
[Wed Jan 16 11:05:44 2008] BEGIN HANDLER MESSAGES
[Wed Jan 16 11:05:45 2008] END HANDLER MESSAGES
[Wed Jan 16 11:05:45 2008] action exited with status 0
[Wed Jan 16 11:05:45 2008] completed event "button/power PWRF 00000080 00000002"
[Wed Jan 16 11:05:46 2008] received event "button/power PWRF 00000080 00000003"
[Wed Jan 16 11:05:46 2008] notifying client 4613[107:116]
[Wed Jan 16 11:05:46 2008] executing action "/etc/acpi/powerbtn.sh"
[Wed Jan 16 11:05:46 2008] BEGIN HANDLER MESSAGES
[Wed Jan 16 11:05:46 2008] END HANDLER MESSAGES
[Wed Jan 16 11:05:46 2008] action exited with status 0
[Wed Jan 16 11:05:46 2008] completed event "button/power PWRF 00000080 00000003"
[Wed Jan 16 11:05:47 2008] received event "button/power PWRF 00000080 00000004"
[Wed Jan 16 11:05:47 2008] notifying client 4613[107:116]
[Wed Jan 16 11:05:47 2008] executing action "/etc/acpi/powerbtn.sh"
[Wed Jan 16 11:05:47 2008] BEGIN HANDLER MESSAGES
[Wed Jan 16 11:05:47 2008] END HANDLER MESSAGES
[Wed Jan 16 11:05:47 2008] action exited with status 0
[Wed Jan 16 11:05:47 2008] completed event "button/power PWRF 00000080 00000004"
[Wed Jan 16 11:05:47 2008] received event "button/power PWRF 00000080 00000005"
[Wed Jan 16 11:05:47 2008] notifying client 4613[107:116]
[Wed Jan 16 11:05:47 2008] executing action "/etc/acpi/powerbtn.sh"
[Wed Jan 16 11:05:47 2008] BEGIN HANDLER MESSAGES
[Wed Jan 16 11:05:47 2008] END HANDLER MESSAGES
[Wed Jan 16 11:05:47 2008] action exited with status 0
[Wed Jan 16 11:05:47 2008] completed event "button/power PWRF 00000080 00000005"
[Wed Jan 16 11:05:47 2008] received event "button/power PWRF 00000080 00000006"
[Wed Jan 16 11:05:47 2008] notifying client 4613[107:116]
[Wed Jan 16 11:05:47 2008] executing action "/etc/acpi/powerbtn.sh"
[Wed Jan 16 11:05:47 2008] BEGIN HANDLER MESSAGES
[Wed Jan 16 11:05:47 2008] END HANDLER MESSAGES
[Wed Jan 16 11:05:47 2008] action exited with status 0
[Wed Jan 16 11:05:47 2008] completed event "button/power PWRF 00000080 00000006"
[Wed Jan 16 11:05:48 2008] received event "button/power PWRF 00000080 00000007"
[Wed Jan 16 11:05:48 2008] notifying client 4613[107:116]
[Wed Jan 16 11:05:48 2008] executing action "/etc/acpi/powerbtn.sh"
[Wed Jan 16 11:05:48 2008] BEGIN HANDLER MESSAGES
[Wed Jan 16 11:05:48 2008] END HANDLER MESSAGES
[Wed Jan 16 11:05:48 2008] action exited with status 0
[Wed Jan 16 11:05:48 2008] completed event "button/power PWRF 00000080 00000007"
[Wed Jan 16 11:05:48 2008] received event "button/power PWRF 00000080 00000008"
[Wed Jan 16 11:05:48 2008] notifying client 4613[107:116]
[Wed Jan 16 11:05:48 2008] executing action "/etc/acpi/powerbtn.sh"
[Wed Jan 16 11:05:48 2008] BEGIN HANDLER MESSAGES
[Wed Jan 16 11:05:48 2008] END HANDLER MESSAGES
[Wed Jan 16 11:05:48 2008] action exited with status 0
[Wed Jan 16 11:05:48 2008] completed event "button/power PWRF 00000080 00000008"
[Wed Jan 16 11:05:49 2008] received event "button/power PWRF 00000080 00000009"
[Wed Jan 16 11:05:49 2008] notifying client 4613[107:116]
[Wed Jan 16 11:05:49 2008] executing action "/etc/acpi/powerbtn.sh"
[Wed Jan 16 11:05:49 2008] BEGIN HANDLER MESSAGES
[Wed Jan 16 11:05:49 2008] END HANDLER MESSAGES
[Wed Jan 16 11:05:49 2008] action exited with status 0
[Wed Jan 16 11:05:49 2008] completed event "button/power PWRF 00000080 00000009"
[Wed Jan 16 11:05:53 2008] exiting
```

Settings in /etc/default/acpi-support
```

# Comment the next line to disable ACPI suspend to RAM
ACPI_SLEEP=true

# Comment the next line to disable suspend to disk
ACPI_HIBERNATE=true

# Change the following to "standby" to use ACPI S1 sleep, rather than S3.
# This will save less power, but may work on more machines
ACPI_SLEEP_MODE=mem

# Add modules to this list to have them removed before suspend and reloaded
# on resume. An example would be MODULES="em8300 yenta_socket"
#
# Note that network cards and USB controllers will automatically be unloaded 
# unless they're listed in MODULES_WHITELIST
MODULES=""

# Add modules to this list to leave them in the kernel over suspend/resume
MODULES_WHITELIST=""

# Should we save and restore state using the VESA BIOS Extensions?
# SAVE_VBE_STATE=true 2007-01-15
SAVE_VBE_STATE=false

# The file that we use to save the vbestate
VBESTATE=/var/lib/acpi-support/vbestate

# Should we attempt to warm-boot the video hardware on resume?
#POST_VIDEO=true 2007-01-15
POST_VIDEO=false

# Save and restore video state?
# uncommented 2007-01-15
SAVE_VIDEO_PCI_STATE=true

# Should we switch the screen off with DPMS on suspend?
USE_DPMS=true

# Use Radeontool to switch the screen off? Seems to be needed on some machines
# RADEON_LIGHT=true

# Uncomment the next line to switch away from X and back again after resume.
# This is needed for some hardware, but should be unnecessary on most.
# DOUBLE_CONSOLE_SWITCH=true

# Set the following to "platform" if you want to use ACPI to shut down
# your machine on hibernation
HIBERNATE_MODE=shutdown

# Comment this out to disable screen locking on resume
LOCK_SCREEN=true

# Uncomment this line to have DMA disabled before suspend and reenabled
# afterwards
# DISABLE_DMA=true

# Uncomment this line to attempt to reset the drive on resume. This seems
# to be needed for some Sonys
# RESET_DRIVE=true

# Add services to this list to stop them before suspend and restart them in 
# the resume process.
STOP_SERVICES=""

# Restart Infra Red services on resume - off by default as it crashes some
# machines
RESTART_IRDA=false

# Switch to laptop-mode on battery power - off by default as it causes odd
# hangs on some machines
ENABLE_LAPTOP_MODE=false

# Spindown time on battery
SPINDOWN_TIME=12
```
Note that I started with (leaving all other settings the same in the file):
```
# Should we save and restore state using the VESA BIOS Extensions?
 SAVE_VBE_STATE=true 

# Should we attempt to warm-boot the video hardware on resume?
POST_VIDEO=true 

# Save and restore video state?
# SAVE_VIDEO_PCI_STATE=true
```

Any suggestions helpful.
[http://ubuntuforums.org/showthread.php?t=596666](http://ubuntuforums.org/showthread.php?t=596666) seems to work for the one poseted it, but  did not help for me (thanks anyway for the link; was still good help in troubleshooting and could have been the solution).

Oh, PC model is Compaq Evo 2400 MHz, 512 MB, frontside bus 166 MHz

---

### Post by mvdberg112 on 2008-07-01
Hibernate and Standby work now, which means that coming back from either one, it does not give a black screen. Some issues still seem to exist, which I think have to do with the limited driver or the limited information on the driver configuration.

After testing with eight different settings. Setting seven was the hit... It is not perfect yet, but it works. See the right settings below. 

> **System config**]
  Compaq EVO D510 2400 MHz 512 MB RAM, i845 chipset, using 
  GNOME
  Ubuntu 7.10 with kernal 2.5.22-15-generic. 
  acpi 0.09-3ubuntu1 and 
  acpid1.0.4-5ubuntu8
  acpi-support 0.103 
(let me know if you need any other information in case you work on these packages or have a problem yourselves)

In cat **/etc/default/acpi-support**, used the following parameters and values:[B]
  SAVE_VBE_STATE=false
  POST_VIDEO=true
  SAVE_VIDEO_PCI_STATE=false[/B]
All other values I left default.


See the full report of the testing below, for anybody who can benefit.
```

TEST 1 Jan 19 ACPI-support
# Test 1 
SAVE_VBE_STATE=false
POST_VIDEO=false
SAVE_VIDEO_PCI_STATE=false
# result: disaster: comes back with black screen from standby-keyboard hangs - power button needed to restar
[Sat Jan 19 11:52:59 2008] notifying client 11434[0:0]
[Sat Jan 19 11:52:59 2008] client has disconnected
[Sat Jan 19 11:52:59 2008] executing action "/etc/acpi/powerbtn.sh"
[Sat Jan 19 11:52:59 2008] BEGIN HANDLER MESSAGES
[Sat Jan 19 11:52:59 2008] END HANDLER MESSAGES
[Sat Jan 19 11:52:59 2008] action exited with status 0
[Sat Jan 19 11:52:59 2008] completed event "button/power PWRF 00000080 00000001"
[Sat Jan 19 11:53:00 2008] received event "button/power PWRF 00000080 00000002"
[Sat Jan 19 11:53:00 2008] notifying client 4621[107:116]
[Sat Jan 19 11:53:00 2008] executing action "/etc/acpi/powerbtn.sh"
[Sat Jan 19 11:53:00 2008] BEGIN HANDLER MESSAGES
[Sat Jan 19 11:53:00 2008] END HANDLER MESSAGES
[Sat Jan 19 11:53:00 2008] action exited with status 0
[Sat Jan 19 11:53:00 2008] completed event "button/power PWRF 00000080 00000002"
note that power button was pressed, but system did not do anything -> the script does not receive the right info perhaps.
----------
# Test 2
SAVE_VBE_STATE=true
POST_VIDEO=false
SAVE_VIDEO_PCI_STATE=true
# result: gdm pretty good: comes back with password prompt and after that with gnome desktop. can work. however, one
# strange thing: the screen keeps a kind of flickering. When i do not nothing (and so no screen update is needed), it is a stable as it can be. But when I type this very text in gedit or open gedit or any kind of action to open another window, the screen flickers, as if it needs to rebuild the screen again and again....    The tty all 6 work fine. Seems to work very good.
[Sat Jan 19 11:53:51 2008] starting up
[Sat Jan 19 11:53:51 2008] 72 rules loaded
[Sat Jan 19 11:53:52 2008] client connected from 4626[107:116]
[Sat Jan 19 11:53:52 2008] 1 client rule loaded
[Sat Jan 19 11:54:08 2008] client connected from 7396[0:0]
[Sat Jan 19 11:54:08 2008] 1 client rule loaded
[Sat Jan 19 12:03:08 2008] client connected from 7396[0:0]
[Sat Jan 19 12:03:08 2008] 1 client rule loaded
Note that the press of the 'suspend' button is not mentioned here - appearently the suspend button is not an event for ACPID. which is logical since it is software from the gdm.
[Sat Jan 19 12:06:08 2008] client connected from 7396[0:0]
[Sat Jan 19 12:06:08 2008] 1 client rule loaded
[Sat Jan 19 12:06:50 2008] client connected from 7396[0:0]
[Sat Jan 19 12:06:50 2008] 1 client rule loaded
----------
# Test 3
## Test 3
#SAVE_VBE_STATE=true
#POST_VIDEO=false
#SAVE_VIDEO_PCI_STATE=false
## result: gdm comes back with password, but terms do not work.
acpi-support file changed. last line in /var/log/acpid file:
[Sat Jan 19 12:06:50 2008] 1 client rule loaded
not yet restarted gdm. first suspend and hit key and come back from suspend and give password. The following two lines in the acpid file:
[Sat Jan 19 13:06:06 2008] client connected from 7396[0:0]
[Sat Jan 19 13:06:06 2008] 1 client rule loaded
Conclusion: suspend does not generate by itself a power-button entry...
Just once standby and come back and type password again; same lines:
[Sat Jan 19 13:08:40 2008] client connected from 7396[0:0]
[Sat Jan 19 13:08:40 2008] 1 client rule loaded
Log out and relogin (which should restart gdm):
[Sat Jan 19 13:08:55 2008] client connected from 10068[0:0]
[Sat Jan 19 13:08:55 2008] 1 client rule loaded
Now suspending machine it is 13:10
Came back from suspend, was asked to type password; terminal came up. Can use CTRL-ALT-F1 etc to go to text terminal, but output looks garbled; every character is an intelligble bitmap, but the screen does change those strange characters when typing into the terminal, which means that the terminal seems alive
[Sat Jan 19 13:11:23 2008] client connected from 10068[0:0]
[Sat Jan 19 13:11:23 2008] 1 client rule loaded
[Sat Jan 19 13:11:41 2008] client connected from 10068[0:0]
[Sat Jan 19 13:11:41 2008] 1 client rule loaded
[Sat Jan 19 13:11:58 2008] client connected from 10068[0:0]
[Sat Jan 19 13:11:58 2008] 1 client rule loaded
[Sat Jan 19 13:27:01 2008] client connected from 10068[0:0]
[Sat Jan 19 13:27:01 2008] 1 client rule loaded
Why do I see a 'client connected'  again at 13:27? There are no events as far as know, except jumping with CTRL-ALT-F1 to tty, giving command 'clear' (which I cannot read of course because of the intelligable characters) to clear the screen and back after giving CTRL-ALT-F9 (actually this is strange as well: why need to use F9 in stead of F7? CTRL-ALT-F7 is not virtually unable to read).
-------------
## Test 4
SAVE_VBE_STATE=true
POST_VIDEO=true
SAVE_VIDEO_PCI_STATE=false
## result:
last line in acpid:
[Sat Jan 19 13:28:19 2008] client connected from 10068[0:0]
[Sat Jan 19 13:28:19 2008] 1 client rule loaded
now logout and login and suspend.
After suspend, pressed a key; system came back, but with blank screen and no action possible: not CTRL-ALT-BKSP, not CTRL-ALT-DEL, not CTRL-ALT-F1, not any key not any mouse, even not numlock changed state.
REbooted system
This are messages in acpid:
[Sat Jan 19 13:37:02 2008] client connected from 11140[0:0]
[Sat Jan 19 13:37:02 2008] 1 client rule loaded
[Sat Jan 19 13:38:07 2008] client connected from 11140[0:0]
[Sat Jan 19 13:38:07 2008] 1 client rule loaded
[Sat Jan 19 13:38:34 2008] client connected from 11140[0:0]
[Sat Jan 19 13:38:34 2008] 1 client rule loaded
[Sat Jan 19 13:39:58 2008] starting up
[Sat Jan 19 13:39:58 2008] 72 rules loaded
[Sat Jan 19 13:40:00 2008] client connected from 4629[107:116]
[Sat Jan 19 13:40:00 2008] 1 client rule loaded
[Sat Jan 19 13:40:16 2008] client connected from 7399[0:0]
[Sat Jan 19 13:40:16 2008] 1 client rule loaded
This seems that all these messages are AFTER the reboot, so that 'started up' does not make complete sense: I believe client was already connected, because 'from 11140' is all the same, while at 13:28:19 (see above), the number was differen.
---------------
## Test 5
SAVE_VBE_STATE=true
POST_VIDEO=true
SAVE_VIDEO_PCI_STATE=true
result: system hang,  cannot do antyhing but reboot after come back from suspend

---------------
## Test 6
SAVE_VBE_STATE=false
POST_VIDEO=false
SAVE_VIDEO_PCI_STATE=true
new kernel 2.6.22-15-generic
## result:
After suspend, pressed a key; system came back, but with blank screen and no action possible: not CTRL-ALT-BKSP, not CTRL-ALT-DEL, not CTRL-ALT-F1, not any key not any mouse, even not numlock changed state.
REbooted system
Relogin
After hibernate, turn on PC Again: both terminal and gnome work perfectly. Gnome asks password as expected.
This are messages in acpid (both before and after suspend):
[Thu Jun 26 23:54:49 2008] starting up
[Thu Jun 26 23:54:49 2008] 72 rules loaded
[Thu Jun 26 23:54:51 2008] client connected from 4928[107:116]
[Thu Jun 26 23:54:51 2008] 1 client rule loaded
[Thu Jun 26 23:55:08 2008] client connected from 7877[0:0]
[Thu Jun 26 23:55:08 2008] 1 client rule loaded
[Thu Jun 26 23:57:24 2008] client connected from 7877[0:0]
[Thu Jun 26 23:57:24 2008] 1 client rule loaded
[Thu Jun 26 23:57:45 2008] client connected from 7877[0:0]
[Thu Jun 26 23:57:45 2008] 1 client rule loaded
[Thu Jun 26 23:58:14 2008] client connected from 7877[0:0]
[Thu Jun 26 23:58:14 2008] 1 client rule loaded
[Fri Jun 27 00:01:12 2008] received event "button/power PWRF 00000080 00000001"
[Fri Jun 27 00:01:12 2008] notifying client 4928[107:116]
[Fri Jun 27 00:01:12 2008] notifying client 7877[0:0]
[Fri Jun 27 00:01:12 2008] client has disconnected
[Fri Jun 27 00:01:12 2008] notifying client 7877[0:0]
[Fri Jun 27 00:01:12 2008] client has disconnected
[Fri Jun 27 00:01:12 2008] notifying client 7877[0:0]
[Fri Jun 27 00:01:12 2008] client has disconnected
[Fri Jun 27 00:01:12 2008] notifying client 7877[0:0]
[Fri Jun 27 00:01:12 2008] executing action "/etc/acpi/powerbtn.sh"
[Fri Jun 27 00:01:12 2008] BEGIN HANDLER MESSAGES
[Fri Jun 27 00:01:12 2008] END HANDLER MESSAGES
[Fri Jun 27 00:01:12 2008] action exited with status 0
[Fri Jun 27 00:01:12 2008] completed event "button/power PWRF 00000080 00000001"

---------------
## Test 7
SAVE_VBE_STATE=false
POST_VIDEO=true
SAVE_VIDEO_PCI_STATE=false
## result:
last line in acpid:
[Fri Jun 27 02:27:40 2008] starting up
[Fri Jun 27 02:27:40 2008] 72 rules loaded
[Fri Jun 27 02:27:42 2008] client connected from 4789[107:116]
[Fri Jun 27 02:27:42 2008] 1 client rule loaded
[Fri Jun 27 02:28:00 2008] client connected from 7737[0:0]
[Fri Jun 27 02:28:00 2008] 1 client rule loaded
action: place machine into suspend
result: machine goes into suspend
action: press one button
result: machine comes back and asks for password. gnome terminal works and comes back in same state. Other terminals with CTRL-ALT-F1 etc are readable characers. GOOD!
[Fri Jun 27 02:28:00 2008] 1 client rule loaded
[Fri Jun 27 02:34:00 2008] client connected from 7737[0:0]
[Fri Jun 27 02:34:00 2008] 1 client rule loaded
[Fri Jun 27 02:34:17 2008] client connected from 7737[0:0]
[Fri Jun 27 02:34:17 2008] 1 client rule loaded
action: place machine into hibernate
result: machine gives some quick messages on a text terminal, then turns off
action: press power button
result: Grub comes up like normal. Linux starts. There is white bar acrross the screen during startup, which indicates the restore of the hibernate. Gnome comes back but asks first for password. gnome terminal works and comes back in same state. Other terminals with CTRL-ALT-F1 etc are readable characers. GOOD!
[Fri Jun 27 02:39:32 2008] client connected from 7737[0:0]
[Fri Jun 27 02:39:32 2008] 1 client rule loaded
[Fri Jun 27 02:40:01 2008] client connected from 7737[0:0]
[Fri Jun 27 02:40:01 2008] 1 client rule loaded
[Sat Jun 28 22:00:18 2008] client connected from 13413[0:0]
[Sat Jun 28 22:00:18 2008] 1 client rule loaded

note: CTRL-ALT-F12 shows a text screen with all white flahsing etters e accent d'acu on a grey background... So the whole screen ful of the letter e. With the accent of course.]
note2: potential issue with full screen with video over flash in firefox. Fullscreen seems to extent beyond the real screensize, sodat about 25% falls ouside the border and is invisible. Note sure if related, might be intermittent. But can even be anything else that is running at this moment.

---------------
## Test 8 - edited 2008-06-28 to test after next reboot, whenever that is.
SAVE_VBE_STATE=false
POST_VIDEO=true
SAVE_VIDEO_PCI_STATE=true
#System comes back with blank screen, CTRL-ALT-F1 etc do not work.
#Possibly, system without immediately after reboot, CTRL-ALT-F1 does not work, althouhg gnome does. Not sure if related. Screen way too big: menu bar does not fit in this screen.

```
No warranty, just my testimony. Might do good, might do bad, whatever for whoever.

---

