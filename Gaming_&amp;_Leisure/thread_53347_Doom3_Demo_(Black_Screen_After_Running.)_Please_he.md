---
title: "Doom3 Demo (Black Screen After Running.) Please help."
date: 2005-07-31
forum: Gaming &amp; Leisure
---

### Post by PrimoTurbo on 2005-07-31
I have a ATI 9700 Pro 128Mb and I think I setup the ATI drivers correctly. I downloaded and installed doom3-linux-1.1.1286-demo.x86.run, when I go into terminal and run the game "doom3-demo" the game starts up with a black screen and just sits there. I have to ctrl + alt + backspace. Please help me out.

---

### Post by shawn on 2005-07-31
I had the same problem with the demo but the 1.3 patched binaries work fine. Try and borrow the game from someone and see if that works.

Good luck!

---

### Post by PrimoTurbo on 2005-07-31
I found out what the problem was and fixed it thanks to the people at #ubuntu. Also thanks to psychonate for helping me out with a bunch of stuff and making this script to launch doom3 demo.

The problem is that doom3 runs in alsa while gnome runs esd. Fixed it by killing esd then by enabling after the game. Here is the script psychonate made me for doing this quickly.

Open gedit and copy the below into it.

#!/bin/bash
killall esd
doom3-demo
esd &

Save it as doom3-noesd in whichever directory you want (mine is located in my home directory)

Now go into terminal, cd into the directory you saved the script in, and type "chmod +x doom3-noesd"

No you can create a launcher or use ./doom3-noesd

---

### Post by drizek on 2005-08-04
[QUOTE=PrimoTurbo]I found out what the problem was and fixed it thanks to the people at #ubuntu. Also thanks to psychonate for helping me out with a bunch of stuff and making this script to launch doom3 demo.

The problem is that doom3 runs in alsa while gnome runs esd. Fixed it by killing esd then by enabling after the game. Here is the script psychonate made me for doing this quickly.

Open gedit and copy the below into it.

#!/bin/bash
killall esd
doom3-demo
esd &

Save it as doom3-noesd in whichever directory you want (mine is located in my home directory)

Now go into terminal, cd into the directory you saved the script in, and type "chmod +x doom3-noesd"

No you can create a launcher or use ./doom3-noesd[/QUOTE]
 im using kubuntu with an nvidia card and have teh same problem. how can i fix this? i dont have esd running.

---

### Post by Kemotaha on 2005-08-04
[QUOTE=drizek]im using kubuntu with an nvidia card and have teh same problem. how can i fix this? i dont have esd running.[/QUOTE]
 KDE doesn't use esd.  It uses arts I believe.   I could be wrong but you will need to kill that instead of ESD

---

### Post by drizek on 2005-08-04
[QUOTE=Kemotaha]KDE doesn't use esd.  It uses arts I believe.   I could be wrong but you will need to kill that instead of ESD[/QUOTE]
 ill try that. i cant login ATM though, so ill have to figure that problem out firs ;)

---

### Post by drizek on 2005-08-04
the logging in problem istn there anymore, which is wierd. anyway, i got doom 3 running but the sound sucks.

---

