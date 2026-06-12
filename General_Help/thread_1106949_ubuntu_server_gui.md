---
title: "ubuntu server gui"
date: 2009-03-26
forum: General Help
---

### Post by speedy_pg on 2009-03-26
Hi, 
I have just managed to get ubuntu server working through virtual box which was a pain, how can load/install a gui interface from the command prompt, whenever i run aptitude install "system" it just says package cant be found. I am new to linux and have been using desktop ubuntu up untill now through vb where the gui loads automatically then you can start a terminal session.

---

### Post by albandy on 2009-03-26
sudo apt-get install ubuntu-desktop

---

### Post by speedy_pg on 2009-03-26
I have tryed this also, just says "could not find package ubuntu desktop

---

### Post by dmizer on 2009-03-26
What do you intend to do with your server?

---

### Post by speedy_pg on 2009-03-26
no idea really, network the machine, run network applications from it, i am a microsoft engineer and I am trying to teach myself linux, currently i have been using ubuntu desktop and running termial sessions to learn commands and start writing scripts and trying to get my head around the whole linux enviroment, i am running everything through vmware at the moment. i really need to get a couple of machines and install linux on them.

---

### Post by dandnsmith on 2009-03-26
I'd guess that the install fails because you don't have internet access to the repositories.

---

### Post by speedy_pg on 2009-03-26
yes you are right. I am an idiot. 

when i ran update command is just sits there obviously because it cant get access to the web, i will hit myself in the head with a large object.

---

### Post by mb_webguy on 2009-03-26
Installing the ubuntu-desktop package will essentially install the desktop version of Ubuntu.  If you just want a GUI for a server, I'd go with something simpler like the Openbox window manager, and the PyPanel panel.  Installing these will give you a GUI without installing a ton of additional applications as well.

---

### Post by Krupski on 2009-03-26
> **speedy_pg said:**
> Hi, 
I have just managed to get ubuntu server working through virtual box which was a pain, how can load/install a gui interface from the command prompt, whenever i run aptitude install "system" it just says package cant be found. I am new to linux and have been using desktop ubuntu up untill now through vb where the gui loads automatically then you can start a terminal session.

Why did you install Server if you want a GUI?

Server is not a "better" version of Ubuntu Linux... it's just optimized for.... running a server. For example, memory is managed differently and the interrupt tick rate is different (i.e. geared towards better server response).

If you want to run a GUI desktop, just install Ubuntu (or Kubuntu or whatever desktop you prefer).

You CAN just type "apt-get -V install gdm" (gdm for Gnome and kdm for KDE) and at next boot you will come up in the GUI, but I don't know if a server install plus a gdm/kdm install is the same as a "real" GUI install (i.e. there may be things left out, missing or not configured properly).

If you can, I would suggest starting from the beginning and just install the Ubuntu version that you want.

-- Roger

---

### Post by dmizer on 2009-03-26
> **Krupski said:**
> 
If you can, I would suggest starting from the beginning and just install the Ubuntu version that you want.

-- Roger

I will echo this. Ubuntu server is tuned for a non-GUI environment, and you may have problems with your computer as a result. If you want a GUI, you should install a GUI based release of Ubuntu.

---

### Post by Iowan on 2009-03-26
A [link]("https://help.ubuntu.com/community/ServerGUI") for your consideration.

---

### Post by dmizer on 2009-03-26
> **Iowan said:**
> A [link]("https://help.ubuntu.com/community/ServerGUI") for your consideration.

Thank you for that, I was not aware of its existence.

---

