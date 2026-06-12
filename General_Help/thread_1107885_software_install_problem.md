---
title: "software install problem"
date: 2009-03-27
forum: General Help
---

### Post by simonlugi on 2009-03-27
I have recently installed Kubuntu. At first everying went well.
Now when I try and install software through Adept I get the following mesage

APT Error. Context:
    Package download failed, 
    I wasn't able to locate a file for the sun-java6-bin package. This might mean you need to manually fix this package. (due to missing arch), 
    I wasn't able to locate a file for the sun-java6-jre package. This might mean you need to manually fix this package. (due to missing arch), 
    : , 
    : , 
    : , 
    : , 
    : , 
    : , 
    : , 
    : 

Can someone give simple to follow instructions what I need to do to fix it.

---

### Post by HavocXphere on 2009-03-27
Not entirely sure whether its the same, but my Kubuntu+Java hassles were fixed by:

sudo apt-get install sun-java6-jre sun-java6-plugin
sudo update-alternatives --config java

---

### Post by simonlugi on 2009-03-27
No unfortunately that did not work for me.

---

### Post by simonlugi on 2009-03-27
Reading package lists... Done
The following is the message I recived in Konsole

Building dependency tree
Reading state information... Done
Package sun-java6-plugin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-plugin has no installation candidate

---

### Post by hyper_ch on 2009-03-27
sun java is not open source and hence it is not in default repos. You have to enablue universe or multiverse in order to get access to sun java.

---

### Post by simonlugi on 2009-03-27
How do I do that?

---

### Post by SuperSonic4 on 2009-03-27
[https://help.ubuntu.com/community/Repositories/Kubuntu](https://help.ubuntu.com/community/Repositories/Kubuntu)

---

### Post by simonlugi on 2009-03-27
I have managed to figure out where I have been going wrong. I had not accepted the Sun Java licence agreement. 
For those who may also have this problem 
When you get to the blue screen showing Sun Java Terms and Conditions scroll down to the bottom. Press the forward arrow at the bottom of the text terms which should highlight <Ok> hit Enter and the y enter.

Thanks for your help

---

### Post by hyper_ch on 2009-03-28
btw,for managing your repos you can also use my tool in my sig. 

How big is your screen? I usually see that "OK" thing upon java installation when I install it.

---

### Post by simonlugi on 2009-03-31
I am using a 19inch screen

---

