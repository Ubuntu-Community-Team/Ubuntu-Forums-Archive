---
title: "nvidia drivers i hoary"
date: 2005-01-18
forum: General Help
---

### Post by thorhr on 2005-01-18
I have two computers running ubuntu last night I upgraded the hp which has a 932 MGz processor and a nvidia vanta 16 Mb video driver after the upgraded to hoary I installed nvidia-glx everything works great! So i decided to upgrade the other one also, I built it myself.It has a 2.66 processor and a nvidia GForce 4 128 mb 3D card after the upgrade I again installed nvidia-glx then i got a  message that X11/XF86Config has been altered so i opened XF86Config and deleted Load GLcore and dri and i added nvidia in the driver section then i rebooted and all i got  was the nvidia splash screen nothing else would work i hit alt- del a few times  and got a screen saying X is not configured right so i opended XF86Config-4 and put Load GLcore  and Load dri and nv instead of nvidia in the driver section.rebooted gui, started. Opened x11 saw that i had XF86CONFIG AND X11/xorg.conf so i did the same to both files and  the gui still would not boot all i get is the nvidia splash screen. I had the same problem with Fedora core 3 on this computer i think xorg will not work with this card because i reinstalled warty and the glx drivers work great the same with fedora core 2 worked also i want to run ubuntu hoary on this box because it is the best linux os i need to get the nvidia card to work in hoary can anyone help me?

---

### Post by daniels on 2005-01-18
The new version of the nVidia drivers causes hangs on some chipsets, it's a 'known issue' according to nVidia, and I can't do anything about it because the drivers aren't open source.  All you can really do is wait for a new release from nVidia.

---

### Post by thorhr on 2005-01-19
Thanks I thought that was what was wrong because i reinstalled warty on the computer and the nvidia card works using the 6111 nvidia driver. Is there any way to use that driver with hoary?

---

### Post by daniels on 2005-01-19
Not really, I'm afraid.  It needs waay too much patching to get it working with 2.6.10.

---

### Post by thorhr on 2005-01-19
Thank You! I have tried a lot of Linux operating systems and ubuntu is the best!!

---

