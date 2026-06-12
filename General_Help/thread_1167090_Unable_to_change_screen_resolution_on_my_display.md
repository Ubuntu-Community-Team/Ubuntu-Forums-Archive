---
title: "Unable to change screen resolution on my display"
date: 2009-05-22
forum: General Help
---

### Post by kinngg on 2009-05-22
I was first messing around with Kubuntu but when I changed it from gdm to kdm my login screen did not appear, so I changed it back to gdm. After that when I login to my ubuntu I can't edit or change my screen resolution. Usually I can just click on display and my nvidia settings would show but now, everytime I open the nvidia this shows up: 

You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. 

And when I run the command in the terminal this shows up: 

chilin@chilin-laptop:~$ sudo nvidia-xconfig

Using X configuration file: "/etc/X11/xorg.conf".

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Device section "Configured Video Device" must have a Driver
                  line.

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'


And my desktop effects seems to be unabled. I think something is not recognizing my video card.

---

### Post by Kareeser on 2009-05-22
Can you type this into the console and upload the file to your reply?

```
cat /etc/X11/xorg.conf > ~/Desktop/xorg-config
```

---

### Post by kinngg on 2009-05-22
Nevermind! Problem solved when I reinstalled my hardware drivers! :) Thanks though

---

