---
title: "KDE Pure in Ubuntu 12.04"
date: 2012-05-01
forum: Desktop Environments
---

### Post by overcast on 2012-05-01
I got tired of suggestion of installing kubuntu in order to have KDE in ubuntu. Is there any way plain vanilla installation of KDE in ubuntu 12.04?

I don't want to install kubuntu and then get rid of some packages. I just want KDE. Why? i like the bootscreen of ubuntu and i don't want to get rid of that. Asking this question on askubuntu will result in moving the thread as duplicate so asking here in the hope that someone with vanilla KDE installation can help. 

Thanks in advance.

---

### Post by mips on 2012-05-01
It's either plasma-desktop or kde-workspace, both are 107MB in size and both pull in 174 packages on my Xubuntu.

---

### Post by SeijiSensei on 2012-05-01
> **overcast said:**
> I just want KDE. Why? i like the bootscreen of ubuntu and i don't want to get rid of that.

You're making this effort because of a boot screen that appears for maybe ten seconds?

---

### Post by clparker on 2012-05-02
I'm interested to know as well, can't there be a way to do this? Wouldn't one add some KDE repository and use a package manager?

---

### Post by grahammechanical on 2012-05-02
Surely, you are looking at this the wrong way around.

The Kubuntu developers have done all the work for you. They have already replaced Gnome with KDE.

---

### Post by collisionystm on 2012-05-02
Dude....

Install kubuntu-desktop

sudo apt-get install kubuntu-desktop

then just change the plymouth theme ( boot screen ) to your choice.

edit 
/lib/plymouth/themes/default.plymouth


Here is the default Ubuntu

Plymouth Theme]
Name=Ubuntu Logo
Description=A theme that features a blank background with a logo.
ModuleName=script

[script]
ImageDir=/lib/plymouth/themes/ubuntu-logo
**ScriptFile=/lib/plymouth/themes/ubuntu-logo/ubuntu-logo.script**


Problem solved.

Always do the *-desktop because it keeps everything clean. if you install just kde you will have gnome and kde files all appearing under the kde menu and it looks like ****

So long story short. Just take 10 seconds to change the plymouth you want.

---

### Post by overcast on 2012-05-02
Thanks @collisionystm, off to try your method.

@grahammechanical, not all the work. i like gnome session fallback and i have one member who likes KDE. so i want to choose things during the boot. also i like to keep the boot screen of ubuntu, so there.

---

### Post by de Bacon on 2012-05-02
Overcast,  I used the solution of installing kubuntu desktop to ubuntu 11.04, it worked find for me.  I too like some of each.  Now I don't like the unity desktop of ubuntu so have reversed, loading Kubuntu and adding the gnome desktop.  I kind of get what I want.  

Good luck.

---

### Post by jhhayesii on 2012-06-15
Not to long ago I read somewhere the Kubuntu folks lost funding for their project so their fate was uncertain. So trying to figure out how to install KDE through a Ubuntu distro is not a bad idea. That's why I'm here. :)

---

### Post by oldos2er on 2012-06-15
Kubuntu is alive and well. [http://www.christianoss.org/blog/2012/04/10/future-kubuntu-blue](http://www.christianoss.org/blog/2012/04/10/future-kubuntu-blue)

---

### Post by zombifier25 on 2012-06-15
kde-plasma-workspace for KDE only, nothing more.

---

