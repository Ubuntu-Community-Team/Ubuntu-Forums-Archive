---
title: "Steam not working on ubuntu 16.04 lts 64-bit"
date: 2016-04-16
forum: Gaming &amp; Leisure
---

### Post by frdd7528 on 2016-04-16
Steam when i click on it does the startup animation on my side then closes, i do a bit of reading and someone says to type "steam" into the command terminal and i do so and this is the output:

Running Steam on ubuntu 16.04 64-bit
STEAM_RUNTIME is enabled automatically
Installing breakpad exception handler for appid(steam)/version(0)
libGL error: unable to load driver : nouveau_dri.so
libGL error: driver pointer missing
libGL error: unable to load driver : nouveau
libGL error: unable to load driver : swrast_dri.so
libGL error: unable to load driver : swrast
help anything i have done wrong please tell me I will be happy to tell you

---

### Post by howefield on 2016-04-16
Hello and welcome to the forum.

Thread moved to the "*Gaming & Leisure*" forum for better support.

---

### Post by alex_32 on 2016-04-16
Hello,

Here [http://askubuntu.com/questions/635851/error-in-installing-steam-on-ubuntu-15-04](http://askubuntu.com/questions/635851/error-in-installing-steam-on-ubuntu-15-04). It has the command how to start steam from the terminal so it works, and if needed instructions on how to create a script.

---

### Post by MikeCyber on 2016-04-17
you need to install the proprietary Nvidia drivers

---

### Post by oscarivera9 on 2016-04-17
> **MikeCyber said:**
> you need to install the proprietary Nvidia drivers
Yup, try installing proprietary Nvidia drivers then re-install Steam.  Let us know if that worked and if so mark the thread as solved.

---

### Post by bakimenko on 2016-08-03
Just updated to 16.04 and Steam doesn't start after that.
Solved by:
```
[COLOR=#000000][FONT=&amp]find ~/.local/share/Steam/ \( -name "libgcc_s.so*" -o -name "libstdc++.so*" -o -name "libxcb.so*" \) -print -delete[/FONT][/COLOR]
```
Nvidia driver is 361.42

---

### Post by MikeCyber on 2016-08-03
funny I don't have that directory but would have suggested to remove in your home the hidden folder .steam

---

### Post by rech1313 on 2016-08-18
Had the same issue, but I was able to get steam running by following the instructions on the link:
[http://askubuntu.com/questions/451221/ubuntu-14-04-install-nvidia-driver](http://askubuntu.com/questions/451221/ubuntu-14-04-install-nvidia-driver)
basically I tried:

[LIST=1]
[*]*add the graphics-drivers ppa*
[LIST]
[*]*$ sudo add-apt-repository ppa:graphics-drivers/ppa*
[*]*$ sudo apt-get update*
[/LIST]

[*]*install the recommended driver*
[LIST]
[*]*$ sudo ubuntu-drivers autoinstall*
[/LIST]

[*]*restart your system*
[LIST]
[*]*$ sudo reboot*
[/LIST]
[/LIST]
That allowed me to get steam running, I still have not installed a game and tried to play, but I'm in the process of doing that (slow connection).

---

