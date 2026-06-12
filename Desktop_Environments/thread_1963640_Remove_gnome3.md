---
title: "Remove gnome3"
date: 2012-04-22
forum: Desktop Environments
---

### Post by Kiraitachi on 2012-04-22
Hi guys ^^, I've been having this problem quite some long time and I was delaying it, but now that 12.04 is about to come I wanna get a fresh update with clean stuff.

So lets get into the prob:

The thing is that I have ubuntu 11.10 with unity, but wanted the faenza icon theme running and found a workaround installing gnome tweaker tool, but when I installed the "tool" all gnome dependencies got installed also...so now Im having Gnome 3 and Unity, later on I remove the tool but left the gnome 3 environment, I always run Unity and having no prob with it, dont like gnome 3 at all....so 

Is there a way to uninstall gnome 3 and just leave Unity as it if came from brand new cd??? I dont wanna get messed up with gnome shell cause I need that for Unity right??

Thanks to any answers, Im a coder and already been 5 years since using ubuntu so I pretty much know my workaround, dont need to get noobish ^^.

Just give me some apt-get remove (the dependencies needed to be removed) that will fix it ^^ thanks!!!!

:popcorn:

---

### Post by 3Miro on 2012-04-22
Unity is just a shell on top of Gnome 3, hence removing Gnome 3 will in fact remove Unity. What you need to remove is not Gnome 3, but Gnome-shell and Gnome-session-fallback. If you remove those two packages, the login scree should go back to just Unit 3D/2D options.

---

### Post by Kiraitachi on 2012-04-25
> **3Miro said:**
> Unity is just a shell on top of Gnome 3, hence removing Gnome 3 will in fact remove Unity. What you need to remove is not Gnome 3, but Gnome-shell and Gnome-session-fallback. If you remove those two packages, the login scree should go back to just Unit 3D/2D options.

Yes but will that remove all the dependencies packages that came with gnome 3 environment and will be just like a fresh install?? just Unity?? 

And if thats true, how do I do that???

---

### Post by dino99 on 2012-04-25
ubuntu installion packages is drived by a "meta-package" named ubuntu-desktop. You can remove it, no problem, and then you can uninstall what you dont want/need, like gnome-shell, ....

sudo apt-get install synaptic
sudo synaptic

---

### Post by 3Miro on 2012-04-25
> **Kiraitachi said:**
> Yes but will that remove all the dependencies packages that came with gnome 3 environment and will be just like a fresh install?? just Unity?? 

And if thats true, how do I do that???

Please, do not call it Gnome 3, it is confusing. You want to remove Gnome-shell.

With dino99's suggestion you can use synaptic to remove gnome-shell and gnome-session-fallback. You may be able to do that from the Software Center, but I am not sure how, I mostly use Synaptic.

The additional dependencies would require an extra step. Note that those additional dependencies take up only a small amount of space on your HDD and do not get loaded to slow down your machine or something. To remove the packages that have been automatically added during installation, you can use the commmand:
```
sudo apt-get autoremove
```
You need to type this in the terminal and it will remove the programs that have been automatically installed. I don't know if Synaptic or the Software Center can do that too.

---

### Post by Kiraitachi on 2012-04-26
> **3Miro said:**
> Please, do not call it Gnome 3, it is confusing. You want to remove Gnome-shell.

With dino99's suggestion you can use synaptic to remove gnome-shell and gnome-session-fallback. You may be able to do that from the Software Center, but I am not sure how, I mostly use Synaptic.

The additional dependencies would require an extra step. Note that those additional dependencies take up only a small amount of space on your HDD and do not get loaded to slow down your machine or something. To remove the packages that have been automatically added during installation, you can use the commmand:
```
sudo apt-get autoremove
```You need to type this in the terminal and it will remove the programs that have been automatically installed. I don't know if Synaptic or the Software Center can do that too.


Already did a sudo apt-get remove gnome-shell && session-fallback and worked thanks guys.

---

### Post by 3Miro on 2012-04-26
If this has solved your problem, please mark the thread as "solved".

---

