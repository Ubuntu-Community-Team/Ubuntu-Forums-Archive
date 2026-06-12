---
title: "Can boot into &quot;Ubuntu Classic&quot; but not Unity"
date: 2011-04-29
forum: Desktop Environments
---

### Post by KStorm on 2011-04-29
At GDM, when I attempt to log into the Ubuntu desktop (the one with Unity), I get nothing more than the GDM background screen and movable mouse pointer--nothing after that.  I have to perform an Alt+SysRQ+REISUB to restart the system every time.

Selecting "Ubuntu Classic" poses no problems as of yet.  Any solutions?

---

### Post by JDorfler on 2011-04-29
What's your video card and do you have the proprietary drivers installed?  I've got a Radeon HD 6970 and had to install FGLRX via Synaptic, then go to the terminal and use "sudo aticonfig --initiate -f" then "sudo reboot now".  Unity came right up.

---

### Post by KStorm on 2011-04-29
The video is onboard Radeon HD 4200 (512MB) and the proprietary drivers have just been installed.  Unity boots up fine for the time being, but the bootsplash resolution has been reduced to something other than 1680x1050 (which I suppose is standard).  I also cannot run aticonfig from the terminal because the option 'initiate' is unrecognized.

'aticonfig: unrecognized option '--initiate'
aticonfig: parsing the command-line failed.'

---

### Post by Kazuki Mishima on 2011-04-29
> **JDorfler said:**
> What's your video card and do you have the proprietary drivers installed?  I've got a Radeon HD 6970 and had to install FGLRX via Synaptic, then go to the terminal and use "sudo aticonfig --initiate -f" then "sudo reboot now".  Unity came right up.

JDorfler: I'm having the same problem as the original poster, I have some sort of Radeon card (forget which model exactly) and I tried your solution, but when I tried the "sudo aticonfig --initiate -f" command, all I got was this error:
```
aticonfig: No supported adapters detected
```

So I'm not sure where to go from there...

---

### Post by JDorfler on 2011-04-30
Go [here]("http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Installing_the_drivers_manually") and replace Maverick with Natty for the instructions.

---

