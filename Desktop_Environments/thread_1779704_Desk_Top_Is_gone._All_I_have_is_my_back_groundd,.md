---
title: "Desk Top Is gone. All I have is my back groundd,"
date: 2011-06-10
forum: Desktop Environments
---

### Post by xbostonirishx on 2011-06-10
I was messing with something in comzig, and all of a sudden I got some window saying there was a conflict with something. I could've go back, and now all i have is my desk top back ground.  IHow do i fix this? I am new to linux, Right now at my surrent lefel of understanding, and current situation, I cant access anything, 

Please help. 

Boston,

---

### Post by sent17inel on 2011-06-10
try running this in terminal and then restart the computer.

> gconftool-2 --recursive-unset /apps/compiz

---

### Post by xbostonirishx on 2011-06-10
How do I open my terminal? is there a keyboard short cut?

---

### Post by sent17inel on 2011-06-10
> **xbostonirishx said:**
> How do I open my terminal? is there a keyboard short cut?

try restarting and before you login. look to the bottom of your screen and try logging in as "classic ubuntu" and then navigate to terminal and paste the code
```
gconftool-2 --recursive-unset /apps/compiz
```

then restart and before you login switch it back to the regular ubuntu session. it will probably make more sense once you see it so just get to the login screen first. good luck!

---

### Post by xbostonirishx on 2011-06-10
Not working, I tried rebooting into safe mode, went into root shell, but no luck there. Totally lost. 

 No option for that

---

### Post by xbostonirishx on 2011-06-10
There wasnt an option for classic

---

### Post by sent17inel on 2011-06-10
> **xbostonirishx said:**
> There wasnt an option for classic

[http://news.cnet.com/i/ne/p/2008/1029Ublogin-screen540x405.jpg](http://news.cnet.com/i/ne/p/2008/1029Ublogin-screen540x405.jpg)

do you see where it says options in the bottom left?

it should say like session or something if you are on the new natty narwal and it should be at the bottom but in the middle of the screen. Is this where you were looking??

---

### Post by xbostonirishx on 2011-06-10
this is the only screen that comes up. Not even a splash screen. I may just have to reload this. I wouldnt be loosing anyting exceot for what I did since yesterday. But I Don't want to give up that easy

---

### Post by sent17inel on 2011-06-10
> **xbostonirishx said:**
> this is the only screen that comes up. Not even a splash screen. I may just have to reload this. I wouldnt be loosing anyting exceot for what I did since yesterday. But I Don't want to give up that easy

try this and see if it gets you to the login screen to try my aforementioned instructions.

```
alt+SysRq+K
```

---

### Post by xbostonirishx on 2011-06-10
I have absolutely no idea what i have done now, but I got frustrated and hit a bunch of button on my key beard and now my entire screen is black and I seem to be in the terminal. I tried that recon command and nothing came up after it. Also I have no idea how to get out of this screen or what to do next. Any ideas?

---

### Post by sent17inel on 2011-06-10
if you tried the gcon command then go ahead and reboot and see if the issue resolved itself. If not, might as well do a quick re-install.

---

### Post by xbostonirishx on 2011-06-10
Thanks for the help. I'm doing the reinstall now.

---

### Post by sent17inel on 2011-06-10
no problem. sorry I couldn't help. When I fist got into linux in 2007 I had to do a fresh install every day because I kept breaking my install soo it happens.

---

### Post by xbostonirishx on 2011-06-10
Glad that I;m not the only one. Good thing I have a windows box next to me. Man  scanreg/restore would be A BEAUTIFUL OPTION here. But I wont get on here and complain about linux. I'd rather complain about windows.

---

### Post by liztrd on 2011-06-10
Try this
step 1. restart
step 2. when login window show up,select the "Safe Desktop Mode"(or"Safe Genome Desktop"...something) on the bottom panel.
step3 sudo apt-get purge compiz
step 4. restart
step 5. reinstall compiz

---

### Post by xbostonirishx on 2011-06-11
Thanks again, Im reinstalled, and back and up in runing. the reinstall only took about 10 minutes.

---

