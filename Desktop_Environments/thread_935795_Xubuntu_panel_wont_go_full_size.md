---
title: "Xubuntu panel wont go full size"
date: 2008-10-02
forum: Desktop Environments
---

### Post by loldrup on 2008-10-02
I have a laptop connected to my 1680x1050 monitor, and the XFCE-panel wont stretch further than 1024 pixels in width (the width of my laptops monitor). I only use the big monitor. What can I do to make it stretch to the full width of my external monitor?

It has detected the resolution of 1680x1050 fine. It's just the panel that doesn't adhere to this..

---

### Post by loldrup on 2008-10-02
Also, my windows thinks that "maximize" means going to a resolution of 1024x768. The rest of my monitors pixels feels neglected..

---

### Post by Peter09 on 2008-10-02
Just to check, is the size of your wallpaper the problem, have you got it set to full screen, can you place icons out side of the wallpaper?

Sorry just re-read - I think you are saying that a maximised window is not full screen, which then makes my comment N/A

---

### Post by loldrup on 2008-10-04
> **Peter09 said:**
> Sorry just re-read - I think you are saying that a maximised window is not full screen, which then makes my comment N/A

true. it is not full screen

---

### Post by roger_1960 on 2008-10-04
Hi

Try

sudo displayconfig-gtk  (in terminal)

enter your password and then change "model" and resolution.  Hopefully it will work.  You may also need to select screen 2, depending on where it is connected.

---

