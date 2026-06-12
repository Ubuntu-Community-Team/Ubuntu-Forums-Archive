---
title: "FPS verrry low."
date: 2005-09-13
forum: Desktop Environments
---

### Post by conjurer on 2005-09-13
Hi I just switched from windows to (ubuntu) linux. I know that its supposed to run faster but right now my computer is lagging big time and I dont know what seems to be the problem. When I dont do anything, my Frames per second is around 200, but as soon as I do something a tiny bit image intensive (like browsing around google maps, or simply dragging squares on my desktop), the FPS drops to something like 7.

I have 512 MB of ram and my graphic card is a nVidia Geforce 2 MX400 graphic card. (I know its pretty old but it worked fine under windows and it certainly didnt cause my computer to lag when dragging boxes on my desktop)

Can anyone help?

---

### Post by ispmarin on 2005-09-13
Are you using the NVIDIA drivers?

Ivan

---

### Post by conjurer on 2005-09-14
Oh hadnt thought about that... Thanks!

---

### Post by conjurer on 2005-09-14
Hmm does anyone know how to prevent the nvidia logo from appearing when you start the computer?

---

### Post by seethru on 2005-09-14
[QUOTE=conjurer]Hmm does anyone know how to prevent the nvidia logo from appearing when you start the computer?[/QUOTE]
 edit the xorg.conf file

```
sudo gedit /etc/X11/xorg.conf
```

look for where you declare the driver setting as nvidia and at the end of that section (before endsection) put 
```
Option "NoLogo"
```

doing this from memory, at work atm so I can't remember exactly but I believe thats correct.

---

