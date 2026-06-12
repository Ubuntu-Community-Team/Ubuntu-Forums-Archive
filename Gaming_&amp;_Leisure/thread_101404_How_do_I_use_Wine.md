---
title: "How do I use Wine?"
date: 2005-12-09
forum: Gaming &amp; Leisure
---

### Post by PheonixRising on 2005-12-09
Hi, I was wondering, could someone walk me through exactly how to install wine, use it to install and play a game (specifics on Guild Wars and Pariah would be greatly appreciated) what do I need to play the game.

Thanks!

Also, I don't think Ubuntu is detecting my nVidia card. Is that going to be a problem?

---

### Post by Harleen on 2005-12-09
Just install the package "wine" through synaptic. The version delivered with breezy is rather old, so you should add the following line to your /etc/apt/sources.list to get the latest version:

```
#wine updates
deb http://wine.sourceforge.net/apt/ breezy/
```

If you have added the above line, you can also install winetools, which is a great help for installing some windows components might needed by the games you want to install.

If you installed winetools, you can configure wine by running "winetools" from the command line. Otherwise run "winecfg".

If everything is set up corectly, you can try to run any windows program by typing "wine progname.exe".  But don't expect too much - most games will refuse to run. I don't know about the games you mentioned, but it's worth a try.

You of course have to set up your graphic card to get descent frame rates in 3D-Games. 
if running "glxgears -printfps" gets you frame rates above 500, you can be pretty sure your cars is working. If not, you should intall the NVidia drivers first.

---

### Post by PheonixRising on 2005-12-09
Hmm... would you mind telling me where toget the nVidia Drivers?

---

### Post by Harleen on 2005-12-09
short version: Just install nvidia-glx through synaptic and run "sudo nvidia-glx-config enable" afterwards.

Extensive version: [http://ubuntuforums.org/showthread.php?t=85499](http://ubuntuforums.org/showthread.php?t=85499)

---

### Post by Perfect Storm on 2005-12-09
```

sudo apt-get install nvidia-glx
sudo nvidia-glx-config enable

```

reboot

---

