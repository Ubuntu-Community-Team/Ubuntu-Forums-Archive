---
title: "Trouble installing codecs for totem media player"
date: 2006-03-05
forum: Desktop Environments
---

### Post by kuys on 2006-03-05
Every time I try to update my repositories and/or codecs, it asks for the umbuntu cd. I put the cd in the drive and it doesn't do anything. I believe in the process of updating my video card drivers using the nvidia how-to i found in these forums I updated my kernel to a newer version than what the cd is. Is there a way around this? please help.

---

### Post by matthew on 2006-03-05
Open a terminal (Applications->Accessories->Terminal from the menu) and do the following in the terminal window

sudo gedit /etc/apt/sources.list
<enter password when prompted>

In the file that opens, put a # in front of the line for the cd (it should be the first line or so in the file)

Save and close, close the terminal and open Synaptic and see if that fixes the problem.

Then check the repositories link in my signature for more info/ideas

---

### Post by kuys on 2006-03-05
What packages in Synaptic do I need to install to enable video play with totem? \

Also when I try Mplayer I get a error saying new_face failed error. Please supply the txt font file. mplayer/subtfont.tts.

---

