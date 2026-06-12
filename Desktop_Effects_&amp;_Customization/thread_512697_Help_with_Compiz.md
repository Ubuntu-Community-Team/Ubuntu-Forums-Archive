---
title: "Help with Compiz"
date: 2007-07-29
forum: Desktop Effects &amp; Customization
---

### Post by ukulele_ninja on 2007-07-29
Ok, I got Compiz installed and all and I can run it, but it deletes my windows frames. I read that if you right click the icon in the system tray and tell it to use emeryld as your windows decorator its supposed to fix it but... it didnt so im sad. What fixes the windows? and how exactly do I make compiz do fun cool things?

---

### Post by FleetAdmiral74 on 2007-07-29
Can you clarify if you are using Compiz or Compiz Fusion?

---

### Post by pashashome on 2007-07-29
Try running this in Terminal.

```
compiz --replace -c emerald
```

Does that work?

---

### Post by ukulele_ninja on 2007-07-30
ryan@Ted:~$ compiz --replace -c emerald
Fatal: Failed test: texture_from_pixmap support
Checks indicate that it's impossible to start compiz on your system.


that was my result from running that string

---

### Post by Gigzaholic on 2007-07-30
edit your xorg.conf file by going to the terminal and typing:

sudo gedit /etc/X11/xorg.conf

under the device section add the following:

Option "AddARGBGLXVisuals" "True"

oh and change defaultdepth to 24 if it's not already set at that

reference link: [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Beryl_.28Nvidia.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Beryl_.28Nvidia.29)

the instructions are for beryl but they dhould work with your specific problem.

---

### Post by ukulele_ninja on 2007-07-30
Well I tried that and now Ubuntu wont make it to the login screen at all!

---

