---
title: "Login loop - White screen - Font error"
date: 2020-03-26
forum: Desktop Environments
---

### Post by ndaidong on 2020-03-26
Hi guys,

I cannot use Ubuntu on my new laptop (MSI Modern 14A10RB) anymore after trying to switch to Gnome classic.
At first, I've installed Ubuntu 20.04 pre version, but it seems not stable for daily usage. I'm software developer who work on the *nix systems, the regular errors are not problem, but it stuck at login window. Pressing Ctrl + Alt + F4 and doing some stuff from terminal doesn't help.
Then I installed Xubuntu 19.10, and install gnome-session to get the classic Gnome layout (with the smarter dash). The same error happened again. Sometimes, it fall in the login loop. Sometimes I can login, but a few system texts do not appear correctly, and suddenly, a white screen shows as below: 



Do these issues relate to the hardware. How to fix them?

Thanks.

---

### Post by u666sa on 2020-03-28
I had something similar, but not exactly the same.  After install I'd get GDM background but without login screen.  Turns out it showed second monitor on my laptop, the display port output, instead of LCD.  The solution was to press space and enter password and then press enter.  That logged me into the system.  Then I had to move mouth to the right until I see it and right click and configure display, in particular monitor.  After that gnome desktop worked the way it should, but GDM still did the same.  To fix that issue I had to copy monitors.xml from profile into global GDM profile directory.

Possible solution for you could be this - sudo apt install lightdm

This will install light and possibly let you login.

Alternatively, you can hook up an external monitor or TV to your laptop to see what's happening on your display port. 

P.S.  What video card do you have?  I have GeForce 420M, and I'm limited by CUDA 8.0 with that particular card, that in turn requires clang 4 and g++ 4.7, so I'm stuck on Debian based systems.  You seem to be going for the latest and unstable.  I used to be like you, I used to run Fedora for several months, until one day it stopped working after updates, 390xx graphic driver issue after kernel update.  Then I realized something, I don't have a new system, I need to run CUDA and in order to run CUDA I need certain dev tools and that automatically limits my scope of distributions, thus Ubuntu 18.04 LTS.  Bleeding edge is not always good, besides your Ubuntu versions are not bleeding edge Linux, neither is Fedora.  The most bleeding edge is Arch based distros, Manjaro for example.  I'd run it, it's nice, but no dev no needed dev tools for me to have CUDA working..  My suggestion is not to go with distros that end their life after about a year, like you have right now, and go for either a rolling release or LTS.  Realize you are a beta software tester at this point.  Updates come in, things sometimes break, that's your situation.  (That's every Fedora user out there, lul.)  Run towards LTS.  Because it's time consuming to install Linux and configure everything. ):P

---

### Post by ndaidong on 2020-04-01
hi u666sa
Thank you for your response. I've installed lightdm and reconfigure to use it as default display manager however that doesn't help too.
My laptop is just released few months ago. It has a MX250 graphic card. As an AI developer, I work with pytorch/tensorflow so CUDA, cuDNN are important part. I've installed CUDA 10.2, nvidia driver 440, and downgrade to gcc/g++7 to install other nvidia tools.
Now I switched to Fedora 31 and looks like everything works well.

---

