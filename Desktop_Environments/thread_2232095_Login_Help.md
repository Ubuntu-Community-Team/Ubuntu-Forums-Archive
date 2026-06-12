---
title: "Login Help"
date: 2014-06-29
forum: Desktop Environments
---

### Post by rschanzenbacher on 2014-06-29
Hi again! I'm running Ubuntu 14.04LTS with propitiatory NVIDIA drivers. My question is, when I boot up is it normal for a login screen to either freeze or be a black screen for 20 seconds or more? If not, WHY is it doing this?  Sorry if im not in the right Thread, I'm a n00b at this. ;)

---

### Post by Dreamer Fithp Apprentice on 2014-06-29
I've had this a lot on systems that seemed ok otherwise, so my GUESS would be yes. For me the cursor just sits in the upper left corner for a while as if the leprachaun inside that makes it all go was pausing to take a swig out of his jug before getting down to business. That's my theory and I'm sticking to it. But I'll be interested to see what wiser ones believe.

---

### Post by grahammechanical on 2014-06-29
Do you really mean the login screen? Or are you referring to the screens that we see before the login screen appears. There is an important difference.

It is not a simple task to load to a desktop environment. From the Grub menu the Linux kernel starts to load. The video is very low resolution so a display server is loaded (it is called X) and the Xserver determines the correct screen resolution and switches to a better video driver (open source or proprietary). As we do not like seeing the normal Linux messages a splash screen is provided by something called Plymouth. But we need a display manager for the desktop environment. And so the Light Display Manager (LightDM) takes over and presents a greeter that is the login screen with a background. After login the switch is made to a window compositor (Compiz) to manage the User Interface (Unity) 

The transitions are not smooth and we notice this fact. It is one of the things that it is hoped will be improved when ubuntu makes the switch to the Mir display server with the release of 16.04. The X server will be gone. So, will LightDM and Compiz. 

This is not a complete description of what happens during the loading of Linux/Ubuntu but it is the reason why we see black screens and purple screens and then black screens and then a login screen.

Regards.

---

### Post by rschanzenbacher on 2014-06-29
Thank you for the facts about my leprechaun being lazy! :p Though I've heared that mir might be in 14.10.

---

