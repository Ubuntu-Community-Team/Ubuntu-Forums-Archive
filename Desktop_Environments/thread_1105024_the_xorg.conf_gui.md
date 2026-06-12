---
title: "the xorg.conf gui?"
date: 2009-03-24
forum: Desktop Environments
---

### Post by monkeyslayer56 on 2009-03-24
how can i configure X useing the gui? i can get the gui up but only after i crash X and run in low graphics mode ut i can do anything then becouse after about 3 mouse clicks or 1 min and then it freezes before i can get anything done i know i can edit it from gedit but if possable i would like to use a gui and when i gooogle all i found was stuff saying there is a gui not hopw to get it up so please help me please i am still a linux n00b

---

### Post by gjoellee on 2009-03-24
try to run an "xfix". Read how here: [http://www.kshoster.net/?c=tuts/xfix](http://www.kshoster.net/?c=tuts/xfix)

---

### Post by monkeyslayer56 on 2009-03-24
i don't think thats is exactly what i need because my X is not broken i just want the utility that comes up after u brake X but without breaking it i can edit by hand but i think it would be much easyer to have a utility configure it that way i need/want it

---

### Post by Locutus_of_Borg on 2009-03-24
xorgcfg?

thats the only one i know of..not really a GUI, but you get like a blue screen with menu options you can select with the keyboard

---

### Post by monkeyslayer56 on 2009-03-24
go and make a big error in the xorg.conf file so it forces it into lowgraphic mode when it boots up it gives u the option to reconfiger X with a real nice gui were u can select your screens the screen placements refresh rates reolutions adn the drivers to use thats what im asking is there a way to get that WITHOUT crashing X like i mentioned

---

### Post by Locutus_of_Borg on 2009-03-24
try:
sudo dpkg-reconfigure xserver-xorg

---

### Post by monkeyslayer56 on 2009-03-24
all those are from a terminal like thing im looking for is that [http://fosswire.com/post/2007/08/ubuntu-getting-xorgconf-gui/](http://fosswire.com/post/2007/08/ubuntu-getting-xorgconf-gui/) 
it just doesn't tell how to bring it up and i have gotten it beofre but only by miss configuring X

---

### Post by Locutus_of_Borg on 2009-03-24
i dont know

open terminal and enter just xo then press tab and see if any suggestions look relevant

---

### Post by overdrank on 2009-03-24
> **monkeyslayer56 said:**
> all those are from a terminal like thing im looking for is that [http://fosswire.com/post/2007/08/ubuntu-getting-xorgconf-gui/](http://fosswire.com/post/2007/08/ubuntu-getting-xorgconf-gui/) 
it just doesn't tell how to bring it up and i have gotten it beofre but only by miss configuring X

Hi and the link you provided is I believe the displayconfig-gtk and was stopped after Hardy 8.04.

---

### Post by monkeyslayer56 on 2009-03-24
> **overdrank said:**
> Hi and the link you provided is I believe the displayconfig-gtk and was stopped after Hardy 8.04.
i have hardy 8.04 and i just entered that command in the terminal and it was exactly what i was looking for thanks for the help

---

