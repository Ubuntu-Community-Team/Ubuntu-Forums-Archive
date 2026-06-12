---
title: "Minecraft - Slow FPS"
date: 2014-02-07
forum: Gaming &amp; Leisure
---

### Post by Askaron on 2014-02-07
Hello everyone. I recently installed Lubuntu 64 bit as a virtual hard disk on VirtualBox (3.5 GB Ram dedicated).
I installed both openjdk 6 and 7. I then downloaded Minecraft.jar. 
The game appears to be really slow. 

So I decided to run it with terminal, to see what happens ```
java -jar Minecraft.jar
```

Here's what the terminal tells me when I use Openjdk 7 as default:

```
[13:27:27 INFO]: Client> [13:27:27] [Client thread/ERROR]: @ Post render
[13:27:27 INFO]: Client> [13:27:27] [Client thread/ERROR]: 1280: Invalid enum
[13:27:27 INFO]: Client> [13:27:27] [Client thread/ERROR]: ########## GL ERROR #

```

This is the last thing the terminal tells me when I quit the game:

```
[14:41:10 ERROR]: java.io.IOException: Stream closed
```


Same happens with Openjdk 6 set as default.
Please help me :(

---

### Post by jonifen on 2014-02-07
Have you enabled 3D acceleration for the VM? Just wondering as the error reports "GL ERROR" which I presume to be "OpenGL".

---

### Post by sffvba[e0rt on 2014-02-08
3D acceleration in virtualization is poor and I seriously doubt you will get a decent gaming experience using Virtualbox.

---

### Post by Askaron on 2014-02-08
Thank you for your replies. I tried to enable 3d acceleration, and the **game is** now **playable**, **until I get the** same **errors** stated in my first post. From that moment on, the game becomes unplayable: I can't move properly, since the character looks up and down all the time.
I actually don't think it's a problem related to VBox: since Minecraft only needs 1 GB Ram, and I gave 3.5 GB Ram to Lubuntu (and Xubuntu, the other system I'm using), I think it's something else causing it. In addition, the game is actually playable, until I get those errors.

---

### Post by xREDEMPTIONx on 2014-02-08
May I ask why your trying to run the game in Virtualbox in the first place? Why not just run it on the desktop you are running Vbox in? Minecraft runs great on Linux with openjdk. You will get much better performance there because the Vbox graphics drivers are not making full use of the graphics capabilities of your host system even with 3d acceleration enabled. I've tried running several different games in Vbox and every single on either ran horribly or didn't run at all. I can almost guarantee your issue is because of Vbox.

---

### Post by Askaron on 2014-02-10
Ok, thanks for the information. Too bad I can't properly install a Linux OS without getting the GPT partition problem with Gparted. I need to solve this problem.

---

### Post by dannyboy79 on 2014-02-10
do you have another thread for your "gpt partition" problem? i'd be interested in helping and I am not aware of any "gpt partitioning" problem in linux

---

### Post by Askaron on 2014-02-10
> **dannyboy79 said:**
> do you have another thread for your "gpt partition" problem? i'd be interested in helping and I am not aware of any "gpt partitioning" problem in linux

Thank you, but I managed to solve the problem (seems like I formatted a GPT, and created a new MBR partition table over that with a tool that doesn't understand GPT. FixDisks helped me fixing it).
I now have Minecraft running properly on Ubuntu, dual boot. :p

---

