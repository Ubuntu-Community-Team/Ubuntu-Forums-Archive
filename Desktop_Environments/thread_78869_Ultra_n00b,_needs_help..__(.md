---
title: "Ultra n00b, needs help.. : ("
date: 2005-10-19
forum: Desktop Environments
---

### Post by localsly on 2005-10-19
gabe@HOME:~/Desktop$ ./RealPlayer10GOLD.bin
bash: ./RealPlayer10GOLD.bin: Permission denied

[COLOR="Red"]then i tried something else and got...[/COLOR]


gabe@HOME:~/Desktop$ ./RealPlayer10GOLD.bin
./RealPlayer10GOLD.bin: error while loading shared libraries: libstdc++.so.5: ca nnot open shared object file: No such file or directory

today i just started linux, and i find it pretty challenging, but i would still like to use it, so umm, if anyone would like to help me out with installing software in general then it would be very nice..

thanks.

---

### Post by migueljacq on 2005-10-19
[QUOTE=localsly]gabe@HOME:~/Desktop$ ./RealPlayer10GOLD.bin
bash: ./RealPlayer10GOLD.bin: Permission denied

[COLOR="Red"]then i tried something else and got...[/COLOR]


gabe@HOME:~/Desktop$ ./RealPlayer10GOLD.bin
./RealPlayer10GOLD.bin: error while loading shared libraries: libstdc++.so.5: ca nnot open shared object file: No such file or directory

today i just started linux, and i find it pretty challenging, but i would still like to use it, so umm, if anyone would like to help me out with installing software in general then it would be very nice..

thanks.[/QUOTE]

Easiest way to install new software is using Synaptic:

System >> Adminstration >> Synaptic Package Manager (might have to enter your password)

Not sure about Realplayer. Looks like it is looking for the shared library: How did you install Realplayer?

---

### Post by localsly on 2005-10-19
okay, well i have gotten far enough to notice that its giving me a permission denied.. is there anyways to be aproved? cause i would like to install this program.

---

### Post by migueljacq on 2005-10-19
[QUOTE=localsly]okay, well i have gotten far enough to notice that its giving me a permission denied.. is there anyways to be aproved? cause i would like to install this program.[/QUOTE]

try typing sudo followed by the rest. you'll probably have to enter your password if it asks. 

i.e  sudo ./RealPlayer10GOLD.bin 

not sure what the *.bin files do. Are they supposed to be executable? bash scripts? anyone know?

---

### Post by migueljacq on 2005-10-19
[QUOTE=localsly]cause i would like to install this program.[/QUOTE]

have you not installed it?

i think the easiest thing for you is to type this into the terminal:

sudo apt-get install realplayer

then

killall gnome-panel

then look at Applications >> Sound and Video >> Realplayer

---

### Post by heimo on 2005-10-19
[quote=localsly]okay, well i have gotten far enough to notice that its giving me a permission denied.. is there anyways to be aproved? cause i would like to install this program.[/quote]

Could you give more details? Error message? Did you install libstdc++5?
```
sudo apt-get install libstdc++5

```

---

