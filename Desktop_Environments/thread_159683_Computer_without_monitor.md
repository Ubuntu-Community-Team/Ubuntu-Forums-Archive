---
title: "Computer without monitor"
date: 2006-04-13
forum: Desktop Environments
---

### Post by Smika on 2006-04-13
Hello,

I hope this is the right place for ask my question.
I have a loptop with Linux and a desktop PC with also Linux (without a monitor). I want that i can use the desktop PC from my laptop. So on the monitor of my laptop i can see what i do on my desktop PC.

Anybody can help me? thanks  a lot!!!

Smika

---

### Post by Ubuntuud on 2006-04-13
Unless you wish to open your laptop and do some experimental things, this is impossible, there isn't a vga/dvi entrance on such a monitor, all integrated.

---

### Post by Smika on 2006-04-13
Sorry for my bad english. I very tired.

I mean that i want use vnc software like netop or somethig like that, but i don;t know what kind of software i can use on linux.

---

### Post by JeyGordon on 2006-04-13
You may want to try FreeNX ([http://developer.berlios.de/projects/freenx/]("http://developer.berlios.de/projects/freenx/"))

Another possible alternative would be NoMachine NX ([http://www.nomachine.com/]("http://www.nomachine.com/"))

The advantage of these over VNC applications is that they are more secure and make more efficient use of the available bandwidth by compressing at the X layer and tunneling over SSH.

Of course, if you need to use VNC, you can install TightVNC([http://www.tightvnc.com/]("http://www.tightvnc.com/"))

---

