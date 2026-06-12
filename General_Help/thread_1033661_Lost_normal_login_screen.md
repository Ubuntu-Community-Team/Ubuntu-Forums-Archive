---
title: "Lost normal login screen"
date: 2009-01-07
forum: General Help
---

### Post by aschwerin.moses on 2009-01-07
Well, im not sure how to explain this under title, but i installed kde-desktop few days back on my Ubuntu 8.04. Today i removed it by following [THIS]("http://www.psychocats.net/ubuntu/puregnomehardy") ... now that i restart my computer is just goes to the terminal screen (not sure what that is called but its the screen that u get by doing CTRL+ALT+F1) ... now what do i do.. how do i get thinks back??

---

### Post by bc90021 on 2009-01-07
What happens if you type:

startx

That is the command for starting the X server.

---

### Post by aschwerin.moses on 2009-01-07
nice.. that works.. but when i restart the computer, it again brings be back to the terminal screen

---

### Post by thegreenblob on 2009-01-07
Maybe gdm got removed in the process.

Try
```
sudo apt-get install gdm
```

(gdm is the login manager)

---

