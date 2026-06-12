---
title: "ubuntu 12.04 doesn't recognize my graphic card driver"
date: 2012-07-19
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ty74 on 2012-07-19
I have always had trouble with my graphic on my dell dimension 4700. I change the screen resolution and that fix most of my problems but when I go into the details app on ubuntu it says for graphic unknown and for drivers unknown and experience standard. The status texts are always messed up, but now videos are messed up for youtube the sound keeps going but the picture freezes. I have chromium as my browser and adobe flash plug in. when I use movie player it corrupt the texts for everything and makes the screen blurred. I can live with it but it would be great if it could be fix. thanks for taking the time to read this post.

---

### Post by KaisaUbun2 on 2012-07-20
> **ty74 said:**
> I have always had trouble with my graphic on my dell dimension 4700. I change the screen resolution and that fix most of my problems but when I go into the details app on ubuntu it says for graphic unknown and for drivers unknown and experience standard. The status texts are always messed up, but now videos are messed up for youtube the sound keeps going but the picture freezes. I have chromium as my browser and adobe flash plug in. when I use movie player it corrupt the texts for everything and makes the screen blurred. I can live with it but it would be great if it could be fix. thanks for taking the time to read this post.

Try installing the nvidia drivers 
```

sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-current
```

if this doesn't work you may have a hybrid graphic card and you must use bumblebee but try this first. Unless of course you have only an integrated card then another solution maybe necessary or if you have a radeon

---

### Post by ty74 on 2012-07-21
I type the commands in one at a time. It said I need the ubuntu 12.04 cd. then I typed them in all at once and gave this line Error: need a repository as argument.

---

### Post by gifford on 2012-07-29
From your last post it sounds like you do not have repositories activated. Do you have synaptic installed? Also, did you add the x-swat repository as suggested?

---

### Post by ty74 on 2012-07-30
Yes I have synaptic install, but I do not have  x-swat repository  installed. Can you walk me through the steps.

---

### Post by gifford on 2012-08-03
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-current

This was all included in KaisaUbun2 post.

---

### Post by ty74 on 2012-08-04
I have a Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04) will the command still work? I tried it before and it says ppa needs an argument, if type all at once and if type separate, needs to insert a ubuntu 12.04 live cd.

---

### Post by gifford on 2012-08-04
I'm sorry...just assumed you have Nvidia graphics. Did you run the command
 lspci | grep VGA 
to determine your graphics controller?

So, maybe some more information about your computer would help. How much memory does it have? What is the cpu?, etc.

---

### Post by ty74 on 2012-08-04
I did that command and got  Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04). I have an intel pentium 4 processor and 512mb of ram (pretty sad I know). I will look for the cpu.

---

### Post by ty74 on 2012-08-04
It is a 2.80GHz cpu.

---

### Post by gifford on 2012-08-04
Are you running Unity or Unity 2d? You answered the question about the cpu...pentium 4.

---

### Post by ty74 on 2012-08-04
I have unity. I do have the intel pentuim 4 processor with 2.80GHz cpu.

---

### Post by ty74 on 2012-08-06
dell dimension 4700 desktop with 512MB RAM and ubuntu 12.04 32-bit.

---

