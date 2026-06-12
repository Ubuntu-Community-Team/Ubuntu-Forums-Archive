---
title: "&quot;XGL Absent, checking for NVIDIA&quot; when using an ati card"
date: 2006-10-30
forum: Desktop Environments
---

### Post by fotakis on 2006-10-30
Hello all,

I installed ubuntu edgy eft 6.1, after seeing some killer videos using bery on Ubuntu machines. Anyways I gave it a go, I had some problems getting dri to work with my card ATI Radeon 9600 on an HP zt3010 laptop. 

Now dri works, so I went ahead installing XGL using this howto [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Xgl.2FBeryl_.28ATI.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Xgl.2FBeryl_.28ATI.29). I now get this weird error, and I can't do anything with it.


```
XGL Absent, checking for NVIDIA
Nvidia Absent, assuming AIGLX
beryl: No composite extension
```

I took all the steps in order to install fglrx, and that is my driver I 
have tested using 

```

dmesg | grep "fglrx"
fgl_glxgears
glxgears
glxinfo | grep "direct"   <----The answer is yes

```


So I am kind of stuck, I have looked everywhere for this, since googling 
this is a bit tricky, the searches return Nvidia specific results.

Well anything else I need to tell you guys just tell me and I am there.

Thanks for reading in the first place

Best Regards,
Fotis

---

### Post by fotakis on 2006-11-02
Hello all again,

I am here answering my own question. For anyone looking the problem was that I didn't understand the difference between xgl, and aiglx, and compiz and beryl. 

I have an ati, and I was able to get beryl working with no 3D acceleration, but that was just too slow. So I decided to take on adding the fglrx from the ubuntu repos, and following this [guide]("http://wiki.cchtml.com/index.php/Xgl-Compiz-Dapper")
i was able to get beryl loading and everything. 

Now I am getting this weird behaviour, and I would like to know if someone can point me in the right direction. I am able to rotate the cube, the menus come up using the effect, but If i open an application say firefox, and I click on the title bar, or  try to drag the window, gnome just crashes.

If someone could please help me out, I'd very much appreciate it.

Best Regards,
Fotis

---

### Post by WalmartSniperLX on 2006-11-14
Hey. I have the same problem. I've been trying to figure this out myself, but no luck yet. Ill make sure to post here when I figure this out. :D

---

