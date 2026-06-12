---
title: "Problem loading install.exe in Wine"
date: 2008-04-29
forum: Desktop Environments
---

### Post by gewitty on 2008-04-29
Just started to use Wine and am trying to install TrackLogs, which is rated as a Gold app which runs with no bugs. However, when I try to run the install.exe from the CD (specifying Wine as the application to open it), nothing happens. I also tried to run it from Terminal by cd to the CD drive then entering 'wine setup.exe'. This resulted in the error message shown below.

dave@dave-desktop:/media/cdrom1$ wine setup.exe
preloader: Warning: failed to reserve range 00000000-60000000
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
wine: could not load L"C:\\windows\\system32\\setup.exe": Module not found
dave@dave-desktop:/media/cdrom1$ err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report

Is this something I've missed in the Wine setup, or is there some other problem?

---

### Post by renzokuken on 2008-04-29
before you did any of this did you run

```
winecfg
``` from the terminal, it sets up wine and creates the necessary folders/configuration files

---

### Post by gewitty on 2008-04-29
I ran Wine config from the Wine menu initially. I just tried it again, using Terminal and got the same response:

dave@dave-desktop:~$ winecfg
preloader: Warning: failed to reserve range 00000000-60000000
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report

---

### Post by dillthedog on 2009-08-28
I got quite excited when I saw it marked as 'Gold' too. tracklogs is a bit of a killer app for me and was almost a factor in going MS in getting a laptop. I'd really like to get it to work. Here's what I get:

[INDENT][FONT="Courier New"]
dougie@osprey:/media/cdrom$ wine setup.exe 
Usage:
  Install a product:
    msiexec {package|productcode} [property]
    msiexec /i {package|productcode} [property]
    msiexec /a package [property]
  Repair an installation:
    msiexec /f[p|o|e|d|c|a|u|m|s|v] {package|productcode}
  Uninstall a product:
    msiexec /x {package|productcode} [property]
  Advertise a product:
    msiexec /j[u|m] package [/t transform] [/g languageid]
    msiexec {u|m} package [/t transform] [/g languageid]
  Apply a patch:
    msiexec /p patchpackage [property]
    msiexec /p patchpackage /a package [property]
  Modifiers for above operations:
    msiexec /l[*][i|w|e|a|r|u|c|m|o|p|v|][+|!] logfile
    msiexec /q{|n|b|r|f|n+|b+|b-}
  Register a module:
    msiexec /y module
  Unregister a module:
    msiexec /z module
  Display usage and copyright:
    msiexec {/h|/?}
NOTE: Product code on commandline unimplemented as of yet
[/FONT][/INDENT]

---

