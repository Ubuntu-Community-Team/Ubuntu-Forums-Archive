---
title: "Installing Compiz Fusion Problem (Download part missing)"
date: 2007-09-26
forum: Desktop Effects &amp; Customization
---

### Post by tsumiro on 2007-09-26
hey. ive got this problem with installing compiz fusion. when i try to install using instructions from:

[http://news.softpedia.com/news/How-to-Install-Compiz-Fusion-on-Ubuntu-58113.shtml](http://news.softpedia.com/news/How-to-Install-Compiz-Fusion-on-Ubuntu-58113.shtml)

i put in this:



```
sudo apt-get -y install compiz compiz-gnome compizconfig-settings-manager compiz-fusion-plugins-extra libcompizconfig-backend-gconf

```

and then i get this:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package compizconfig-settings-manager
```

so whats up? why cant i get this file? so far, all the tutorials on how to install compiz tell you to do the same thing, and if i put in

```
sudo apt-get -y install compizconfig-settings-manager
```

or anything after that (compiz-fusion-plugins-extra, and libcompizconfig-backend-gconf)

i get the same error.... help plz?

btw im using fiesty....

---

### Post by FuturePilot on 2007-09-26
Did you run
```
sudo apt-get update
```

---

### Post by patang on 2007-09-26
Try searching for compiz in synaptic (the graphical package manager). You should see the settings manager there. Install it.

I broke my compiz once and the solution that worked was:
a) Search for compiz in synaptic.
b) Completely remove all the installed packages
c) Reinstall everything.
d) Enjoy eyecandy.

Hope this helps

---

### Post by giox on 2007-09-26
This how to might help. It shows you how to ad the repo for compiz and the key need it to download it. follow step by step from the begining. It works for me. Good luck.

---

### Post by FuturePilot on 2007-09-26
If you're using Nvidia you don't need XGL.

---

### Post by Rupertronco on 2007-09-26
Moreso, if you're using Nvidia you don't want anything to do with XGL. Do not follow that guide.

---

### Post by tsumiro on 2007-09-26
im not using nvidia. i think im using ati. im using a ibook g4, sooo... yeah. btw what exactly is the synaptic package manager???

is it the add remove programs thing in the main menu?

and i did do the update thing....

---

### Post by FuturePilot on 2007-09-26
Synaptic is the package manager. It's the backend to Add/Remove. But it's the frontend to apt-get. If that makes sense:p You can find it in System>Administration>Synaptic Package Manager. Did you try it again after updating apt?

---

### Post by tsumiro on 2007-09-26
have they changed the repos?

maybe there is another repo??? cuz i still cant find that file....


rrrrghh!

---

### Post by tsumiro on 2007-09-26
so yeah, is there another repo where i can find the manager and fusion files? cuz i seem to have all the compiz files now....

---

### Post by tsumiro on 2007-09-26
wait a seccc.... is compiz fusion for PPC too? cuz i checked i checked the link in FuturePilots sig, and its for i386 architecture....


mmmmm.,...

---

### Post by FuturePilot on 2007-09-26
That link is for the old Compiz. That won't work with Compiz Fusion. I should probably get rid of that since everyone seems to be using CF now.

---

### Post by Rupertronco on 2007-09-27
> **tsumiro said:**
> wait a seccc.... is compiz fusion for PPC too? cuz i checked i checked the link in FuturePilots sig, and its for i386 architecture....


mmmmm.,...

Compiz-Fusion is available for PPC architecture. Just make sure that those are the packages you've downloaded. Obviously the x86 version won't work for you regardless of what you do.

---

### Post by isaacj87 on 2007-09-27
I'm not sure what you guys are talking about because I used those instructions recently and they work fine. The only thing the instructions are missing is how to install emerald.

---

### Post by tsumiro on 2007-09-28
finally i fixed my first problem, and now i have this problem:


```
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  compiz: Depends: compiz-fusion-plugins-main (>= 0.5.2+git20070917) but it is not installable
          Depends: compiz-fusion-plugins-extra (>= 0.5.2+git20070917) but it is not installable
          Depends: libcompizconfig0 (>= 0.5.2+git20070912-0ubuntu2) but it is not installable
  compizconfig-settings-manager: Depends: python-compizconfig but it is not installable
E: Broken packages
```

i get this error when i put in this code:

```
sudo apt-get update && sudo apt-get dist-upgrade && sudo apt-get install compiz compizconfig-settings-manager 
```

can compiz-fusion just not be installed on PPC architecture?

anyway i got the code from here: (this was also how i got the solution to my problem...)

[https://help.ubuntu.com/community/CompositeManager/CompizFusion](https://help.ubuntu.com/community/CompositeManager/CompizFusion)

so yeah...

---

### Post by NovruzeliH on 2008-07-11
man i get this 

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package compiz-core is not installed, so not removed
E: Couldn't find package desktop-effects

```

and im using xubuntu 8 :( the latest one

---

