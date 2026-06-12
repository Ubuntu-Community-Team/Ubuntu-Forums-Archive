---
title: "Out of Range Error..."
date: 2007-03-11
forum: Desktop Environments
---

### Post by NightriderXP on 2007-03-11
I recently downloaded ubuntu-6.06.1-desktop-i386.iso and burned it to CD.  I did a checksum on the downloaded file and it passed.  I also used Ubuntu's own Testing utility to make sure the copy burned to CD was good...

I tried booting to Ubuntu 6.06 and after it installed drivers, etc, the Out of Range error message appears in the middle of the screen, followed shortly after by the sound of the OS booting up.  But I never see anything other than the Out of Range error message...

My PC Specs:
[LIST][*]2800+ AMD
[*]1 GB RAM
[*]160 GB HDD Master - 9 GB Free Space on C partition
[*]120 GB HDD Slave[/LIST]

[img]http://img398.imageshack.us/img398/3663/dontknow6sf.gif[/img]

---

### Post by taurus on 2007-03-11
You forgot to include the make and model of your graphic card and your monitor.  Do you see a console if you press <Ctrl><Alt>F2, after the sound?

---

### Post by NightriderXP on 2007-03-11
Thanks for the quick reply taurus...

When I press Ctrl+Alt+F2 after the sound, it takes me to the ubuntu@ubuntu:~$ prompt.  When exiting, there is an Failed error next to Unmounting local filesytem...

Here are are additional PC details that I ommited in my inital message:

[list][*]Rage 128 Pro (5446) [Display adapter]
[*]ViewSonic VP2130 LCD
[*]Plextar DVDR PX-740A
[*]Sony CD-RW CRX225E
[*]ASUSTeK Computer INC. A7N8X2.0 REV 1.xx mobo[/list]

[img]http://img505.imageshack.us/img505/7136/munky24nf.gif[/img]

---

### Post by taurus on 2007-03-11
At that prompt, run

```
sudo dpkg-reconfigure xserver-xorg
```
Use **vesa** as a driver for your graphic card.  When done, press <Alt>F7 and then restart X again with <Ctrl><Alt>Backspace.  Do you see anything now?

---

### Post by NightriderXP on 2007-03-11
Ok, I entered the Vesa driver in the configuration but wasn't sure when I was supposed to press F7 or Ctrl+Alt+Backspace, so I used all the default settings and completed the configuration process.  It returned me to the ubuntu prompt.  F7 alone did nothing, so I tried using Ctrl+Alt+F7 and it returned me to the Out of Range error.  I pressed Ctrl+Alt+Backspace and it returned me to the ubuntu prompt.  I tried repeating the process trying the F7 and Ctrl+Alt+Backspace suggestions while in configuration, but it didn't seem to help.  So I'm a bit unsure of what you meant to do next at this point...

I did manage to get the display of 3 additional errors that I have seen occassionally when attempting to boot previouslly.  I don't know if they add anything to what we have discussed so far or if they are a cause or effect of another problem, so I will let you be the judge:

[list][*]hub_port_status failed err=-110
[*]connect-debounce failed port 3 disabling
[*]cannot disable port 3[/list]

[img]http://img398.imageshack.us/img398/3663/dontknow6sf.gif[/img]

---

### Post by NightriderXP on 2007-03-11
Wow this is a busy forum.  It doesn't take much for a topic to get lost in the shuffle...

So am I at a point where I need to give up or does someone have any other ideas?  I've appreciated the courteous and timely assistance so far, so hopefully there is an answer/solution to resolving this problem.  I really would like to get this to work...

[img]http://img398.imageshack.us/img398/3663/dontknow6sf.gif[/img]

---

