---
title: "Ok, one more"
date: 2005-12-15
forum: General Help
---

### Post by tanis143 on 2005-12-15
I promise this is my last question for the day. I'm just exicted that there are other options to gaming than windows and really want cedega to work. However, when I goes to do the test, it fails on the opengl test. Says my driver is not configured properly. I've already checked that the opengl packages are installed, and it does recognize my vid card correctly. What can I do from here? And please, if you ask me to do something, give me commands, I'm very new to linux (in fact, less than 24 hours, though I do have a little bit of knowledge).

---

### Post by wylfing on 2005-12-15
First, what video card do you have?

Second, you could try the old standby test program: glxgears. Just open a command line terminal and type 
```
glxgears
```
hit Enter and see if it runs. If you get a segmentation fault there's something wrong with your OpenGL setup.

---

### Post by tanis143 on 2005-12-16
Its an FX5200 128bit 128meg vid card. I can not remember the manufacturer though. Here is what I got when I tried glxgears:

```
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual
```

---

### Post by Rinzwind on 2005-12-16
[QUOTE=tanis143]Its an FX5200 128bit 128meg vid card. I can not remember the manufacturer though. Here is what I got when I tried glxgears:

```
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual
```[/QUOTE]

edit your xorg.conf and make sure that

Load GLX
Load dri

are there and not commented out!

From what I've seen this is mostly the problem.
After that run the glxgears again ;)

---

### Post by tanis143 on 2005-12-16
It does the same with those lines commented out and with them not commented out. By default they were not commented out, however I read somewhere they needed to be. If I make changes to the xorg.conf file do I need to restart the xserver?

---

### Post by tanis143 on 2005-12-16
*sigh* I feel so new, its not even funny. I've tried to update my nvidia drivers, but it tells me that it could not find a kernal something that matches my kernal, and cant compile it because the libc is not found. Also, I read something somewhere about having to run a command that configs the nivdia glx to enable. I dunno, I've been using linux a total of 2 days now and just getting a bit frustrated with it. I love it, and I hate it because I grew up in windows. 

Can someone give me a link to help with enabling glx and/or updating nvidia's drivers with Ubuntu 5.10?

---

### Post by wylfing on 2005-12-16
Please don't get cranky. There are a lot of possible setups and since you didn't say anything about what setup you have, it's necessary for us to ask questions to find out what's going on. And I would wager you didn't pay a single dollar for your copy of Ubuntu and not a single dollar for support. So stamping your foot about how you have to wait 2 days is kind of silly.

Now, the information you probably want is [right here](https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia?highlight=%28nvidia%29). It sounds to me like you tried to download the driver from the nVidia web site and compile your own kernel module. That is definitely possible, but it generally makes your life harder. It's much better to use the ready-made nVidia drivers available in Synaptic. ([Learn about Synaptic](https://wiki.ubuntu.com/SynapticHowto?highlight=%28synaptic%29).)

I'm guessing that the compilation of your custom drivers failed, and that's probably for the best, because nothing got installed. Just go ahead and follow the instructions linked above and you'll be fine.

---

