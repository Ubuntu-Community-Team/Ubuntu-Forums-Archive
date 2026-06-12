---
title: "Modify Unity Application Launcher"
date: 2012-04-30
forum: Desktop Environments
---

### Post by axe87 on 2012-04-30
I need to change the executable path to an existing application launcher in Unity. Does anyone know where I can find the configuration? I've looked in ~/.local/share/applications but can't see the configuration for my application, in this case Eclipse.

---

### Post by wojox on 2012-04-30
Look in /usr/share/applications
You may have to copy it to ~/.local/share/applications

---

### Post by axe87 on 2012-05-01
I don't see anything relevant in /usr/share/applications.

Eclipse is installed in a separate opt directory.

---

### Post by wojox on 2012-05-01
> **axe87 said:**
> I don't see anything relevant in /usr/share/applications.

Eclipse is installed in a separate opt directory.

Of course it was not that easy. :p

Have you loooked at this [How to pin Eclipse to the Unity launcher?]("http://askubuntu.com/questions/80013/how-to-pin-eclipse-to-the-unity-launcher")

---

### Post by axe87 on 2012-05-03
Wojox,

Thanks yes, I checked it out but it doesnt help. I can't seem to get rid of the orginal launcher with the wrong path in it. Surely Unity stores the launcher configuration somewhere?

---

