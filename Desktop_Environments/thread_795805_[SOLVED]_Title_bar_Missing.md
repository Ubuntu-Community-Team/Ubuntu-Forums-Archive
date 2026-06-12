---
title: "[SOLVED] Title bar Missing"
date: 2008-05-15
forum: Desktop Environments
---

### Post by SnackMasterX on 2008-05-15
Hello, I just installed 8.04 and installed the nvidia drivers for my 7900 GT (not the "new" glx drivers) however after I installed the nvidia drivers my title bars disappeared. If I edit the xorg.conf and change the driver from nvidia to vesa then my title bar reappears however I cannot use twinview with the vesa driver.

Thanks in Advance for any assistance that can be provided.

---

### Post by hermes0710 on 2008-05-16
I suppose you mean the window decorations and not the panels by "title bars". Try typing through a terminal "metacity --replace" to see what happens

---

### Post by SnackMasterX on 2008-05-16
No, I wish it was as simple as the themes missing but I mean title bar as in where it says the program name and has the minimize, maximize, and close buttons. No idea what happened but I get the same problem when I try using an ATI card as well. Thought it might just be something with the nvidia drivers but I have no idea why it's doing this. I get the title bar back when I change from nvidia to vesa driver in the xorg.conf though. Any suggestions?

---

### Post by TWeerts on 2008-05-17
that is what he is talking about. i just had the same problem. the way i fixed it was:

system > preferences > advanced desktop effects settings > effects > window decoration. make sure "window decoration" is checked.

---

### Post by SnackMasterX on 2008-05-17
Ohh, sorry I didn't understand that. I will do this when I get home, thanks for the help!

---

### Post by SnackMasterX on 2008-05-18
Alright I have another question, what do I do if I do not have

system > preferences > advanced desktop effects settings

---

### Post by TWeerts on 2008-05-18
you must install the package "advanced desktop effects settings." use synaptic.

however, my title bars have disappeared again. and my window decorations are checked, though. any help?

---

### Post by angry_johnnie on 2008-05-19
Advance desktop effects (the package is called compizconfig-settings-manager) will give you window decorations, **if** you're using compiz.

I'f you're not using compiz, you could just do what hermes0710 suggested.

Open a terminal and type

```
metacity --replace & disown
```

If the problem is compiz-related, then yes, install compizconfig-settings-manager, and enable the **window decorations** plugin.

---

### Post by anuban on 2008-05-19
Do the following and see:

[LIST]
[*] Press CTRL+ALT+F2
[*] Login and password
[*] sudo apt-get remove gnome-panel
[*] sudo apt-get install gnome-panel
[*] sudo apt-get install ubuntu-desktop.
[*] Restart...
[/LIST]
 everything should be fine.:smile:

There is a similar thread for the same issue some people are facing:
[http://ubuntuforums.org/showthread.php?t=772229](http://ubuntuforums.org/showthread.php?t=772229)
Hope it helps...

---

### Post by bslaveboy on 2008-05-23
I'm still having the problem with the missing title bars.

I've uninstalled and re-installed the gnome-panel etc. as you suggested, but that doesn't help.

Replacing with metacity does work, but then I don't have any of the desktop effects, which kinda makes having a graphics card rather pointless.

---

### Post by VMC on 2008-05-23
> **TWeerts said:**
> that is what he is talking about. i just had the same problem. the way i fixed it was:

system > preferences > advanced desktop effects settings > effects > window decoration. make sure "window decoration" is checked.

For the life of me I can't find this application. My system preferences doesn't show desktop effects settings. I even wnet to "/usr/share/applications" and looked around. Found nothing about this. Thanks.

---

