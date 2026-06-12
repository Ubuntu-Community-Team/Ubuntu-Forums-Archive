---
title: "Starting Beryl"
date: 2007-05-24
forum: Desktop Environments
---

### Post by lbozzay on 2007-05-24
Hi all,

I'm a new Kubuntu (Feisty) user and I really like the system. I decided to install Beryl. I have an ATI X700 card. I have the open source driver installed, direct rendering is on, I can play 3D games with no problem.
I installed Beryl, and Beryl manager is running but when I want to change to Beryl in 'Select Window Manger' menu, the display just falls back to KDE.
I don't know where I could find log files to start analyzing the problem. Please if you have any idea how to fix this, a reply would be very much appreciated.

Thanks in advance!

Bozz

---

### Post by Znupi on 2007-05-24
Are you sure you are logged in to your Xgl session?

---

### Post by lbozzay on 2007-05-24
I have only Default, KDE and Failsave session when KDE starts. Is that normal, I have heard that there should be a 3D session.

---

### Post by Znupi on 2007-05-24
There should be an Xgl session. Refer to [this tutorial](https://help.ubuntu.com/community/Beryl/ATI/Feisty) and just look at **Setting Up XGL** and **Creating a XGL Login**. Then try logging in into Xgl... Of course, you may have to roll back the beryl core. If you don't want to, you'll have to install AiGLX, but I don't know how to do that.

---

