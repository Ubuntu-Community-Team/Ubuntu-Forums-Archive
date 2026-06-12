---
title: "Certain compiz effects in metacity - possible?"
date: 2013-01-26
forum: Desktop Environments
---

### Post by ntzrmtthihu777 on 2013-01-26
Hello all, looking into desktop customization, currently using Gnome fallback as I can't stand unity. There are a few effects in compiz I really like, but overall it gobbles too much ram, so is it possible to enable some like it in metacity, or some other light-weight alternative?

In particular I am interested in multiple desktops, desktop grid and snapping windows (able to make a window take exactly half of a virtual desktop using hotkeys/dragging to the right edge)

---

### Post by JOHNNYG713 on 2013-01-26
Compiz is compiz, by selecting just a few effects, makes compiz run faster, but still it is what it is, Compiz ! Hee Hee made a funny ! :D Metacity has a composting effect kind of an echo if you will, when icons are selected and windows open or close, you can also have multiple desktops in metacity, but it will just switch desktops, there is an app called Brightside, That will switch desktops wth a sliding effect, but I am not sure if it will do what you want, having half of an open winow hang in to an other desktop. so really, it is ether, or, but not both, cant have your cake and eat it too ! ;) or may be you can !;)

---

### Post by ntzrmtthihu777 on 2013-01-26
Any alternatives to metacity or compiz, kindof a nice medium?

---

### Post by JOHNNYG713 on 2013-01-26
Well there is E17, Enlightenment, that has heavy composting, and if you want more effects like compiz you can add ecomorph to it, by installing E17 with this ppa [https://launchpad.net/%7Emerlwiz79/+archive/e17-svn/+index#](https://launchpad.net/%7Emerlwiz79/+archive/e17-svn/+index#)
add it to your source list then
sudo apt-get update sudo apt-get install e17
then open synaptic, search e17 add all of the components except the one
that says "all" and the one that wants to install conman and remove network manager
or Cinnamon has some onboard effects !
sudo add-apt-repository ppa:gwendal-lebihan-dev/cinnamon-stable sudo apt-get update sudo apt-get install cinnamon

log out and choose the new desktop and tweak away !

---

### Post by ntzrmtthihu777 on 2013-01-26
How is that on resource use? I am trying to avoid huge hogs.

---

### Post by JOHNNYG713 on 2013-01-26
sorry, Double post

---

### Post by ntzrmtthihu777 on 2013-01-26
Umm, I hope thats a posting error on your part, as its the exact same. Could you answer my earlier question?

---

### Post by JOHNNYG713 on 2013-01-27
Sorry about that, my net connection is  similar to a piece of string and two tin cans ! Sometimes I cant tell what is going on ! any hoo, I find E17 has a bit of a learning curve, but really good on the resources, I have it on an old IBM X600 Laptop and have no issue, Cinnamon has an effects,and 2D option, both are very good, also google how to make compiz run faster, there are some tips and tricks that might be helpfull !

---

### Post by Frogs Hair on 2013-01-27
E17 has low system requirements but the PPA posted has been inactive for over a year and there are more up to date PPAS . The XFCE Session has compositing which includes some eye candy. To Install XFCE Session: This is not the same as the Xubuntu desktop 

```
sudo apt-get install xfwm4 
```
```
sudo apt-get install xfce-goodies
```

---

### Post by ntzrmtthihu777 on 2013-01-27
> **Frogs Hair said:**
> E17 has low system requirements but the PPA posted has been inactive for over a year and there are more up to date PPAS . The XFCE Session has compositing which includes some eye candy. To Install XFCE Session: This is not the same as the Xubuntu desktop 

```
sudo apt-get install xfwm4 
``````
sudo apt-get install xfce-goodies
```
Ok, sounds nice, but does it have the particular effects I was looking for? Sorry if I sound like a broken record, but I'm pretty ignorant in this particular area. I will, however, have a google about the choices you have given. Thanks for the input.

[EDIT]Um, all the info I turn up on xfce links it with xubuntu, could you please explain the distinction?

---

### Post by JOHNNYG713 on 2013-01-30
> **Frogs Hair said:**
> E17 has low system requirements but the PPA posted has been inactive for over a year and there are more up to date PPAS .
merlwiz79 is the only ppa I have found that has all e17 modules and works with natty through Quantel, even though it is a natty ppa, he does maintain it to insure it is still a viable source, please elaborate on "more up to date PPAS" that have all the modules and ecomorph, as I have not found one.

---

