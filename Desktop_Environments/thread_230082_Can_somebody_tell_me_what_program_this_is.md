---
title: "Can somebody tell me what program this is?"
date: 2006-08-05
forum: Desktop Environments
---

### Post by Sumint620 on 2006-08-05
i was looking on this wiki, [http://gentoo-wiki.com/HOWTO_XGL](http://gentoo-wiki.com/HOWTO_XGL) , and noticed that media player. does anybody know what that is and where i can get it? thanks

---

### Post by Dubbayoo on 2006-08-05
considering it says mplayer on the taskbar I would guess that it is in fact mplayer; your question should be what skin is it, the answer to which i don't know.

---

### Post by kingbilly on 2006-08-05
The program you see is MPlayer.
You can install it using EasyUbuntu, Automatix, or Synaptic.  Just do a quick forum search.
The specific skin you are seeing is called proton and you can find it here
[http://www.mplayerhq.hu/design7/dload.html](http://www.mplayerhq.hu/design7/dload.html)
Scroll down the page until you reach the skins catagory.

---

### Post by Sumint620 on 2006-08-05
yeah i saw that on the bottom picture but i don't think that is the same program. the one i'm talking about is the one in the first picture (left side) as well as the fourth (left side again). if that is indeed mplayer if somebody could give me the skin that would be good.

---

### Post by kingbilly on 2006-08-05
I believe it is amarok
If you have enabled extra repositories open up a terminal and type:
```
sudo apt-get install amarok
```

---

### Post by Sumint620 on 2006-08-05
yeah i got it. i'm getting it through synaptic though. thanks for telling me the program

---

### Post by Sumint620 on 2006-08-05
ok so i installed amarok and everything looked fine. when i go to start the program from applications > sound and video > amarok, it loads the splash screen and thats it. when i load it from a console this is what i get 

```
ryan@Ubuntu-Desktop:~$ amarok
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
amaroK: [Loader] Starting amarokapp..
amaroK: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kbuildsycoca running...
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
terminate called after throwing an instance of 'std::bad_alloc'
  what():  St9bad_alloc
KCrash: Application 'amarok' crashing...
Could not find 'drkonqi' executable.
KCrash cannot reach kdeinit, launching directly.
```

no idea whats going on.

---

### Post by kingbilly on 2006-08-06
You may want to post this as a new thread if you haven't already, this time with a title such as "Problem Installing Amarok".  This way someone who is familiar can view it when they read the unanswered post section, which this new thread would show up in.

Oh yes, and this also means I'm not sure how to help you but your welcome for the ID on the program yesterday.

Good Luck!

---

