---
title: "Removing kde login menu"
date: 2012-07-22
forum: Desktop Environments
---

### Post by Friwise on 2012-07-22
Hello!!!!!

I tried to see how beautiful is the kde4 desktop.
I was not so impressed and in fact I was quite disappointed so I uninstalled it following the instructions of another website [http://www.psychocats.net/ubuntu/pureubuntu](http://www.psychocats.net/ubuntu/pureubuntu). It worked somehow... I mean it is not any more in the options of login.
However the login is still the KDE4 and I want to get rid of it because it just makes my login slower.

Is there any way I can do that?

Thanks in advance

---

### Post by Superpelican12 on 2012-07-23
What you mean with "KDE4-loginscreen" is called KDM (K Display Manager).
Ubuntu' s default display manager is now LightDM. In the past (before Unity etc.)
it was GDM (Gnome Display Manager) . When you installed the KDE4
package  it also installed KDE' s default login screen/display manager.
What you need to do is uninstall the "kdm" package.
P.S. May I ask what you exactly  found disappointing about KDE ;-)

---

### Post by Friwise on 2012-07-23
Thanks for answering!

I think I uninstalled the kde package. In the log in options there is no KDE option anymore. However the log in page (desktop or whatever the picture we see when we need to log in) is still the same KDE. 

What I did not like is that I couldn't find some programmes (i.e log files viewer) and it was slowing my laptop too much with no real beauty effect.

In any case. Can you help me uninstall the KDE package properly, since this is what I may need?

---

### Post by cmcanulty on 2012-07-23
Install splash screen manager and set it to what you want. I has same problem after trying LXDE

---

### Post by Friwise on 2012-07-23
I will try that now and I will let you know if and how it worked. Hmmm.... I don't know how to install it. I can't find it at ubuntu softwar center. Can you help a bit?

:KS Thanks in advance!!!

---

### Post by Krytarik on 2012-07-23
Seems like you overlooked an important bit of *Superpelican12*'s reply:
> **Superpelican12 said:**
> What you need to do is uninstall the "**kdm**" package.
Apart from that, I'd also run this command, to get rid of all other packages the installation of KDE may have left over:
```
sudo apt-get autoremove --purge
```Regards.

---

### Post by Friwise on 2012-07-23
Thank you all!!! Especially Krytarik!!!
Solved after followinf Krytarik's advice.

---

### Post by cmcanulty on 2012-07-23
Here it is also is in synaptic

---

