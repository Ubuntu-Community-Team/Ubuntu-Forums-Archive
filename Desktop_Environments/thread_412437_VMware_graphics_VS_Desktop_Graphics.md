---
title: "VMware graphics VS Desktop Graphics"
date: 2007-04-18
forum: Desktop Environments
---

### Post by bothosnx on 2007-04-18
I'm just managed to installed ubuntu on VMware. I'm new on Linux and also my first time on VMs. I noticed the resolution on Ubuntu VM only goes up to 1024X768. This is not so good cause i'm used to something higher than this on windows. Is this limited by VM or Ubuntu? i have GT6600 card not sure if it's how it's picked up on VM.

Can i also hi-jack this thread to ask another Q. Can one boot to complete bash (non X window) on ubuntu v6.10. I know you can load terminal but would like the real console. Well on the manual it says press CNTRl-ALT-F1 to load console. I did this both while on terminal & on desktop with no response.

---

### Post by yeleek on 2007-04-18
Vmware i'm afraid won't pass your graphics card to the vm environment.  You will be using a vmware based graphics driver within the virtual machine.  Same as if you were running a virtual windows environment within a vmware machine.

Ta

---

### Post by Jhongy on 2007-04-18
^^ What he said. Ubuntu will display at whatever resolution you need (once you have the correct driver installed).

If you're using VMWare workstation or Server, install the VMWare tools... this will enable you to select a higher resolution. However, the performance will *not* be the same as running it directly on your hardware.

---

### Post by Renegade of Funk on 2007-04-18
Open the file: /etc/X11/xorg.conf

Search for the Section: Screen

there you can alter this sections:
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection

to the modes you like.
Save the file and you are done.

After you have changed the file and saved it you can press CTRL+ALT+BACKSPACE (to end the current X window session) BEWARE: Close all applications first and save all files. Else they will be lost :P

Cheers.

---

