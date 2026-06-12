---
title: "3d games run slow with fast graphics card"
date: 2008-03-02
forum: Gaming &amp; Leisure
---

### Post by daveluke on 2008-03-02
I have an Nvidia Geforce 8400M with Duo-Core 2.0 Ghz.. 2 Gig of RAM..

My desktop runs pretty smoothly, but whenever I run 3d games, it gets really choppy. I installed what I think is the correct drivers: nvidia-glx-new in synpatic. Even when I turn off compiz, it is still very slow when running games like Penumbra and Frets on Fire. In Penumbra and Tremulous, I can't even get a resolution higher than 800x600. My desktop resolution is 1280x800.

Any ideas on how to fix this? Thanks.

---

### Post by grossaffe on 2008-03-02
i guess you got an inspiron 1420, right?  i've been meaning to install ubuntu onto mine.

---

### Post by daveluke on 2008-03-03
No, actually its a ASUS barebone. I forget the exact model.. Can anybody help???

---

### Post by jacksaff on 2008-03-03
Your card is very, very far from a fast graphics card. You can't realistically play 3D games with an 8400M unless you turn the resolution and detail way down.

---

### Post by Josh1 on 2008-03-03
Yeah the 8400m isn't fantastic. Are you WINE'ing/Cedega'ing or playing native games?

---

### Post by Ferrat on 2008-03-03
have you activated restricted drivers? 

System >> Administration >> Restricted Drivers Manager 

then make sure NVIDIA accelerated graphics driver is checked, at least for me I know that setting has jerked my 3D rendering around sometimes

---

### Post by ahaslam on 2008-03-03
Try:
```
nvidia-settings -a OpenGLImageSettings=3
```
This sets your OpenGL image setting for maximum performance. Texture details will be reduced, but the extra frame rate is more noticeable.

---

### Post by zxscooby on 2008-03-03
Thanks , i didnt know about the nvidia-settings manager , added it to my menu.

---

