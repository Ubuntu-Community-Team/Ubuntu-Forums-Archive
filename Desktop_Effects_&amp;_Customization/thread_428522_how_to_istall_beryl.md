---
title: "how to istall beryl"
date: 2007-04-30
forum: Desktop Effects &amp; Customization
---

### Post by emres on 2007-04-30
I am an absolute beginner.and i want to install beryl. i have nvidia geforce3. ubuntu edgy is installed. please, can someone tell me how to install beryl?
thank you before you help:)

---

### Post by Seisen on 2007-04-30
[http://ubuntuguide.org/wiki/Ubuntu:Edgy#How_to_install_Beryl.2FAIGLX_.28Nvidia.29]("http://ubuntuguide.org/wiki/Ubuntu:Edgy#How_to_install_Beryl.2FAIGLX_.28Nvidia.29")

Try this and see if it works.

---

### Post by bodhi.zazen on 2007-04-30
first install the nvidia driver. Easiest way is via envy :

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

Go for the "unstable" version ;)

Then install beryl.


=====

Next add this line to sources.list :

In a terminal : ```
gksudo gedit /etc/apt/sources.list
```

Add this line (at the bottom of the file):> deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) edgy main 

Now, again in a terminal,

```
sudo wget http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg -O- | sudo apt-key add -
```

======

Install beryl :

In a terminal : ```
sudo apt-get update
sudo apt-get install beryl emerald emerald-themes
```

Now restart X (log out and back in)

Open a terminal and type:```
beryl-manager
```

If you have problems you may need to edit /etc/X11/xorg.conf (gksudo gedit /etc/X11/xorg.conf) :

Add these lines to the "devices" section :> Option "AddARGBGLXVisuals" "True"
Option "RenderAccel" "True"
Option "AllowGLXWithComposite" "True"
Option "backingstore" "True"
Option "TripleBuffer" "True"

re-start X again ...

type beryl-manager again ...

---

### Post by emres on 2007-04-30
I installed beryl but when i try to access beryl manager, i see black screen and then username and password screen. after i see the desktop, again black screen.now i cannot use my ubuntu. How can i fix it?

---

### Post by bodhi.zazen on 2007-04-30
There are sooo many potential problems ....

well, can you provide more details ?

Did you install the nvidia driver ? How ? is it working ?

Error messages ?

Look in or post /var/log/Xorg.0.log

and a copy of /etc/X11/xorg.conf

---

### Post by chunchengch on 2007-04-30
1. I would recommend you to install Ubuntu 7.04 (Feisty Fawn)
2. Refer to my previous thread "Personal summary of installing and enabling Beryl in Feisty", I am sure that you will enjoy Beryl soon!:)

---

### Post by chunchengch on 2007-04-30
I am a Linux newbie and have a laptop with nVidia GEFORCE GO 7300 (128MB), I tried and failed many times to install Beryl, however, I found the solution finally, and now the Beryl is working gorgeously and stably.

---

### Post by emres on 2007-05-03
i dont remember exactly cause i cannot use ubuntu, but somewhere it detects hardware and needed drivers and download and install in terminal. after that, i did everything  what bodhi.zazen said. now i will install ubuntu again.and upgrade to 7.04 and of course i ll try again. thanks

---

