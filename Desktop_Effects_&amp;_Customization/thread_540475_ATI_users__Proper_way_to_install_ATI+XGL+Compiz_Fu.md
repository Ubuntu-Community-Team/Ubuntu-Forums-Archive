---
title: "ATI users : Proper way to install ATI+XGL+Compiz Fusion"
date: 2007-09-01
forum: Desktop Effects &amp; Customization
---

### Post by hidden_leaf_sasuke on 2007-09-01
This tutorial is for ATI users only . For ATI graphics cards, the things you have to do is this ;

1.Install propriety driver
2.Install XGl (and remove the fglrx)
3.Install Compiz- Fusion
4.Done.

For installing Propriertary Driver , go to System > Administration > Restricted Driver Manager and enable the ATI driver.

For installing XGL , go [HERE]("http://ubuntu4life.blogspot.com/2007/08/installing-atixglcompiz-fusion.html") and for installing Compiz-Fusion go [HERE]("http://ubuntu4life.blogspot.com/2007/07/lets-get-started.html").

Dont just install Compiz Fusion just like that. I'll cause problem and it wont start. Follow the steps and you dont have problem. 

Problems occur when :
1. You dont install the right way
2. You have broken dependencies ( make clean uninstall then )
3. You dont install XGL ( its serious dude, it can make some freeze )
4. You messed up with your xserver conf. Try to backup ( if you have one ). If not, make a fresh installtion. Dont mess with xserver unless you got experience with it.

---

### Post by Tiger-Smith on 2007-09-01
Fglrx is part of the ATi proprietary driver.

---

### Post by hidden_leaf_sasuke on 2007-09-01
yes, but it has to be removed

---

### Post by hidden_leaf_sasuke on 2007-09-01
guys, if this tutorial is not working (or working) please leave a comment.

---

### Post by Tiger-Smith on 2007-09-01
If you remove Fglrx then you remove the kernel base for the ATi Proprietary drivers, which inturn means no hardware acceleration, which inturn means no Fusion, you can remove the old versions of Fglrx but they still have to be replaced unless your using OpenSource drivers, in which case you wont be using Fusion because their not supported...

---

### Post by hidden_leaf_sasuke on 2007-09-01
fglrx is removed to be replaced by xorg open source driver. using fglrx is not recommended. i've tried it before, man it really slows down my computer all the times. that's why we need open source driver. its way better than fglrx driver. and i dont have problem to run compiz fusion with open source driver (actually, its faster and better).

---

### Post by erfahren on 2007-09-01
We install XGL to enable the use of desktop effects *with* the proprietary ATI driver fglrx. The driver doesn't natively support desktop effects by itself (the way I understand it). 

I use a combination of these howtos:
[http://ubuntuforums.org/showthread.php?t=482773](http://ubuntuforums.org/showthread.php?t=482773)
[http://ubuntuforums.org/showthread.php?t=488385](http://ubuntuforums.org/showthread.php?t=488385)
and the [*Updated* Compiz Fusion Guide on Ubuntu 7.04](http://ubuntuforums.org/showthread.php?t=481314) --(that one seems to be closed and defunct now --- hmm... interesting.) 

I think those pretty much already cover it.

Anyway, if using XGL the only reason to remove the fglrx driver is to install a newer version than what's available in the Ubuntu repositories. The guides you linked to (which seem to be basically the same has the howtos above) make no mention of removing fglrx. Maybe you should check them out again.

oh, you posted this while I was posting:
> 
fglrx is removed to be replaced by xorg open source driver. using fglrx is not recommended. i've tried it before, man it really slows down my computer all the times. that's why we need open source driver. its way better than fglrx driver. and i dont have problem to run compiz fusion with open source driver (actually, its faster and better).

I had problems with the open-source driver personally. The suspend function didn't work if I remember correctly. There are a myriad of issues with ATI cards. What works well for one person doesn't always work for another. There's another howto on the open source driver here: [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

but again, if you are enabling the proprietary driver you're not using the open-source one. The proprietary driver is fglrx.

---

### Post by Tiger-Smith on 2007-09-01
Xorg is an xserver and nothing more,  and by installing the drivers from the restricted repositories you are automatically updating fglrx, the only way to remove it would be to run open-source drivers on top but then there would be no need for Xgl and Fusion wouldn't run atall  or it might but barley haven't had a chance to test.

---

### Post by tadah on 2007-10-21
well it seems i did everything in order, in the end restarted my pc, made the last line (*compiz --replace*) and got this:

[b]
Checking for Xgl: not present.
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 
[/b]

what's the problem? ](*,)

---

### Post by tadah on 2007-10-22
No ideas? :(

---

### Post by tadah on 2007-10-26
tried again. now after *compiz --replace*:
```

Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with fglrx ATi drivers...
Starting gtk-window-decorator
/usr/bin/compiz.real (core) - Fatal: Support for non power of two textures missing
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :1.0

```

---

### Post by meindian523 on 2007-10-26
Basic fundamental is that you DON'T have to remove fglrx.

<advertisement>FOR ATi Radeon XPress 200 series cards

[http://ubuntuforums.org/showthread.php?t=567108](http://ubuntuforums.org/showthread.php?t=567108)

</advertisement>:)

---

### Post by bribaetz on 2007-10-26
well thats not the limitation of my problem. 
okay so i install all the stuff for the advanced settings but i messed up my card driver when i messed with it to see if any of them would work because i hadn't read all the threads so my comp is fine at this piont its a little crapy with the video. my card environment thingy will have a blank at the top of the window bar where you move it or close it. so i just disable it and i messed with my driver some more and i also mess with my screen settings size etc. now every time i try to log in it takes me back to the log in screen unless i use the failsafe_gnome thing with out using any extra scripts which would be okay if my mouses left click and right click weren't backwards. by the way my video card is "ATI rage 128" how might i fix this problem.

---

### Post by meindian523 on 2007-10-27
You "messed" with your card drivers?Would you please enlighten us the "messing" you did?How are we supposed to help without details?

---

