---
title: "Upgrade to Ubuntu Studio?"
date: 2010-06-01
forum: Desktop Environments
---

### Post by Jake007g on 2010-06-01
I want to install Ubuntu Studio, for multimedia purposes. I know I could go the simple way of doing it and install it to a partition, but I was wondering if it was possible to install it as a new environment. I'm a bit of a Linux noob, but I know that with 10.04 you can boot into Gnome, KDE and XFCE without changing the operating system. Is is possible to get Ubuntu Studio as a seperate environment? 

If it isn't, I'd be happy to just install all of the multimedia programs onto my Ubuntu desktop, does anybody know a terminal command to get all the software packages at once?

Hope someone can help

-Jake

---

### Post by Jake007g on 2010-06-01
bump

---

### Post by calinut1 on 2010-06-01
> **Jake007g said:**
> I want to install Ubuntu Studio, for multimedia purposes. I know I could go the simple way of doing it and install it to a partition, but I was wondering if it was possible to install it as a new environment. I'm a bit of a Linux noob, but I know that with 10.04 you can boot into Gnome, KDE and XFCE without changing the operating system. Is is possible to get Ubuntu Studio as a seperate environment? 

If it isn't, I'd be happy to just install all of the multimedia programs onto my Ubuntu desktop, does anybody know a terminal command to get all the software packages at once?

Hope someone can help

-Jake

Hey there!
Open a terminal(Applications -> Accessories -> Terminal) and type:

```
sudo apt-get install ubuntustudio-desktop
```

Then wait for the installation to begin. It's as simple as that! :)
Hope I helped you!
Good luck!

EDIT: It may be the case that you will be able to choose between the desktop environments at startup. You will be able to choose between Gnome and Ubuntu Studio. In case you only want Ubuntu studio, you should remove Gnome
The command is ```
 sudo apt-get remove ubuntu-desktop
```

---

### Post by Jake007g on 2010-06-01
Thank you very much for the help, that is exactly as I wanted!

---

### Post by cchhrriiss121212 on 2010-06-01
Studio is not an environment, its a collection or packages with a different kernel and a new theme. It still uses gnome. You could also try installing the packages separately which will give you more flexibility when adding and removing. If you install the metapackage from the repos then you cannot remove any of the individual programs without removing the desktop.

---

### Post by Jake007g on 2010-06-01
> **cchhrriiss121212 said:**
> Studio is not an environment, its a collection or packages with a different kernel and a new theme. It still uses gnome. You could also try installing the packages separately which will give you more flexibility when adding and removing. If you install the metapackage from the repos then you cannot remove any of the individual programs without removing the desktop.

Yeah I kind of figured that out now I've installed it with the command that the guy above me posted. Still, I like the colours and themes of Studio, but I also like the way you can keep it looking like standard Ubuntu :)

Does anyone know how I can install all of the extra media packages, because I only got about 4 new ones :/

---

### Post by calinut1 on 2010-06-01
> Yeah I kind of figured that out now I've installed it with the command that the guy above me posted. Still, I like the colours and themes of Studio, but I also like the way you can keep it looking like standard Ubuntu :)

Does anyone know how I can install all of the extra media packages, because I only got about 4 new ones :/

Try:

```
sudo apt-get install ubuntustudio-audio
```
```
sudo apt-get install ubuntustudio-video
```
```
sudo apt-get install ubuntustudio-graphics
```

These commands should install audio, video and graphics software, though I don't know if it's not the same that comes with ubuntustudio-desktop

And thanks for telling me that's not an environment! I didn't use Ubuntu Studio and I didn't know that it used Gnome. I though it used an environment of itself :P. (I should have thought about it better. Ubuntu uses Gnome, so Ubuntu Studio should use Gnome too)

---

### Post by Jake007g on 2010-06-01
Thanks a lot, I'll give that a go after Britains got talent, I'll double post and let you know how it goes :)

---

### Post by Jake007g on 2010-06-01
Update; took a while, but worked perfectly! Thank you very much for your both for help, I really appreciate it!

---

### Post by calinut1 on 2010-06-02
> **Jake007g said:**
> Update; took a while, but worked perfectly! Thank you very much for your both for help, I really appreciate it!

No problem.

---

