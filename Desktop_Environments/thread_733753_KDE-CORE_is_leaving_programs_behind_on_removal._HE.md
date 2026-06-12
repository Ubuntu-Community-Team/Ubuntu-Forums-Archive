---
title: "KDE-CORE is leaving programs behind on removal. HELP"
date: 2008-03-24
forum: Desktop Environments
---

### Post by kelinu on 2008-03-24
Ok, I generally use GNOME on my Ubuntu Gutsy. I decided to install KDE-CORE from Synaptics to see what all the hype was about....and guess what!? I hated it. And now I want to remove it. So I went back to GNOME and from Synaptics, tried to remove kde-core. That  didn't work.  Then I tried to remove the kde-core with the aptitude comand in terminal...that did work for the actual kde, but now on my GNOME desktop I get all the applications from KDE on my applications menu in my Gnome desktop.  I'd like to get rid of all these apps that came with KDE-CORE and I've no idea how!  

PLEASE PLEASE PLEEEEEEEEASE HELP!!!

Michael =)

---

### Post by fela on 2008-03-24
what you should of done to install KDE was ```
sudo aptitude install kubuntu-desktop
``` then you could uninstall it by running ```
sudo aptitude remove kubuntu-desktop
```

as it seems you haven't done that, you will have to manually uninstall all of the KDE apps you don't want, e.g. if it was konqueror: ```
sudo apt-get remove konqueror
```
removes it. And ```
sudo apt-get purge konqueror
``` purges it (deletes any configuration files as well as the program)

or you could use synaptic to just mark all the kde apps for removal and click apply.

---

### Post by kelinu on 2008-03-24
> **fela said:**
> what you should of done to install KDE was ```
sudo aptitude install kubuntu-desktop
``` then you could uninstall it by running ```
sudo aptitude remove kubuntu-desktop
```

as it seems you haven't done that, you will have to manually uninstall all of the KDE apps you don't want, e.g. if it was konqueror: ```
sudo apt-get remove konqueror
```
removes it. And ```
sudo apt-get purge konqueror
``` purges it (deletes any configuration files as well as the program)

or you could use synaptic to just mark all the kde apps for removal and click apply.

Hi,
thanks for the info...but if I had to install kubuntu-desktop now and then uninstall it, would all the apps go automatically?

---

### Post by kelinu on 2008-03-24
please someone help here!

---

### Post by yeats on 2008-03-24
I have a similar situation to yours.  I used the package manager to download KDE to try it out and I now want to remove it.   I wish I *had* known about selecting Kubuntu desktop, because there are certain features that are not fully functional in KDE having installed it piecemeal.  I'm pretty new to this too, so I don't have much to offer in the way of technical help.  Thanks for posting this, though, since this post addresses what I wanted to know.

---

### Post by kelinu on 2008-03-25
> **chrissharp123 said:**
> I have a similar situation to yours.  I used the package manager to download KDE to try it out and I now want to remove it.   I wish I *had* known about selecting Kubuntu desktop, because there are certain features that are not fully functional in KDE having installed it piecemeal.  I'm pretty new to this too, so I don't have much to offer in the way of technical help.  Thanks for posting this, though, since this post addresses what I wanted to know.

alright finally probs solved! THANKS!!!!!:KS

---

