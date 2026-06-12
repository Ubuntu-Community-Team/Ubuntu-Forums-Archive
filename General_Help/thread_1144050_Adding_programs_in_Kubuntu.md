---
title: "Adding programs in Kubuntu"
date: 2009-04-30
forum: General Help
---

### Post by conradcliff on 2009-04-30
Hey guys, I'm just wondering if I'm missing something or not...In Ubuntu I have a wonderful little app for adding and removing programs and I can do a search and find just about everything in there but in Kubuntu the app seems different and I can't even find firefox. Am I doing something wrong?

Thanks for any help!! :)

---

### Post by mafaldaspeaks on 2009-05-10
> **conradcliff said:**
> Hey guys, I'm just wondering if I'm missing something or not...In Ubuntu I have a wonderful little app for adding and removing programs and I can do a search and find just about everything in there but in Kubuntu the app seems different and I can't even find firefox. Am I doing something wrong?

Thanks for any help!! :) 

Oh, how i hoped somebody answered you-I'm having the same problem here.

---

### Post by HavocXphere on 2009-05-10
In 9.04 its called packagekit I think. Kubuntu <9.04 used Adept-manager.

Firefox is not installed on Kubuntu by default since Firefox uses gtk(gnome) while Kubuntu uses KDE. i.e. you
can install it but you'd have to download a lot of gnome/gtk libraries with it to make it work.

---

### Post by nzadLithium on 2009-05-10
Kubuntu has a program called Adept I think. It's the kubuntu equivalent of synaptic.

---

### Post by menschmeier on 2009-05-10
I am quite new to Kubuntu too. The App you are searching is adept. You will find it in the menue or using konsole by typing

sudo adept

Hope that helps.

---

### Post by mafaldaspeaks on 2009-05-10
Ok, i just found out that there's a forum especially for kubuntu so I'll just check it out: [http://www.kubuntuforums.net/](http://www.kubuntuforums.net/)

---

### Post by grappler on 2009-05-10
I find synaptic better than adept even though I use kde. It can easily be installed by

```
sudo apt-get install synaptic 
```

and then accessed from the kmenu.

---

### Post by mafaldaspeaks on 2009-05-10
> **HavocXphere said:**
> In 9.04 its called packagekit I think. Kubuntu <9.04 used Adept-manager.

Firefox is not installed on Kubuntu by default since Firefox uses gtk(gnome) while Kubuntu uses KDE. i.e. you
can install it but you'd have to download a lot of gnome/gtk libraries with it to make it work.

Yes, it's doing that now (yes, I've finally managed to learn how to install it) but I wanted it 'cause konqueror already crashed twice in an hour.

---

### Post by apparle on 2009-05-10
In kubuntu you have Kpackagekit for various installation purpose

There is an option Add/Remove Software or something like that under System Settings.
you can use that.

Or you can press Alt+F2 and type Kpackagekit

Earlier kubuntu had Adept but it was unstable so Kpackagekit is used now

---

### Post by conradcliff on 2009-05-11
Hey guys, so I don't know if I was using the wrong search bar or if Kubuntu was just being buggy but when I went back to the app manager again I was able to find Firefox right away. Thanks a ton for all the help!!!

---

