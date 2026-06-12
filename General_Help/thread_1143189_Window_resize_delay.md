---
title: "Window resize delay"
date: 2009-04-29
forum: General Help
---

### Post by dougalkerr on 2009-04-29
Dunno if anybody else has experienced this... when I drag a window to resize it and let go of the drag, the window takes about 4 seconds to come back to normal focus. I have the latest driver for the ALPS touchpad on my Dell Studio 1537 with ATi HD 3400 series graphics.

---

### Post by NeilMonday on 2009-04-30
BUMP.

I have this same problem when resizing windows or maximizing them. I have a quad core with 4GB of ram and an ATI HD 2400.

EDIT: also running Ubuntu 9.04 x64. Same problem occurred on 8.10 x64.

---

### Post by s3lekta on 2009-05-03
bump, same problem here

---

### Post by DeMus on 2009-05-03
> **NeilMonday said:**
> BUMP.

I have this same problem when resizing windows or maximizing them. I have a quad core with 4GB of ram and an ATI HD 2400.

EDIT: also running Ubuntu 9.04 x64. Same problem occurred on 8.10 x64.

Do you by any chance have compiz installed and running? Is there a "special effect" which is causing this?

---

### Post by ZaaBI_AlonSo on 2009-05-03
Have the same problem with ati hd 3650

Delay on maximize/unminimize
on resise and on some apps like ktorrent


no problem had with 8.10



if anyone has a solution please help

the problem with compiz is really anoying

without compiz is really better

---

### Post by dougalkerr on 2009-05-11
Hey Guys n' gals I have posted the question on the Compiz forums too. I will let you know if I get any solutions...

---

### Post by s3lekta on 2009-05-12
> **dougalkerr said:**
> Hey Guys n' gals I have posted the question on the Compiz forums too. I will let you know if I get any solutions...

thanks

---

### Post by PhydeauxSpeaks on 2009-05-12
I can't get resize to work at all since upgrading to 9.  Only have fullscreen and whatever smaller window the program chooses, no in between sizes and dragging doesn't work at all.

---

### Post by dougalkerr on 2009-05-30
I have nothing new to report on this problem. I have set my Visual Effects to 'None' so that I do not have the resize delay. It was getting too annoying.
I also reinstalled Ubuntu and played around with installing/reinstalling the graphics card driver - didn't make the slightest bit of difference to the resize effect delay. I tried to follow all suggestions that I could find but, they were either too complex to follow for a mere mortal like me that is used to installing operating systems and fault finding applications (mostly in Windows, unfortunately) or the suggestions did not work...

On the plus side - I used to use Envyng to install the ATI driver for my machine but, when Jaunty came out there was not an install available from the Envy website - now there is.
Albert has made Envyng available for Ubuntu 8.04 onward and it works just fine. No more faffing about trying to follow install instructions from ATI or the Ubuntu help page (sorry guys, you do an excellent job otherwise). It was actually available in Synaptic - wow!!
Once Envy is installed you have to click on the application in the newly created 'System Tools' sub-menu to the 'Applications' menu to activate the driver then reboot. All is well.
I usually check the graphics using the Sky Rocket screensaver. I test the Appearances 'Visual Effects' setting of 'None', 'Normal' and 'Extra' and then open the screensaver settings applet to select Sky Rocket and right-away I found that I only had two choices, None or Extra. Normal would upset the Window Manager controls and even disable or freeze things forcing a reboot. On extra I had the resize delay from minimized windows but, on None I have no problems. My screensaver runs well and no other visual problems at all. In fact the system runs fast with None selected. I do not need the Extra effects even if they do look pretty. I would keep them if the delay bug was not prsent as I like being able to swap desktops using the cube but, the delay is just too damn annoying as I said.
Phew!! well hope someone enjoys reading this. If anyone knows of an alternative to Compiz it might prove interesting...
Cheers for now.

---

