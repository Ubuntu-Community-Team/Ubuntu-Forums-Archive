---
title: "Regnum online - Unsuported video card"
date: 2009-08-26
forum: Gaming &amp; Leisure
---

### Post by PallasAthena on 2009-08-26
I have recently downloaded Regnum Online for Ubuntu, but when I install it I get the error that my video card is not supported. Normally this would be because my computer can't run the graphics I suppose, but I have installed and played the game when using Windows XP, of course with the Windows version, on the same computer and there was no complaint against the poor quality of my hardware... 
I was wondering if there was some way to lower the graphics of the game, thus enabling me to run it on Ubuntu? 
I chose the game so that I could play it on Ubuntu when my Windows broke down again (which it obviously did), so I was quite dissapointed when the Linux-version did not accept my video card, where the windows one did. While I'm vagely proud that the Linux-version has higher standards, it's still annoying. :)

---

### Post by donkyhotay on 2009-08-26
What kind of video card are you using and what driver versions to you have installed for it? Also what version of ubuntu do you have?

---

### Post by Bölvaður on 2009-08-26
To find out what card you have:
open the terminal (applications &#8594; accessories &#8594; terminal) and paste (ctrl+shift+v) this command
```
lspci | grep VGA
```

Now to find out what driver you have:
```
glxinfo | grep client
```
I feel like Im forgetting something. It might be that my last command is not to find what is installed, but Im sure enough that it will tell us something.

---

### Post by PallasAthena on 2009-08-26
Message 1:
*00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)*

Message 2:
[I]get fences failed: -1
param: 6, val: 0
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GL_3DFX_texture_compression_FXT1, GL_APPLE_client_storage, [/I]

:confused: While the first seems pretty straightforward, I'm rubbish at deciphering the second one... I hope it was the answer, just following the commands :oops:
I'm so ashamed of my ignorance right now...

---

### Post by Bölvaður on 2009-08-26
yes this is the great intel problem I would assume.
Follow the *Optimal* Configuration* in this thread:

[http://ubuntuforums.org/showthread.php?t=1130582]("http://ubuntuforums.org/showthread.php?t=1130582&highlight=lspci+|+grep+VGA")

There is not much you need to understand, just copy and paste, but make sure you read about what you are doing, as it isnt 100% copy and pasting. You'll need to use your own judgement sometimes.
Also when you reboot your computer to get into the new kernel pick *2.6.30-02063003-generic* from GRUB, there is no use using newer kernel if it doesnt help you. (newer kernels go at top of the list in grub)

There is a way further down the how-to thread on how to revert the changes if everything goes bananas.

---

### Post by PallasAthena on 2009-08-26
I have done the safe part, but it still doesn't work. Should I follow the instructions further for optimal or cutting edge? Or is my video card doomed to fail?

---

### Post by Bölvaður on 2009-08-27
> **PallasAthena said:**
> I have done the safe part, but it still doesn't work. Should I follow the instructions further for optimal or cutting edge? Or is my video card doomed to fail?

Safe doesnt do very much, what you really need is the kernel, so follow the instructions for Optimal like I stated in my last reply. Also check that post for information on how to boot into it (otherwise you will not gain anything from installing it if you dont use it)

---

