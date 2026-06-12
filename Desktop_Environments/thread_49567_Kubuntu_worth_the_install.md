---
title: "Kubuntu worth the install?"
date: 2005-07-16
forum: Desktop Environments
---

### Post by Noah0504 on 2005-07-16
I like KDE over Gnome, and I was wondering if Kubuntu is worth the install.  I'm just afraid it's not as stable as Ubuntu.  Let me know what you think!

---

### Post by matthew on 2005-07-16
I didn't install Kubuntu, but just added the KDE files (all of them) to my stock Ubuntu install and tested KDE for a while. I think the main differences are in the realm of personal taste, but there is a slight stability difference with Gnome winning on that count. I found I prefer Gnome for a few other reasons as well.

Why not try it out by installing kdebase and kde-core along with whatever else they require, log out, and log in using the new desktop?

---

### Post by Noah0504 on 2005-07-16
I thought about doing that, but I just assumed I might as well try out Kubuntu.  But I didn't want to waste my time if it was unstable.

---

### Post by matthew on 2005-07-16
I hope I didn't imply it is unusable. Lots of people use KDE daily with no real issues. I would say if you are interested in trying it you can do so without worry. What stability differences exist are not so substantial that I would recommend differently.

---

### Post by Noah0504 on 2005-07-16
Okay, thanks.  I'm going to go for it.  :)

---

### Post by Seth on 2005-07-16
[QUOTE=matthew]I hope I didn't imply it is unusable. Lots of people use KDE daily with no real issues. I would say if you are interested in trying it you can do so without worry. What stability differences exist are not so substantial that I would recommend differently.[/QUOTE]
 It is not as stable as Gnome upon initial install... it's a first release! However, once you update to KDE 3.4.1 (you can see how to do so on [http://kubuntu.org](http://kubuntu.org) ) it is rock-solid. I don't use anything except Kubuntu on my desktop and laptop.

---

### Post by Noah0504 on 2005-07-16
[QUOTE=Seth]It is not as stable as Gnome upon initial install... it's a first release! However, once you update to KDE 3.4.1 (you can see how to do so on [http://kubuntu.org](http://kubuntu.org) ) it is rock-solid. I don't use anything except Kubuntu on my desktop and laptop.[/QUOTE]
 That just cleared up any worries I had.

---

### Post by Feanor on 2005-07-17
I'm using Kubuntu on my Hp laptop and it's working perfectly. There were some bugs that with the KDE 3.4.1 are solved. The only thing is that very few applications specific for KDE are available from official repositories, so you should read this topic.

[http://www.ubuntuforums.org/showthread.php?t=49133&page=1&pp=10](http://www.ubuntuforums.org/showthread.php?t=49133&page=1&pp=10)

or if you won't read add simply this repos in your sources.list

```
deb http://dinton.no-ip.org/ kubuntu main
deb-src http://dinton.no-ip.org/ kubuntu main
```

---

### Post by Gezzer on 2005-07-17
i have Kubuntu installed on 3 systems on my home network all updated to KDE 3.4.1
everything seems to running with no major issues whatsoever

the only thing i have done is to install FF & TB as stand alone programs on the /home partition on each system ...

---

### Post by rider343 on 2005-07-17
I have kubuntu updated run in my system... 
it is Rock :)

---

### Post by GeneralZod on 2005-07-17
Is there a deb-src repository for the KDE 3.4.1 Kubuntu packages? There are a few niggling bugs in KDE that I like to fix whenever I update, and a deb-src is by far the most convenient way!

---

### Post by Feanor on 2005-07-17
Try to add these in your /etc/apt/sources.list

```
## Kubuntu
  
  deb http://kubuntu.org/hoary-kde341 hoary-updates main
  deb http://kubuntu.org/hoary-koffice14 hoary-updates main
  # deb http://download.kde.org/stable/3.4.1/kubuntu hoary-updates main
```

Oh sorry, I don't read that you're searching deb-src  :razz:

---

