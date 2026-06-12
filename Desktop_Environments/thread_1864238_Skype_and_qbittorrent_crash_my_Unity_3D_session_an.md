---
title: "Skype and qbittorrent crash my Unity 3D session and..."
date: 2011-10-18
forum: Desktop Environments
---

### Post by ppsalama on 2011-10-18
Hello.
first... sorry for my english...
I have this problem:
Just after installing Skype and/or qbittorrent, when I run it, my Unity 3D session crash (with an ugly screen effect) and get back to gdm in order to login again.
I don't know why it happens in my clean installation of ubuntu 11.10. In natty both worked fine.
Probably you need more info about my PC. From natty to oneiric I only got problems changing nouveau drivers for propietary nvidia drivers (finally I got it works fine -I suppose it-).

I would like Skype and qbittorrent work again.
Thank you very much for your help.
Best regards

---

### Post by fantab on 2011-10-21
I use both, Skype and qbittorrent on my Oneiric. They work fine without any crash or glitch so far. I suggest you update Oneiric and see. If the problem persists then **try completely removing Skype and qbittorrent and reinstall them. **

```
sudo apt-get --purge skype
sudo apt-get --purge qbittorrent
```Also go to your Home folder and **delete .skype and .qbittorrent** files. Then reinstall.

*Edit: You have to _Ctrl+H_ when you are in Home Folder to reveal the hidden dot(.)files.*

---

### Post by ppsalama on 2011-10-21
Thank you very much for your response fantab. I still have the same problem after doing what you say. As you can see in [this]("http://ubuntuforums.org/showthread.php?t=1864672&highlight=qt+apps+crash")[ post]("http://ubuntuforums.org/showthread.php?t=1864672&highlight=qt+apps+crash"), I think Qt is a problem because I have the same problem also with other Qt-based application (VLC).
 Any ideas to fix or reinstall qt? Perhaps that is the solution. What do you think about this?
Best regards and thanks again

---

### Post by ppsalama on 2011-10-22
Installing all libqt4-* does'nt solve the problem :(

---

