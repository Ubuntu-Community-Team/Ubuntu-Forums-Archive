---
title: "ubuntu freezes?"
date: 2009-02-19
forum: General Help
---

### Post by saied45 on 2009-02-19
hello. i like ubuntu( altho its not perfect its much much better than vista). i do have one big issue tho and i dont know if anyone else has ever experienced any problem like this. sometimes ubuntu freezes on me when messages pop up. For example in firefox if u close multiple tabs it asks u if u want to save or dont save. that freezes on me. so i disabled that everything is fine. the other day i tried to unmount a volume and it said it poped a message saying it couldnt do it cause i had an app runing. that also frooze my ubuntu. 
anyone know why. i think its the drivers issue with nvidia but who knows. im not experienced. i be grateful if someone could try to help me
thanks.

---

### Post by Yellow Pasque on 2009-02-19
Can you get to a terminal by pressing Ctrl+Alt+F1 when these freezes happen?
Also, do the Caps Lock and Scroll Lock LED's on your keyboard flash when the freeze occurs?

---

### Post by saied45 on 2009-02-20
thats something i havent tried. im gonna try it now. thanks for the help.  i can do the three figner shuffel sometimes and that works(sometimes, other times i have to restart). but i havent tried ur method.

---

### Post by saied45 on 2009-02-20
nope i couldnt get to terminal. also caps locked light wouldnt turn off when ubuntu frooze, but then it turned off after like a minute but ubuntu was still frozen. im pretty sure its the nvidia drivers

---

### Post by Yellow Pasque on 2009-02-20
It doesn't appear to be a kernel panic, so that's a good sign. It could be an issue with X.org locking up (maybe caused by video driver issue).
I don't know what to suggest, except looking at system logs for warnings/errors.

---

