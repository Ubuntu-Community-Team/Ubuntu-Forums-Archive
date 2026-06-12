---
title: "Everyrhing is disabled on beryl?how do u undisable?"
date: 2007-05-27
forum: Desktop Effects &amp; Customization
---

### Post by ENN0 on 2007-05-27
Ok..im preety anoyed because i wanted beryl fr all the fancy moves...but its all disables...the rain,cube,fade to desktop,wobbly windows...you name its disabled??how do i undisable it so i can use it?

---

### Post by Ub1476 on 2007-05-27
You kinda need to start from the beginning if anyone should be able to help you..

What's your graphic card?

How did you install Beryl?

---

### Post by ENN0 on 2007-05-27
> **Ub1476 said:**
> You kinda need to start from the beginning if anyone should be able to help you..

What's your graphic card?

How did you install Beryl?

My graphics card is an ATI accelerated graphics driver(wich i had to activate trough riestricted drivers manager)

and i instaled it trough this forum,with the source code's

---

### Post by Ub1476 on 2007-05-27
Are you running in a XGL session? If not, Beryl will not work for you.

---

### Post by bapoumba on 2007-05-27
@ ENN0: moved your thread to "Desktop Effects & Customization".

---

### Post by ENN0 on 2007-05-27
> **Ub1476 said:**
> Are you running in a XGL session? If not, Beryl will not work for you.

what is an xgl session?i doubt i was,i can do the basic in beryl like move windows and all the simple commands...but not the good stuff!!

---

### Post by Ub1476 on 2007-05-27
Okay, here's what you gotta do: 

1) uninstall beryl:

```
sudo aptitude remove beryl beryl-core beryl-manager beryl-plugins beryl-plugin-data beryl-settings beryl-setting-bindings libberyldecoration0 libberylsettings0 libemeraldengine0
```

2) Install beryl and XGL: [Link to guide]("http://ubuntuguide.org/wiki/Ubuntu_Feisty#How_to_install_Beryl_.28ATI.29")

Scroll down to ...Alternate method: Using closed source FGLRX drivers from ATI... and start the guide from there.

Good luck;)

---

