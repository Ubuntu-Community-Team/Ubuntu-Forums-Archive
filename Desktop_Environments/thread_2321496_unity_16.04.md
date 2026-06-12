---
title: "unity 16.04"
date: 2016-04-22
forum: Desktop Environments
---

### Post by okkadiroglu on 2016-04-22
Hi,

Just upgraded to Ubuntu 16.04. About a month ago I was not able to use unity desktop for some reason that I did not figure out. I expected that the upgrade will take care of my problem. When I log in using Ubuntu desktop all windows open on top of each other and can not move any of them. I use Metacity but I prefer Unity. If I start unity in a terminal it works well but the the strip a tho top of the window disappears and it seems that unity works under Metacity. How can I use unity when I login to my user?

Many thanks for the help, best regards

---

### Post by grahammechanical on 2016-04-22
Please tell us the hardware specification & please include information about the video adapter. Especially the amount of video memory it has. It may be that your video adapter cannot do the hardware accelerated 3D rendering the Unity 3D requires or you may need to change to a different video driver. Please run this command

```
/usr/lib/nux/unity_support_test -p
```

This is what I get. What do you get?

> graham@sda6-Lubuntu:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   nouveau
OpenGL renderer string: Gallium 0.4 on NVA5
OpenGL version string:  3.0 Mesa 11.2.0

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes

Regards.

---

### Post by dFlyer on 2016-04-22
Have you tried this from the release notes:

restart unity-panel-service

---

### Post by okkadiroglu on 2016-04-23
Thank you very much **grahammechanical**, 

I use a AMD FX(tm)-4100 Quad-Core Processor × 4  computer with GeForce 8500 GT/PCIe/SSE2 graphics and 7.8GB memory. The output for the command you requested is given below.

[I]oyo@okk001:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce 8500 GT/PCIe/SSE2
OpenGL version string:  3.3.0 NVIDIA 304.131[/I]

[I]Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes

[/I]

Also many thanks** dFlyer**, 

I did what you have asked me to do and I got

[I]oyo@okk001:~$ restart unity-panel-service
restart: Name "com.ubuntu.Upstart" does not exist[/I]

when I searched for unity-panel-services all I found was a manual page. When I tried to install unity I got

[I]sudo apt-get install unity
Reading package lists... Done
Building dependency tree       
Reading state information... Done
unity is already the newest version (7.4.0+16.04.20160415-0ubuntu1).[/I]

Thank you both for taking your time to help me.

Best regards.

---

### Post by Frogs Hair on 2016-04-23
If you can get into the terminal in the Ubuntu session with ctrl + Alt + t try the following.

 ```
sudo apt-get install dconf-tools
``````
dconf reset -f /org/compiz/
``````
setsid unity
```

---

### Post by $yl9pAR%t on 2016-04-23
Recomended driver for your GPU is 340.xx, do you have 340.xx or 304.xx?

---

### Post by deadflowr on 2016-04-23
> **mefisto888 said:**
> Recomended driver for your GPU is 340.xx, do you have 340.xx or 304.xx?

It's 304
> OpenGL version string: 3.3.0 NVIDIA 304.131

---

### Post by okkadiroglu on 2016-04-24
Hi all,

Thanks very much for all your work in helping me. After two days of trying I finally solved my problem. For a very long time I was playing with packages and installing them and removing them. At my age (70) one must slow down a bit. So I decided to use LTS. My solution to my problem was a very brutal  one. After taking a backup of my home directory I erased every thing and started from the scratch. Now everything works well. Many thank for all of your help.

My very best regards to all.

---

### Post by vasa1 on 2016-04-24
> **okkadiroglu said:**
> Hi all,

Thanks very much for all your work in helping me. After two days of trying **I finally solved my problem**. ...
Then please mark your thread [SOLVED] so that it may help others. Instructions for doing so are here: [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads).

Thank you :)

---

