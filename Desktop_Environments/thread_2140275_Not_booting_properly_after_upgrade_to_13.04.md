---
title: "Not booting properly after upgrade to 13.04"
date: 2013-04-29
forum: Desktop Environments
---

### Post by dizymac on 2013-04-29
[COLOR=#333333][FONT=Ubuntu]Hi everyone![/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]I recently upgraded my Intel i3 3.1ghz box running Ubuntu 64bit 12.10 to 13.04.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]However it doesn't appear to want to boot with the new 3.8.0-19 kernel without going through the recovery boot option and selecting resume normal boot.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]But selecting the older 3.5.0-27 kernel in grub boots fine (appears to run a little slower than before?).[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]I've taken a couple of photos of errors at boot:[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu][https://dl.dropboxusercontent.com/u/3200610/ubuntu%20error1.JPG](https://dl.dropboxusercontent.com/u/3200610/ubuntu%20error1.JPG)[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu][https://dl.dropboxusercontent.com/u/3200610/ubuntu%20error2.JPG](https://dl.dropboxusercontent.com/u/3200610/ubuntu%20error2.JPG)[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]Once it has booted I've also seen some errors reported from compiz and the swap.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]Does anyone know how I can resolve this? I'd like to get the machine running again as I use it as my home server and for some front end web work.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]Cheers[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]David[/FONT][/COLOR]

---

### Post by dizymac on 2013-04-29
On further reading this appears to be related to a bug in the kernel for the gpio conflict: 
[URL="https://bugzilla.kernel.org/show_bug.cgi?id=44991"]
https://bugzilla.kernel.org/show_bug.cgi?id=44991[/URL]

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1078289](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1078289)

By the sounds of this the 3.8.x kernel should have been patched?

---

