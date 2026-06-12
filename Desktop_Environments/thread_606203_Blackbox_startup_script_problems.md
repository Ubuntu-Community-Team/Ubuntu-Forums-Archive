---
title: "Blackbox startup script problems"
date: 2007-11-07
forum: Desktop Environments
---

### Post by AustinMarton on 2007-11-07
Hi there,

I am running Blackbox on Ubuntu Feisty. GDM automatically logs in and starts blackbox. I want to start wbar, bbkeys and a terminal when blackbox starts. 

Following a few threads I have created a .bbstartup.sh file in my home directory. 
```

#!/bin/sh

exec blackbox &
aterm -tr +sb --geometry 70x30+0+300 &
wbar &
bbkeys

```

This works, and starts the appropriate programs on startup.

Now my problem is that when I exit blackbox, even after closing all the other programs, the blackbox bar and disappears, but the background remains. Since blackbox is closed, no menu appears on the desktop, and I have to restart by opening another console with Ctrl+Alt+F2. 
If I comment out the three programs then when I exit blackbox it takes me to the GDM login, which is what I want. (but of course the programs don't run on startup anymore...)

Can anyone help me with this?

Cheers,
Austin

---

### Post by AustinMarton on 2007-11-07
Hi, I have fixed my problem. I merely had to change the order of my script:
```
#!/bin/sh

exec aterm -tr +sb --geometry 60x20+0+300 &
wbar &
bbkeys &
blackbox
```

My only issue now is it would be nice if I could start aterm without a bar up the top with the X on it. I tried Eterm but had absolutely no luck getting it to be transparent.

---

