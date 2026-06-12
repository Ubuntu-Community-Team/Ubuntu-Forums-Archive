---
title: "Display output of app in conky"
date: 2010-03-01
forum: Desktop Environments
---

### Post by dragonboss on 2010-03-01
How do I configure conky to display the output of cmatrix?(Just for eyecandy's sake!)

---

### Post by VCoolio on 2010-03-02
I don't think you can do that. If you want it as an eyecandy background on your desktop, use a transparant terminal without window borders that runs cmatrix (e.g. use roxterm for that and put !(class=Roxterm) in the compiz window decorator plugin at the decoration entry to prevent borders). I wouldn't keep cmatrix running all the time considering it's cpu usage, but that's your call.

---

### Post by matchett808 on 2010-03-02
if you want scrolling text:

${scroll 400 35 ${source (like maybe an exec?)} }

scrolling isnn't very good for me but I haven't invested much time playing with the values...

---

### Post by dragonboss on 2010-03-02
I forgot about those transparent terminals! I just wanted it to be very small and athe bottom of my conky because i have noticed that the cpu usage varies with the size ofthe terminal window and also I think its slower in gnome cos i tried it in backtrack 4 on terminator in 4 windows and it was quick and didn't take much cpu, but its probably a bit slower in gnome cos of compiz and other things. Thanks anyway

---

