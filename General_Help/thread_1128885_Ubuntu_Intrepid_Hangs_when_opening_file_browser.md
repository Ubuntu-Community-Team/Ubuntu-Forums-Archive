---
title: "Ubuntu Intrepid Hangs when opening file browser"
date: 2009-04-18
forum: General Help
---

### Post by abhiram7 on 2009-04-18
Hi 

I have ubuntu intrepid installed in my amd 64 bit, 3 gig RAM comp. The problem is ubuntu freezes very often when i open the file browser to save any file. I wait for 10-15 mins still nothing happens leaving me only the option of rebooting the system. Can u guys help me in fixing this??? its getting worse every day....

thanks

---

### Post by uxen on 2009-04-18
Did you install the proper graphic driver?

---

### Post by juancarlospaco on 2009-04-18
Reinstall File Browser.

---

### Post by abhiram7 on 2009-04-18
Hi 

reinstalled nautilus. says it is already in the latest version.

still the problem exists. :(.

and the graphic dirver i am using the one that is recommended hardware driver. and moreover my videos and graphics are ruuning very well, so i guess the driver installed is fine. Are there any direct way (as a command)  to check for the proper installation of drivers??

---

### Post by uxen on 2009-04-18
In Terminal  **glxinfo | grep -i "direct rendering"**

The answer must be "**yes**"

---

### Post by abhiram7 on 2009-04-18
thanks... yeah i said yes..

---

### Post by juancarlospaco on 2009-04-18
[Try this one.]("apt:/thunar")

---

### Post by abhiram7 on 2009-04-18
thanks a lot. installed thunar and made it default now it  to works fine.

---

### Post by abhiram7 on 2009-04-19
hi

thunrar seems to work fine for day, but ubuntu again is freezing when trying to save a download file in mozilla. is it really the problem of file browser or am i getting it wrong.

---

