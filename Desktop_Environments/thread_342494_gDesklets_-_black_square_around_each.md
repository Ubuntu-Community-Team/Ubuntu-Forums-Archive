---
title: "gDesklets - black square around each"
date: 2007-01-20
forum: Desktop Environments
---

### Post by IamAcoconut on 2007-01-20
I installed gDesklets yesterday, and everthing worked fine. But today, after I booted each desklet, instead of being transparent as previously have a black square **around** them (not just as a background or filling, which I can choose via desklet configuration).

How to undo this? And BTW, how can I make the tray icon visible? 
Help really appreaciated, thanks in advance :)

---

### Post by SPr on 2007-01-20
Hi,

I've just installed gDesklets and this message came up when it was first run. I don't know if it will help you in any way but I thought it might be helpful.

---

### Post by IamAcoconut on 2007-01-20
Hm, I don't see the desklets above my application windows, just on the desktop. I tried hitting <shift><F12>, and nothing happened, after restarting desklets.

And I can change this in configuration, since there's no tray icon (I foolishly disabled it).

Moreover, I don't know where the settings for the gDesklets reside except for the catalogues and files named gDesklets, so even **after reinstallation** I have the same crappy settings :(
Please, help.

---

### Post by SPr on 2007-01-20
Hi,

man gdesklets gives info that may help you :)

---

### Post by IamAcoconut on 2007-01-20
Too bad, it doesn't :(

How do I get the tray icon back?

---

### Post by IamAcoconut on 2007-01-20
Any1? What to edit in order to disable the **float** mode and enable the **tray** icon?

---

### Post by IamAcoconut on 2007-01-21
*bump*

---

### Post by kexodusc on 2007-02-01
Hi there, I recently experienced the same symptoms and found what appears to be a solution to my black square problem.
[http://www.ubuntuforums.org/showthread.php?p=2091798#post2091798](http://www.ubuntuforums.org/showthread.php?p=2091798#post2091798)

Hope this helps you.

---

### Post by IamAcoconut on 2007-02-01
Thanks.
I wasn't translucency, but the float mode in my case that I had to disable. But since the key shortcut didn't work (even after manually changing it) and I couldn't acces configuration, because tray I had turned off the tray, and there was no way to turn it on, I got stuck.
I removed all the files and folders named gdesklets, (incl. hidden) installed the package again and now it's fine.

---

### Post by eustace on 2007-02-21
> **IamAcoconut said:**
> How do I get the tray icon back?

I just stumbled upon the same problem. The solution I found is trivial, just  start the configuration dialog manually (e.g. using Alt+F2): 

```
gdesklets configure
```

Now you can set any gdesklets preferences. 

HTH.

---

