---
title: "Engineering softwares in ubuntu8.04"
date: 2008-10-06
forum: Education &amp; Science
---

### Post by F.Soroush on 2008-10-06
Hi 
I'm a new user of ubuntu and also an angry one of windows xp #-o!!!(it's a big story!!!)
I'm also having following specifications:
I'm student of mechanical engineering and working so much with ansys 
I've dell vostro 1500 note book:popcorn:
now these are my questions:
1:confused:**How can i install ansys**11.0 workbench in ubuntu? also how for fluent and other engineering softwares?
2:(:(:((may be it's not a good place to say!!)my windows do not shut down properly....takes too long(i didn't measure it because each time i turned it off with key!!!!!!) and by this problem my ubuntu does not mount my drives??????how can i repair it????
3now my friend is hear and told me that he has a same problem with mounting drives!!! ha said that he had also the same problem like me with windows and by changing it,it was repaired!!!!
**so what's the problem with mounting???**
4what would happen if i clean windows xp and use ubuntu for ever??
imean may i have problem with future release of softwares???
thanks for helping!!!!!
help ........please!!!!

---

### Post by thelinuxer on 2008-10-06
> **F.Soroush said:**
> Hi 
I'm a new user of ubuntu and also an angry one of windows xp #-o!!!(it's a big story!!!)
I'm also having following specifications:
I'm student of mechanical engineering and working so much with ansys 
I've dell vostro 1500 note book:popcorn:
now these are my questions:
1:confused:**How can i install ansys**11.0 workbench in ubuntu? also how for fluent and other engineering softwares?
2:(:(:((may be it's not a good place to say!!)my windows do not shut down properly....takes too long(i didn't measure it because each time i turned it off with key!!!!!!) and by this problem my ubuntu does not mount my drives??????how can i repair it????
3now my friend is hear and told me that he has a same problem with mounting drives!!! ha said that he had also the same problem like me with windows and by changing it,it was repaired!!!!
**so what's the problem with mounting???**
4what would happen if i clean windows xp and use ubuntu for ever??
imean may i have problem with future release of softwares???
thanks for helping!!!!!
help ........please!!!!

1. Installing engineering software depends on the software installation itself. What I mean is that matlab will be different than ansys for example. You will have to "READ" the installation manual to get it right. 

3. The problem with mounting is that the partition is marked as dirty so it can't be mounted. You can fix this by one of two ways.
   a. Boot into windows then shutdown or reboot. This will fix the partition.
   b. Force mount on ubuntu using this command 
      ```
sudo mount -t ntfs-3g *drivename* *mountpath* -o force 
```

4. I have been using Linux for about 4 years now. For over a year I totally ditched windows. I didn't miss it for a sec. :) .  I found all the replacements I needed. You can find lots of information about replacements of Google. With ubuntu there is almost no problems updating ur distro on every new release.

Regards

---

### Post by F.Soroush on 2008-10-07
your opinion helped me so much "thelinuxer".....thanks very much ....
today i found linux version for fluent but in ansys help for installation and licensing didn't find installation for ubuntu.....it was only for redhat and another one that i do not remember now......
now i've mounted drives all(but without code.....thanks for code also!!)
wish u all luck ......
and wish for windows shut down!!!!!!:D:D
one question!!
does ubuntu has viruse???

---

### Post by Xnst on 2008-10-07
Hi,

I do not know how ansys is doing it, but to install abaqus on ubuntu you have to override the systemcheck. You can do it by giving the installer --no-systemcheck as input or edit the install script to exclude the system check. You probably can do the same with ansys.

best of luck

Niclas

---

### Post by thelinuxer on 2008-10-07
> **F.Soroush said:**
> your opinion helped me so much "thelinuxer".....thanks very much ....
today i found linux version for fluent but in ansys help for installation and licensing didn't find installation for ubuntu.....it was only for redhat and another one that i do not remember now......
now i've mounted drives all(but without code.....thanks for code also!!)
wish u all luck ......
and wish for windows shut down!!!!!!:D:D
one question!!
does ubuntu has viruse???

I guess the ansys installation is only supported on Redhat enterprise and OpenSuse ( but I am not sure though ). I haven't got the installation CD so I can't help you to install it on ur ubuntu box. Perhaps you should contact the support and tell them about ur problem. 

About ur virus question. I will rephrase ur question. Does GNU/Linux have viruses ? The answer is yes, any operating system has its viruses, but on Linux there is only a limited number of viruses and impact is really minimal. If you want to know more please read this article

[http://www.theregister.co.uk/2003/10/06/linux_vs_windows_viruses/](http://www.theregister.co.uk/2003/10/06/linux_vs_windows_viruses/)

Hope that answers ur question :wink:

---

### Post by F.Soroush on 2008-10-08
Thanks for viruses!!!!!
i enjoyed it so much!!

---

### Post by F.Soroush on 2008-10-09
hi
today i done a sudden job and started to install ansys 11.0 SP1 in my ubuntu8.04!!!!
wine started the work standard but in flexlm manager i did a sudden closing!!!!!!! it mean's that ansys can be installed in ubuntu by using wine, but you have to know your computer name , the thing that i do not know and i want it to copy in license.dat file!!!!
question is it: how can i know what's my host name or my computer name?????
so wine solve ansys problem easily.

---

