---
title: "[SOLVED] the composite extensions is not available??."
date: 2007-12-17
forum: Desktop Environments
---

### Post by LostMagix on 2007-12-17
i just put Ubuntu 7.10 on a second system,

i put in the command

sudo apt-get install compizconfig-settings-manager

and it worked fine

when i go to enable my desk top effects it says

"the composite extensions is not available"

im still really new to linux, i know this is something really simple i am missing

---

### Post by chadridesabike on 2007-12-17
try using synaptics package manager to ensure you have ALL of the files installed that are required.

---

### Post by LostMagix on 2007-12-17
> **chadridesabike said:**
> try using synaptics package manager to ensure you have ALL of the files installed that are required.

how do i know what files i need?

---

### Post by avik on 2007-12-17
Do you have your graphics card drivers installed?  What graphics card do you have?

---

### Post by LostMagix on 2007-12-17
i do, its a ATI radeon 9550XL 256MB

as far as i know its working fine, its enabled and in use, and the 3D and 2D accelerator is running

---

### Post by chewearn on 2007-12-17
If you run:
```
glxinfo | grep rendering
```

do you get "direct rendering: Yes" ?

---

### Post by LostMagix on 2007-12-17
```
chris@LostMagix:~$ glxinfo | grep rendering
direct rendering: Yes
chris@LostMagix:~$ 

```

---

### Post by sirdilznik on 2007-12-17
There may be a graphical way to do it, but here's the command line way.  Check your /etc/X11/xorg.conf to see if the composite extension has been enabled.  First backup your file ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```  Then open and edit the file ```
sudo gedit /etc/X11/xorg.conf
```Note:  If you do not have gedit or prefer a different editor substitute "gedit" with your preferred editor in the previous command.  Look for the following lines in the file ```
Section "Extensions"
    Option         "Composite" "Enable"
EndSection
```
It's a long file, I know.  If the section doesn't appear in the file then copy and paste it into the file wherever you want (at the end will be fine).  If it's commented out (a "#" appears at the beginning of each line) simply uncomment it (remove the "#" symbols).

Then save and exit.

If anything goes wrong and you are unable to access X after rebooting or restarting X, then you can always revert to the original file from the command line: ```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```

Hope that helps.

---

### Post by erfahren on 2007-12-17
LostMagix -- nevermind about editing the xorg.conf file

It *should* read that the composite extension is disabled ( or "0" )

now, if you have already enable the restricted driver just do:
```

sudo apt-get install xserver-xgl

```
restart X (Ctrl+Alt+Backspace) and you should be able to enable the desktop effects

---

### Post by LostMagix on 2007-12-17
> **erfahren said:**
> LostMagix -- nevermind about editing the xorg.conf file

It *should* read that the composite extension is disabled ( or "0" )

now, if you have already enable the restricted driver just do:
```

sudo apt-get install xserver-xgl

```
restart X (Ctrl+Alt+Backspace) and you should be able to enable the desktop effects

that did it, thank you all very much!!!!

have a good night

---

### Post by erfahren on 2007-12-17
glad that worked out fairly painlessly!

note: you can mark this thread as "Solved" by going to the "Thread Tools" above the first post.

---

