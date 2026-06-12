---
title: "Gnome classic menu on Ubuntu 14.04?"
date: 2014-05-15
forum: Desktop Environments
---

### Post by ramakanta on 2014-05-15
Today  I have install ubuntu 14.04 LTS( Install inside windows 7). previous was 10.04. when open 14.04 , there is  some missing which is Menu bar .  *screenshot attached *.

[[img]http://s22.postimg.org/5m8j3v8yl/10_04.jpg[/img]](http://postimg.org/image/5m8j3v8yl/)


how to  return ubuntu 10.04 like envirnoment  . please help me . also I hate the unity bar panel which  is left side of desktop . how to delete this bar . please hep me .
thank you .

---

### Post by cariboo on 2014-05-15
Moved to a thread of it's own, as this didn't belong where it was.

---

### Post by ramakanta on 2014-05-15
> **cariboo907 said:**
> Moved to a thread of it's own, as this didn't belong where it was.

I am not understood ????

---

### Post by grahammechanical on 2014-05-16
On Ubuntu 14.04 we open the Ubuntu Software Centre and search for flashback and install gnome-session-flashback. We will then get two additional options at the login screen = Gnome Flashback (Compiz) and Gnome Flashback (Metacity)

Do not install Gnome Classic as that is designed for Gnome 3 shell which is not installed by default on Ubuntu Unity. What is now called Gnome Classic is actually a Gnome 3 shell extension and installing Gnome Classic will require the installation of Gnome 3 shell.

Regards.

---

### Post by ibjsb4 on 2014-05-16
Or do it in terminal

```
sudo apt-get install gnome-session-flashback
```

---

### Post by ramakanta on 2014-05-17
^^ Have you any screenshot of  *gnome-session-flashback  ????*

---

### Post by ramakanta on 2014-05-17
> **grahammechanical said:**
> On Ubuntu 14.04 we open the Ubuntu Software Centre and search for flashback and install gnome-session-flashback. We will then get two additional options at the login screen = Gnome Flashback (Compiz) and Gnome Flashback (Metacity)

Do not install Gnome Classic as that is designed for Gnome 3 shell which is not installed by default on Ubuntu Unity. What is now called Gnome Classic is actually a Gnome 3 shell extension and installing Gnome Classic will require the installation of Gnome 3 shell.

Regards.

how to delete left side panel  ???

---

### Post by Frogs Hair on 2014-05-17
Flashback Session

---

### Post by kansasnoob on 2014-05-18
> **ramakanta said:**
> ^^ Have you any screenshot of  *gnome-session-flashback  ????*

I started some notes regarding Flashback w/Metacity here:

[http://ubuntuforums.org/showthread.php?t=2220264](http://ubuntuforums.org/showthread.php?t=2220264)

In the screenshot there I'm using only a highly edited bottom panel :)

---

### Post by kansasnoob on 2014-05-18
> **ramakanta said:**
> how to delete left side panel  ???

Flashback w/Compiz had a problem still displaying parts of the Unity DE but that should be fixed with recent updates now, however there are multiple known issues with the Flashback w/Compiz session (such as editing the number of workspaces) that require some heavy-duty tweaking in 'compizconfig-settings-manager'. I prefer just using Flashback w/Metacity.

---

