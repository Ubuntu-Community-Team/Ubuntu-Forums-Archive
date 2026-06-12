---
title: "built in mic and webcam issue ?"
date: 2008-05-22
forum: Dell Ubuntu Support (CLOSED)
---

### Post by cooldudeny on 2008-05-22
i am not been able to figure it out if my built in cam and mic is working on ubuntu 8.04 ?

can someone help me with this

---

### Post by Keyper7 on 2008-05-22
> **cooldudeny said:**
> i am not been able to figure it out if my built in cam and mic is working on ubuntu 8.04 ?

can someone help me with this

Go to applications > sound & video > sound recorder
(or something like that, my Ubuntu is in portuguese so I'm not sure)

This is a very simple and straightforward recording software, it should be enough to test if the mic is working. Toy with it and if it does not work try changing the volume settings (right click on the volume applet on the top right corner and select 'volume control')

For the cam, if you are using Hardy there should be an application called "cheese" installed by default (if I remember correctly, on the 'graphics' or on the 'sound and video' submenu, I'm not sure). If you're not using Hardy, cheese is not installed by default. You can either install it with

sudo apt-get install cheese

or try to test your camera with ekiga (applications > internet > softphone). There should be a camera button in ekiga to activate your camera.

PS: In ekiga, you might need to go the preferences and set video input to v4l2 (video 4 linux 2), because your cam might not support v4l (mine didn't).

Let me know if you have any problems.

---

