---
title: "connecting laptop to monitor"
date: 2012-06-19
forum: Desktop Environments
---

### Post by nathanv221 on 2012-06-19
**[SOLVED]**hey, so what i've done is connect my laptop (Dell Precision M4500) with a VGA 15 cable to my monitor.  it works fine with windows, and worked fine in the CD trial of Ubuntu 12.10 (at least with mirror display) but after installing Ubuntu 12.10 it no longer works. the laptop is fine but the other monitor is black. 

the only fix i have attempted was using the display settings to "Detect Displays". but it did not work.

any ideas or other threads that solved this problem?

---

### Post by mr.suchy on 2012-06-19
Hi

What graphic card do you have ? what kind of drivers, official ?

---

### Post by nathanv221 on 2012-06-19
hey mr. suchy im running a nvidia Quadro FX 880M

---

### Post by sudodus on 2012-06-19
12.10 is in early alpha testing stage. You cannot expect that everything is working yet, but it would be valuable if you file a bug about your problem.

I suggest that you try the still new present version 12.04 LTS.

What graphics driver are you using, nouveau, a built-in proprietary driver or an nvidia driver downloaded from the manufacturer's web site?

---

### Post by nathanv221 on 2012-06-19
problem solved! 
what i did was 
open NVIDIA settings,
                go to the dash home screen and type NVIDIA, 
                open "NVIDIA X Server Settings"

 *server settings should open*

 then in the left hand collom of the screen click "X Server Display Configuration".

 then in the right hand side of the screen click the box labled "disabled"

go to the "configuration:" setting select "twin view" 

in the "Resulution:" setting select auto. 

press the button labled "save to x Congiguration File" 

*Save X Configuration" menu should open*

check the box beside "merge with existing file"

hit "save"

*Save X Configuration" menu should close*

on the "NVIDIA X Server Settings" menu click "apply"

then a menu will appear on your other monitor with a countdown click yes. if the countdown reaches 0 and the screen turns back off click apply again.

---

