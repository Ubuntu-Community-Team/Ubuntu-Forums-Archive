---
title: "Google Earth does not work properly on Intrepid"
date: 2009-06-20
forum: General Help
---

### Post by ali.hammad on 2009-06-20
Hello there,

I installed Google Earth on my laptop ( specifications in attached images ) and when I run it, the graphics does not appear correctly, while on windows xp, its working fine. 

For details please view the attached images.

Thanks

---

### Post by DeMus on 2009-06-20
> **ali.hammad said:**
> Hello there,

I installed Google Earth on my laptop ( specifications in attached images ) and when I run it, the graphics does not appear correctly, while on windows xp, its working fine. 

For details please view the attached images.

Thanks

Do you also have problems with other programs?
Which video card do you have and what driver do you use?
Open a terminal and type (or copy)
```
lspci |grep VGA
```
Please look in System-Administration-Hardware drivers to see if a proprietary driver is installed.

---

### Post by ali.hammad on 2009-06-20
> **DeMus said:**
> Do you also have problems with other programs?
Which video card do you have and what driver do you use?
Open a terminal and type (or copy)
```
lspci |grep VGA
```
Please look in System-Administration-Hardware drivers to see if a proprietary driver is installed.

Apparently I don't get any problem with any other software.

Here is the output of the above mentioned command

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)

And no proprietry driver is installed ( Please see the attachment)

---

### Post by DeMus on 2009-06-20
There are (were?) some problems with drivers for Intel videocards running on Jaunty. I was not aware this also applies to Intrepid.

Can you update the driver, either through Synaptic or directly from the Intel site?

I have been looking around on Google but can't find anything related to your problems. Sorry.

---

### Post by ali.hammad on 2009-06-20
how can I update drivers on Intrepid? and what driver do I exactly need ?

---

### Post by Soul-Sing on 2009-06-20
what is the outcome of:
```
glxinfo | grep direct
```

---

### Post by ali.hammad on 2009-06-20
> **leoquant said:**
> what is the outcome of:
```
glxinfo | grep direct
```

The output is 

direct rendering: Yes

---

### Post by tgalati4 on 2009-06-20
In a terminal:

metacity --replace &
googleearth


Watch for errors and post them.

---

### Post by ali.hammad on 2009-06-20
> **tgalati4 said:**
> In a terminal:

metacity --replace &
googleearth


Watch for errors and post them.


Here is the output

baig@baig-laptop:~$ metacity --replace & googleearth
[1] 12679
Window manager warning: "" found in configuration database is not a valid value for keybinding "switch_to_workspace_2"
Window manager warning: Invalid WM_TRANSIENT_FOR window 0x6400006 specified for 0x6400004 (Initializi).
Window manager warning: Invalid WM_TRANSIENT_FOR window 0x640000f specified for 0x64002db (Start up t).



But GoogleEarth runs automactically and is working a little better than before with this command

But i think i have lost my compiz graphics :P

---

### Post by davidsrsb on 2009-06-20
I always had text corruption with GE on Intrepid with an older Intel graphics chip
A clean install of Jaunty has solved everything

---

### Post by tgalati4 on 2009-06-22
Make a script:

gedit gearth.sh

#!/bin/sh
metacity --replace
googleearth
compiz --replace



Now save it and make it executable:

sudo chmod +x  gearth.sh


Run it:

./gearth.sh

---

### Post by howardf42 on 2009-07-04
> **tgalati4 said:**
> In a terminal:

metacity --replace &
googleearth


Watch for errors and post them.

I have been following this thread having similar problems.  When I ran the above command, I got a different set of error messages, but still unable to run GE.

Here are my errors:
```
~$ metacity --replace & googlearth
[1] 5131
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
Window manager warning: Failed to load theme "IndustrialTango": Failed to find a valid file for theme IndustrialTango

bash: googlearth: command not found

```
The last line notwithstanding, GE is installed, but the call is different and still crashing.

---

