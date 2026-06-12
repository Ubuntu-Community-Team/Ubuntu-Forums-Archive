---
title: "Can some one identify This"
date: 2011-04-20
forum: Desktop Environments
---

### Post by darkpaws on 2011-04-20
Here is a screen shot I found and I want the gadget on the right.  Does any one know what that is?

[IMG]http://i34.photobucket.com/albums/d124/SMasseyrr/Gaming/overglossed1.jpg[/IMG]

Thanks in advance

DP

---

### Post by ImDougy on 2011-04-20
i think that is conky.

---

### Post by georgemc on 2011-04-20
The panel on the right underneath the clock is conky.

Check the Software center and synaptic.

George

---

### Post by pbpersson on 2011-04-20
[Here is a thread]("http://ubuntuforums.org/showthread.php?t=281865&highlight=conkey+screenshots") where people shared their conky files along with a screen shot of their panels

---

### Post by darkpaws on 2011-04-21
OK thanks guys.  now is there a way to set Conky up with a startup icon, or at least a way to shut it down?  Also I have tried applying the same config files from the thread and it didnt change anything.

DP

---

### Post by Copper Bezel on 2011-04-21
How were you trying to apply them? The configuration file should just be in your home directory as .conkyrc .

You can just run the command conky to start it up and killall conky to end the process. To get conky at startup, put the command sleep 30s; conky in your Startup Applications in Preferences.

---

