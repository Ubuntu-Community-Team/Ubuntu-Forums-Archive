---
title: "Cinnamon"
date: 2012-06-30
forum: Desktop Environments
---

### Post by Reg on 2012-06-30
I'm using Ubuntu 12.04 and have a problem with a  newly installed Cinnamon. The bottom panel is there - with Firefox and Thunderbird tabs but I can't open them or anything else except the Main menu. I just get a white rectangle in the centre of a blue screen
Any ideas, please? 
Thanks
Reg[/QUOTE]

---

### Post by Shadius on 2012-06-30
You can try checking to see if your packages need to be upgraded by running in a Terminal:
```
sudo apt-get upgrade
```

---

### Post by Reg on 2012-07-01
Thanks for that. I've just tried it and tried apt-get install cinnamon again but the messages is that the latest version is installed.
Reg

---

### Post by Shadius on 2012-07-01
> **Reg said:**
> Thanks for that. I've just tried it and tried apt-get install cinnamon again but the messages is that the latest version is installed.
Reg

There's no need to try to install it again. It's already install and the upgrade command would have upgraded any packages if needed.

---

### Post by Shadius on 2012-07-01
Could you post a screenshot of what happens when you're trying to open a program? So I can see the image you're talking about. I've come across some Cinnamon problems as well. I have my own thread about it and it was suggested that it could be a graphics card issue. Also, could you run the following code in Terminal...
```
/usr/lib/nux/unity_support_test -p
```

---

### Post by Reg on 2012-07-01
reg@reg-HP-d530-SFF-DF377T:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   Tungsten Graphics, Inc
Thanks for this. 
This is what I get with the OpenGL renderer string: Mesa DRI Intel(R) 865G x86/MMX/SSE2
OpenGL version string:  1.3 Mesa 8.0.2

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      no
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       no

Unity 3D supported:       no

Sorry. I can't give you a screen shot. Blue screen with bottom panel and Thunderbird and Firefox tabs. Clicking them does nothing. The menu does come up but logging our produces a white rectangle in the centre of the blue screen. It's a real struggle to log out at all. 

Before I saw your reply I purged Cinnamon and then repeated the installation. But no reponse. The test above was done after this. Thanks. Reg

---

### Post by Shadius on 2012-07-01
> **Reg said:**
> reg@reg-HP-d530-SFF-DF377T:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   Tungsten Graphics, Inc
Thanks for this. 
This is what I get with the OpenGL renderer string: Mesa DRI Intel(R) 865G x86/MMX/SSE2
OpenGL version string:  1.3 Mesa 8.0.2

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      no
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       no

Unity 3D supported:       no

Sorry. I can't give you a screen shot. Blue screen with bottom panel and Thunderbird and Firefox tabs. Clicking them does nothing. The menu does come up but logging our produces a white rectangle in the centre of the blue screen. It's a real struggle to log out at all. 

Before I saw your reply I purged Cinnamon and then repeated the installation. But no reponse. The test above was done after this. Thanks. Reg
Seems like you're having the same problem I was having when I tried Cinnamon. I was getting blue menu box when I tried to open programs like Firefox. I also got the white menu box when I tried to log out and basically had to guess where the buttons were in order to log out. I think it has to do something with the graphics cards not being able to support 3D so I decided to wait  until Cinnamon 2D comes out.

---

### Post by Reg on 2012-07-01
Right. I'd bettter be patient and do the same.
Thanks again.
Reg

---

### Post by Shadius on 2012-07-01
> **Reg said:**
> Right. I'd bettter be patient and do the same.
Thanks again.
Reg

You're welcome, glad to help. :)

---

