---
title: "Windows Crashing Randomly"
date: 2011-05-19
forum: Desktop Environments
---

### Post by cf329rn on 2011-05-19
Hey guys,

So basicly I just installed Ubuntu 11.04 and I am experiencing something I always experience when I install Ubuntu. I will be using a window and then when I switch to another window it will randomly crash and it takes me ages to be able to close it down, sometimes I can never close the window down. This has stopped me from being able to use any version of Ubuntu on my computer which is disappointing because I really love Ubuntu. I have no idea how to fix this issue at all, I have downloaded drivers for Linux from the Nvidia website but I get a window saying it cant be opened, and no surprise after many efforts I can't even close that window. Its a .run file so I don't know if I have to run it via terminal? Can anybody please help me? I am fed up of not being able to use Ubuntu because these windows freezing is making it unbearable to use.

Thanks,
CJ

PS: I am using an Nvidia GT220, I am pretty sure its a graphics card issue because it has to do with the GUI.

---

### Post by 3Miro on 2011-05-19
In Ubuntu, you do NOT install drivers from the Nvidia web page.

Without a proper driver, you are probably in fallback mode. You should click on the Ubuntu logo in the top-left corner, then go to:

Administration -> Additional Drivers (or maybe System -> Admin -> Drivers).

From there, you should be able to activate the recommended Nvidia driver.

---

### Post by wildmanne39 on 2011-05-20
> **cf329rn said:**
> Hey guys,

So basicly I just installed Ubuntu 11.04 and I am experiencing something I always experience when I install Ubuntu. I will be using a window and then when I switch to another window it will randomly crash and it takes me ages to be able to close it down, sometimes I can never close the window down. This has stopped me from being able to use any version of Ubuntu on my computer which is disappointing because I really love Ubuntu. I have no idea how to fix this issue at all, I have downloaded drivers for Linux from the Nvidia website but I get a window saying it cant be opened, and no surprise after many efforts I can't even close that window. Its a .run file so I don't know if I have to run it via terminal? Can anybody please help me? I am fed up of not being able to use Ubuntu because these windows freezing is making it unbearable to use.

Thanks,
CJ

PS: I am using an Nvidia GT220, I am pretty sure its a graphics card issue because it has to do with the GUI.

Hi, I had the same problem, I had to go into additional drivers and change from current driver for my video card to the 173 driver. That will work if you are using a nividia card that needs that driver, because there are issues with a lot of the nvidia drivers. If you do not use the same driver as I do and there is one active for you but it shows another one also switch to that one.

---

