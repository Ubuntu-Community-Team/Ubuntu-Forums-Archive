---
title: "I am unable to find the desktop folder."
date: 2011-03-08
forum: Desktop Environments
---

### Post by n96 on 2011-03-08
I just installed Ubuntu yesterday and I'm still trying to figure out how it works. Basically what I understood was that there is supposed to be a desktop folder in your home folder, but my home folder is empty. I believe I am running gnome, and also I seem to be unable to download any files. I also tried right clicking on the desktop, but that did nothing.

Edit: Actually I can download files, but I can't seem to access them.

---

### Post by Frogs Hair on 2011-03-08
Hi and Welcome 

I'm not clear on what your trying to do . Ubuntu does not come with any desktop folders and you  should be able to create folders by right clicking the desktop and selecting create folder. 

Since you have an internet connection use the first link , it is resource for beginners and when you are ready try and download the guide from the second link.

[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)
[http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)

---

### Post by n96 on 2011-03-08
Well as I was saying, right clicking on the desktop does nothing for me. No dropdown menu, etc.

Edit: OK I found how to access the desktop folder, but still nothing shows up on the actual desktop.

---

### Post by Frogs Hair on 2011-03-08
If you have no context menu on the desktop , then there is something wrong . I should also mention if the programs you downloaded are for Windows they will not run on Ubuntu unaided . Some Windows programs will run on Ubuntu with the aid of program called Wine.

---

### Post by Krytarik on 2011-03-09
The issue that you can't right-click at your desktop (or at least that it doesn't have any effect), I also suppose that you don't *see* any items on your desktop, is most probably related to the video driver or its options. What video card/chip do you have, what driver are you running, how did you install those?

As a temporary workaround you can try "restarting" Nautilus to bring up your desktop:
- press Alt+F2
- enter
```
killall nautilus
```

---

