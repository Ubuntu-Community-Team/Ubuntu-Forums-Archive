---
title: "MATE desktop environment"
date: 2012-09-07
forum: Desktop Environments
---

### Post by czgirb on 2012-09-07
Yesterday I installed MATE desktop environment with the following commands:[COLOR=red]
[/COLOR]> 
sudo add-apt-repository "deb [http://packages.mate-desktop.org/repo/ubuntu](http://packages.mate-desktop.org/repo/ubuntu) precise main"
sudo apt-get update
sudo apt-get install mate-archive-keyring
sudo apt-get update
sudo apt-get install mate-desktop-environment
and it's install **MATE**, **LXDE** and **OPENBOX** desktop environment.

Tried **MATE** ... tried to change the Theme ... mostly is unable to be changed. Some, is able able ... but not 100% changed.
*** In Ubuntu Tweak, theme is still Ubuntu's default theme. **Ambience**.
Tried **LXDE** ... due to the UI is difference, so I don't know how to change it.
OPENBOX ... what is this ??? How it looks like ???

Is it normal? How can I make all the theme is works 100% ???
If it can not, how can I uninstall it ???

---

### Post by Epodx64 on 2012-09-07
> **czgirb said:**
> Yesterday I installed MATE desktop environment with the following commands:[COLOR=red]
[/COLOR]and it's install **MATE**, **LXDE** and **OPENBOX** desktop environment.

Tried **MATE** ... tried to change the Theme ... mostly is unable to be changed. Some, is able able ... but not 100% changed.
*** In Ubuntu Tweak, theme is still Ubuntu's default theme. **Ambience**.
Tried **LXDE** ... due to the UI is difference, so I don't know how to change it.
OPENBOX ... what is this ??? How it looks like ???

Is it normal? How can I make all the theme is works 100% ???
If it can not, how can I uninstall it ???

you can try sudo apt-get install ppa-purge then purge the MATE ppa that will revert you to previous settings might I suggest giving Cinnamon a try it's second only to KDE IMO

---

### Post by czgirb on 2012-09-07
> **Epodx64 said:**
> you can try sudo apt-get install ppa-purge then purge the MATE ppa that will revert you to previous settings might I suggest giving Cinnamon a try it's second only to KDE IMO

Is ... sudo apt-get install ppa-purge deb [http://packages.mate-desktop.org/repo/ubuntu](http://packages.mate-desktop.org/repo/ubuntu) precise main ... is OK?

---

### Post by Epodx64 on 2012-09-07
> **czgirb said:**
> Is ... sudo apt-get install ppa-purge deb [http://packages.mate-desktop.org/repo/ubuntu](http://packages.mate-desktop.org/repo/ubuntu) precise main ... is OK?

uhm 

sudo apt-get install ppa-purge 
then
sudo apt-get ppa-purge ppa:whatever/mate

should work just fine; Did you install Mate from a .deb file or from a PPA?

---

### Post by czgirb on 2012-09-07
> **Epodx64 said:**
> 
... Did you install Mate from a .deb file or from a PPA?


Dunno what U mean. I installed MATE (directly from Terminal) as I described on 1st post.

---

### Post by Frogs Hair on 2012-09-07
See the link to install or remove Mate. [http://www.webupd8.org/2012/04/mate-desktop-12-released-install-it-in.html](http://www.webupd8.org/2012/04/mate-desktop-12-released-install-it-in.html)

---

### Post by Epodx64 on 2012-09-08
> **Frogs Hair said:**
> See the link to install or remove Mate. [http://www.webupd8.org/2012/04/mate-desktop-12-released-install-it-in.html](http://www.webupd8.org/2012/04/mate-desktop-12-released-install-it-in.html)

That seems particularly complex just to install a D.E.

---

### Post by grahammechanical on 2012-09-08
Mate is not an official Ubuntu flavour. That is why it does not have a variation of Ubuntu in its name, like we find with Xubuntu, Kubuntu and Lubuntu. And it is the reason it is installed from its own repositories and not from the Ubuntu repositories.

When we install a different desktop environment we also get stuff that those developers include as part of the desktop. That is why you have not just Mate but also LXDE and Openbox. This is something that happens when we install other desktop environments.

Ubuntu Tweak is designed for standard Ubuntu. It is not designed to modify another desktop environment.

You have to use the tools/utilities that were installed by the Mate desktop environment.

Did you notice this comment in the link provided by Frogs Hair?

> In my test, MATE Desktop worked ok under Ubuntu 11.10, but there were some issues with MATE Settings Daemon in Ubuntu 12.04: the GTK theme wasn't applied correctly.

So, there are issues with themes not applying correctly.

Regards

---

### Post by wheeze on 2012-09-08
> **czgirb said:**
> Yesterday I installed MATE desktop environment with the following commands:[COLOR=red]
[/COLOR]and it's install **MATE**, **LXDE** and **OPENBOX** desktop environment.

Tried **MATE** ... tried to change the Theme ... mostly is unable to be changed. Some, is able able ... but not 100% changed.

I've installed MATE several times on Precise and it has never added LXDE/Openbox. Something is wrong there.

To change the theme in MATE go to the Preferences section and choose Appearance.

---

### Post by wheeze on 2012-09-08
> **Epodx64 said:**
> That seems particularly complex just to install a D.E.

No more complex than adding a PPA is.

---

### Post by offgridguy on 2013-01-19
> **grahammechanical said:**
> Mate is not an official Ubuntu flavour. That is why it does not have a variation of Ubuntu in its name, like we find with Xubuntu, Kubuntu and Lubuntu. And it is the reason it is installed from its own repositories and not from the Ubuntu repositories.

When we install a different desktop environment we also get stuff that those developers include as part of the desktop. That is why you have not just Mate but also LXDE and Openbox. This is something that happens when we install other desktop environments.

Ubuntu Tweak is designed for standard Ubuntu. It is not designed to modify another desktop environment.

You have to use the tools/utilities that were installed by the Mate desktop environment.

Did you notice this comment in the link provided by Frogs Hair?



So, there are issues with themes not applying correctly.

Regards
Another great reply . Thanks

---

