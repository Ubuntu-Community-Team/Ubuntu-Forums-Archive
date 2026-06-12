---
title: "Postal 2 keeps crashing"
date: 2010-06-27
forum: Gaming &amp; Leisure
---

### Post by northconnor on 2010-06-27
I recently installed the game Postal 2: Share the Pain (not just multiplayer) from a repository, and have been experiencing some problems with it. When I used to open it, it would never load after clicking "new game", thought the audio would still be there. After opening it in Terminal, the welcome screen loads very smoothly, I select a new game, a cutscene loads up, and I get to the part where he looks at the map (very beginning) but the loading bar comes up and the game crashes. I get this message in terminal:

connor@connor-laptop:~$ postal2
Postal 2
Copyright 2003 Running With Scissors, Inc.
Unreal Engine
Copyright 2001 Epic Games, Inc.
/usr/bin/postal2: line 10:  2673 Killed                  ./postal2

And after checking "/usr/bin/postal2" , this is what's inside:

  	 	 	 	 	 	  #!/bin/bash # Postal 2  # Home Page: [http://www.ubuntugames.org](http://www.ubuntugames.org) # # Carlos Donizete [a.k.a Coringao]  # Criado em 07.07.2009 # E-mail: [email]coringao@ubuntugames.org[/email] # cd /usr/local/games/postal2 ./postal2

[FONT=Verdana]So something with the last line is being messed up. Any ideas? I have run this same 
game (but multiplayer) on the windows partition of my computer, so I know it can 
handle it. I also ran games in higher demand of CPU that did fine (even Half-life 2). 
I have not installed any drivers for linux, but I never seem to have needed to.
I am running an MSI Wind U120 with 1.6Ghz processor, 1 GB or RAM, and GMA 950 chip.
If I did need to install drivers, how would I go about doing that for my specs? Any help
would be GREAT. Thank you!


[/FONT]

---

### Post by northconnor on 2010-07-01
Anybody? I'm stumped.

---

### Post by northconnor on 2010-07-01
Oh, and when I go to "hardware drivers" it says "no proprietary drivers were found on this system".

---

### Post by rizzeh on 2010-07-01
GMA 950 is Intel onboard grafix chip, I dont think Postal 2 can run on it. You'll need nvidia grafix card to run heavy games successfuly.

---

### Post by northconnor on 2010-07-03
But I was able to run it on the windows partition of my computer. I was even able to run half life 2 :wink: Is it because there aren't any drivers for the built in graphics on linux?

---

### Post by hikaricore on 2010-07-03
It's because intel halfassed the linux drivers + the hardware relies heavily on directx and offers nearly no opengl support.
You're out of luck.

---

### Post by northconnor on 2010-07-04
Oh ok, darn :( well thanks for the help!

---

### Post by themoddingden on 2010-07-05
hi;
they support linux btw.
you can get a linux version and Postal 3 will come out for linux.
get the collection pack it has the addon packs as well

---

### Post by hikaricore on 2010-07-05
> **themoddingden said:**
> hi;
they support linux btw.
you can get a linux version and Postal 3 will come out for linux.
get the collection pack it has the addon packs as well

The OP is already using the linux version of postal2.
Perhaps you should invest more than a millisecond in reading posts before responding.

---

