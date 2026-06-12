---
title: "Nvidia driver makes Ubuntu crap out sometimes"
date: 2009-03-21
forum: General Help
---

### Post by Raskula on 2009-03-21
I have the latest Nvidia driver, 185.13 beta.

Thats the only driver that doesn't mess up the Ubuntu default theme. 

The Problem is that randomly, once or twice a day maybe, my computer just freezes with a white,black,multi-colored screen that is all distorted, its simply just a mess. I have to hold down the power button to shut it off because I can't CTRL+ALT+DELETE to get out of the freeze.


This does this with all the drivers.

Is there any way this can be fixed, how do I show you the error log?

I have an on board Nvidia 6150SE Graphics Card.

---

### Post by hikaricore on 2009-03-21
Linux doesn't use ctrl+alt+delete.

You can hit ctrl+alt+f[1-6] (ie: ctrl alt f1) to get to a text terminal.
Or you can hit ctrl+alt+backspace to restart X.

Neither of these will correct your problem as it stands but atleast you don't just have to shut off the power.
Sorry I don't have time at the moment to help with driver issues.

---

### Post by skydiver|goose on 2009-03-21
Yes, Ctrl Alt Backspace will restart xorg and is a much faster and easier on your system way to get out of a crash/freeze.

Have you tried experimenting with Envy?

---

### Post by Raskula on 2009-03-21
Yeah I meant backspace sorry.

I don't know what envy is.

I installed the driver using this guide: [http://ubuntuforums.org/showthread.php?t=990978](http://ubuntuforums.org/showthread.php?t=990978)

---

### Post by skydiver|goose on 2009-03-21
try installing "envy-ng" and fool with that, with my old (nvidia) box, nothing was stable until I started running through envy

---

### Post by Raskula on 2009-03-21
Would I have to uninstall the Nvidia driver?

---

### Post by skydiver|goose on 2009-03-21
no, envy will handle the driver, just do "apt-get install envy-ng"

---

### Post by Raskula on 2009-03-21
the package wasn't found. Would it be envyng-gtk?

---

### Post by skydiver|goose on 2009-03-21
yes, that's the one, it just comes up as Envy-NG under "Applications" after installed. Sorry, I haven't had to use it since 8.04, so I'm a bit rusty on it...

---

### Post by Raskula on 2009-03-21
I'm not too sure what you want me to do with it. It only lists the old versions of Nvidia.

[img]http://i44.tinypic.com/24fch9h.png[/img]

---

### Post by Raskula on 2009-03-22
I don't know if this helps the situation but after I install a Nvidia driver, all the icons and things on the top and bottom bar like move around.

---

### Post by Raskula on 2009-03-22
I think I fixed the problem. I set the nvidia-settings resolution to auto, and used the ubuntu screen resolution program to set the resolution. 


The only problem I have with this is I can't go higher than 1024x768 with that. and I need it 1280x1024.

How can I accomplish this without changing nvidia-settings?

---

