---
title: "Update ATI-drivers?"
date: 2009-03-12
forum: General Help
---

### Post by Lingonet on 2009-03-12
Hello!

I have a question regarding drivers.
I have a very laggy/hacky computer. Nothing with much graphics works without lag/hack. I'm thinking that it might be the graphic card which is broken, but on a few forums they say that it might be the drivers.
Now, how do I update the drivers in Ubuntu? I have a Ati Radeon X800 graphic card. I have heard of crashes when people update their cards in Ubuntu, so I'm asking here first.
Is it safe? Will my computer crash?

Answers appreciated!

Thank you!

---

### Post by Neo_The_User on 2009-03-12
Here. Follow my guide located here.

[http://ubuntuforums.org/showthread.php?t=1091804&page=2](http://ubuntuforums.org/showthread.php?t=1091804&page=2)

---

### Post by Lingonet on 2009-03-12
Here is the log. I have a Radeon X800, like said.

```
henrik@Femmansbuntu:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: DRI R300 Project
OpenGL renderer string: Mesa DRI R300 20060815 AGP 4x x86/MMX/SSE2 TCL
OpenGL version string: 1.3 Mesa 7.2

Segmenteringsfel

```

---

### Post by Neo_The_User on 2009-03-12
The GPU doesn't matter. they all use the same closed source driver as long as its past the 9250 AGP 8X card so don't give me the attitude if you want my help. btw i've seen fglrxinfo throw out mesa info. it means direct rendering isn't being used. most likely you are using a custom kernel. if so, you'll need to follow my out of date guide.

[http://ubuntuforums.org/showthread.php?t=1036456](http://ubuntuforums.org/showthread.php?t=1036456)

Half the git repos aren't even needed anymore.

---

### Post by Lingonet on 2009-03-12
> **Neo_The_User said:**
> The GPU doesn't matter. they all use the same closed source driver as long as its past the 9250 AGP 8X card so don't give me the attitude if you want my help. btw i've seen fglrxinfo throw out mesa info. it means direct rendering isn't being used. most likely you are using a custom kernel. if so, you'll need to follow my out of date guide.

[http://ubuntuforums.org/showthread.php?t=1036456](http://ubuntuforums.org/showthread.php?t=1036456)

Half the git repos aren't even needed anymore.

What do you mean with attitude?

That was a very long guide! Can you be more specific what will happen if I follow it and what is my goal? The program is needed to see what version of the drivers I have, right? When I downloaded it, Catalyst control center was installed, and it told me to update the drivers by entering a code. Should I do this?

---

### Post by Neo_The_User on 2009-03-12
Well the drivers are installed (not into the kernel based on my observations) most likely due to a custom kernel. Try installing DKMS first and reboot. Make sure you run sudo aticonfig --initial -f before you reboot after you install DKMS. Disregard that thing about the attitude. Misread it. I skim through posts without fully reading them.

---

### Post by Yellow Pasque on 2009-03-12
You currently have the open-source radeon driver installed. This driver is good for 2D performance and stability. If you want to focus on 3D performance, you can try installing ATI's proprietary closed-source driver: [http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide)

---

### Post by Neo_The_User on 2009-03-12
> **Temüjin said:**
> You currently have the open-source radeon driver installed. This driver is good for 2D performance and stability. If you want to focus on 3D performance, you can try installing ATI's proprietary closed-source driver: [http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide)

Yeah Mesa is pretty good but if you have a slow CPU with bad 3dnow! support such as the old AMD Athlon XPs, you don't want Mesa.

---

