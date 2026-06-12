---
title: "Why is the desktop &quot;Unity&quot; shell sticking with Compiz and GTK?"
date: 2013-01-03
forum: Desktop Environments
---

### Post by ojdon on 2013-01-03
Apologises if this is in the wrong place, but I'd like to ask a few questions about the desktop Unity shell. With the recent announcement of Ubuntu Phone's native apps being coded in QML and C++, why on earth did Canonical opt to stick with Compiz and GTK for the desktop shell?

Ubuntu TV in fact, used the same codebase as Unity 2D. I seem to remember that you used to be able to try out Ubuntu TV by patching the features over the Unity 2D session. 

Their official Ubuntu One client, in fact, is also QT based therefore sticks out like a sore thumb with the rest of the desktop experience. 

I assume it was because of important third-party apps such as Firefox which struggles to visually integrate nicely with a QT environment. 

Maybe we could see a new QML + C++ Desktop driven Unity shell in the future releases of Ubuntu? Just wondered if there was a solid reason behind why the decision was made to stick with Compiz and GTK?

---

### Post by pompel9 on 2013-01-03
As far as I have understood it, compiz is the core which unity is built upon.
So the question really is, is it possible to use something other than compiz. Or is unity only possible because of compiz.

---

### Post by ojdon on 2013-01-03
Unity 2D was built using QT and C++ so it is definitely possible. Shame they didn't opt to create a 3D accelerated version and deprecate the current version we have now so it fits nicely with the rest of the Ubuntu-based products that are in development which all use a variation of the Qt framework, it's just the main desktop shell that doesn't these days.

I wonder if the decision would be different if apps like Firefox and GIMP, integrated nicely into QT environments like they do in GNOME and XFCE.

---

### Post by jbicha on 2013-01-03
> **ojdon said:**
> Their official Ubuntu One client, in fact, is also QT based therefore sticks out like a sore thumb with the rest of the desktop experience. 

I assume it was because of important third-party apps such as Firefox which struggles to visually integrate nicely with a QT environment. 



Firefox looks fine in Qt. Ubuntu One looks misplaced in Ubuntu not because it uses Qt but because it uses custom widgets. It looks that way because it was designed to look that way.

---

### Post by ojdon on 2013-01-03
> **jbicha said:**
> Firefox looks fine in Qt. Ubuntu One looks misplaced in Ubuntu not because it uses Qt but because it uses custom widgets. It looks that way because it was designed to look that way.

I thought Firefox suffered from the same visual issues as other GTK based applications do such as the ugly looking scrollbars, etc. Unless it's fixed in recent versions? (Chrome/Chromium still suffers from this, however).

---

### Post by 3Miro on 2013-01-03
Ubuntu used Gnome and Gnome is GTK based environment and Ubuntu isn't moving away from Gnome any time soon. The decision to use QT for Unity 2D did baffle me at the time, but as far as I understand Unity 2D is phased out of Ubuntu anyway.

---

### Post by vasa1 on 2013-01-03
> **ojdon said:**
> I thought Firefox suffered from the same visual issues as other GTK based applications do such as **the ugly looking scrollbars**, etc. Unless it's fixed in recent versions? (Chrome/Chromium still suffers from this, however).
What do you mean? Could you put up images of scrollbars you consider ugly and not ugly with a little context to explain?

---

### Post by grahammechanical on 2013-01-04
> Ubuntu TV in fact, used the same codebase as Unity 2D. 

Not any more.

> Since Unity 2D is deprecated for Ubuntu 12.10, much work is being done to port Ubuntu TV to Unity 3D. Much of this work is included in the 12.10 Ubuntu desktop. Currently the transition is approximately 60% complete.

[http://www.doadjustyourset.com/2012/10/15/ubuntu-tv-weekly-update-11/]("http://www.doadjustyourset.com/2012/10/15/ubuntu-tv-weekly-update-11/")

I have two guesses on your questions.

1) Unity 2D proved to be inadequate at providing the same user experience as Unity 3D. And there appeared an alternative method - LLVMpipe. And so there was now no need for a fallback mode.

2) the Ubuntu mobile user interface benefits from apps coded in QML and Qt.

> We have been working on an SDK with a special set of phone components (think widgets and other UI elements) that run on top of QML and Qt, 

[http://www.jonobacon.org/2013/01/02/announcing-ubuntu-for-phones/]("http://www.jonobacon.org/2013/01/02/announcing-ubuntu-for-phones/")

I would say that logic has less involvement than necessity in the development of Ubuntu or any Linux distribution. Especially if you want to bring Open Source to millions of humans.

Regards.

---

