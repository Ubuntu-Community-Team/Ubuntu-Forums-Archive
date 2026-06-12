---
title: "Nautilus window background goes black when using custom themes"
date: 2014-11-24
forum: Desktop Environments
---

### Post by yousufinternet on 2014-11-24
I am facing a problem when using custom themes in ubuntu 14.04 64-bit unity interface, such as the mbuntu-y theme appearing in the screenshot attached, as you can see the background of nautilus window goes black sometimes when using custom themes, this does not happen when I use Ambiance or Radiance themes.. I have to switch the view to list view and then back to icon view to get the white background again, the same thing occurs when using the nemo file browser..

I haven't been lucky on my search for a solution, I only found someone who has posted the same problem without receiving any answers: [http://askubuntu.com/questions/552075/background-of-nautilus-go-black](http://askubuntu.com/questions/552075/background-of-nautilus-go-black)

Please advice on the source of this problem, and on how to solve it..

Thanks in advance :)

Screenshot: [http://i58.tinypic.com/35n1quw.png](http://i58.tinypic.com/35n1quw.png)

---

### Post by Frogs Hair on 2014-11-24
I can't duplicate the problem and I see there are 3 themes included for different desktops . If you are using Unity make sure you are using the designated theme and also make sure you have a 14.04 compatible version of the theme.

---

### Post by yousufinternet on 2014-11-25
Unfortunately every thing is as it should be and the problem still exists, and not only with this theme but with every theme except the default themes (Radiance and Ambiance).. :(

---

### Post by Frogs Hair on 2014-11-25
How and where were the themes installed ?  Was it via PPA or manually in .themes or usr/shsre/themes ?

---

### Post by yousufinternet on 2014-11-25
> **Frogs Hair said:**
> How and where were the themes installed ?  Was it via PPA or manually in .themes or usr/shsre/themes ?

Thanks for caring to help, they were installed via PPA, I didn't try to install them manually..

---

### Post by Frogs Hair on 2014-11-25
You could try installing the synaptic package manager removing and reinstalling the themes . I have a few NoobsLab themes from PPA and they work as expected. In synaptic you can right click to remove or reinstall.

---

### Post by yousufinternet on 2014-11-26
Tried that also and it didn't help.. 

fortunately, I have found this temporary workaround to solve the problem: 
[https://github.com/shimmerproject/Numix/issues/121](https://github.com/shimmerproject/Numix/issues/121)

the workaround is to disable the overly scrollbars when using custom themes, this can be done with the following command: 

> gsettings set com.canonical.desktop.interface scrollbar-mode normal

---

