---
title: "Transparency"
date: 2006-05-15
forum: Desktop Environments
---

### Post by jedimasterk on 2006-05-15
I am running Breezy and am trying to get translucency in KDE as well as transparency running in Gnome. I have xcompmgr installed. I own a gforce 6800GT and have latest nvidia drivers installed. Run xcompmgr in terminal and get "No Extensions". I have added 
Section "Device"
    Identifier     "NVIDIA Corporation NV40 [GeForce 6800 GT]"
    Driver         "nvidia"
    Option         "RenderAccel""true"
    Option         "AllowGLXWithComposite""true"
EndSection
to my xorg file, and even tried the option Extensions but nothing works. 
What do I need to specifically do to get this to work in both enviroments. I also have xorg 6.8.2.

---

### Post by 23meg on 2006-05-15
You need to have the following:
```
Section "Extensions"
        Option "Composite" "Enable"
EndSection
```

---

### Post by jedimasterk on 2006-05-15
Well I got it to work. KDE works fine with translucency. But with Gnome you have to stop  xcompmgr before you log out or else it will seem like it freezes the screen. I hope XGL and Dapper is better than this.

---

### Post by Ptero-4 on 2006-05-15
gnome 2.14 (Dapper) includes it's own compositing manager.

---

### Post by jedimasterk on 2006-05-16
"Some people says that if you play a Windows XP install CD backwards you will hear demon voices commanding you to worship Satan". But that's nothing. If you play it forward it will install Windows XP"

I agree my friend!.  
Windows Vista will be Microsoft's downfall. Nothing more than an update to Windows XP!. Not a major upgrade like it was suppose to be.

---

