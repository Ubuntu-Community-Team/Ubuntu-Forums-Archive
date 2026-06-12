---
title: "GKrellM not working properly"
date: 2008-12-04
forum: General Help
---

### Post by ozguitarplayer on 2008-12-04
hi,
Kubuntu,
I had to reinstall Kubuntu.

I used to have GKrellM and lm-sensors installed and GkrellM would show (as well as other info) the temp of drives and fan speeds, since I reinstalled I cannot get the temps and fan speed working, 

GkrellM says the sensors aren't detected, lm-sensors is definitely installed, I've even reinstalled it...

..anyone got any ideas where the problem might lie?

---

### Post by john.nicholls on 2008-12-04
Have you run ```
sudo sensors-detect
``` ?

---

### Post by ozguitarplayer on 2008-12-04
hey John, I hadn't run that mainly because I'm new to Linux etc...though I'm keen to learn.
I did run ...sudo sensors-detect all went well then I got...

To load everything that is needed, add this to /etc/modules:
#----cut here----
# Chip drivers
w83627ehf
#----cut here---    

where would I add this if I did it manually, do I look for /etc/Modules in Root?
so I left it and went with...

Do you want to add these lines automatically? (yes/NO)yes
to which I typed yes and got


....nigel@Master:~$ 

and didn't know what to do next..do I just type ..exit cause I have checked and GKrellM still isn't showing temp or fan....

---

### Post by taurus on 2008-12-04
Did you shutdown and restart gkrellm again?  Then, click on gkrellm window with the right button and then Configuration -> Builtins and see if anything shows up in there.

---

### Post by ozguitarplayer on 2008-12-04
thanks taurus, yes I did show down and restart GKrellM and no change, and I don't have a builtins when I right click on the GKrellM panel only configuration theme and quit

should I have started the computer?

---

### Post by adult swim on 2008-12-04
you need to click on configuration when that menu pops up and then look for builtins.  are you using a dell computer?

---

### Post by ozguitarplayer on 2008-12-04
hey adult swim, ok I was being daft of a moment, i was looking at builtins without realising it, I get to senors where temp, fan and voltages are however they no longer list the choices of fans temps etc that can be added to the screen display....used to be there before I reinstalled Kubuntu...and no it's not a dell..

---

### Post by adult swim on 2008-12-04
when you run ```
sensors
``` from a terminal does it return any results?

---

