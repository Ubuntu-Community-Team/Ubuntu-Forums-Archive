---
title: "Super-Newbie post: Compiz-fusion not working"
date: 2007-09-21
forum: Desktop Effects &amp; Customization
---

### Post by japtar10101 on 2007-09-21
I wish I could give a more descriptive information on how either compiz-fusion or emerald themes are not working, but the basic gist is this:
even when I input alt+F2, then compiz --replace, nothing happens.  Same goes to emerald --replace.

I used the following link as reference, and at only one point did installation halt (I tried it again, then it said success).  Since the installation seemed to have worked, my only conclusion is either my graphic card (X1550 ATI, and yes, fgrl is installed) doesn't support it, or I'm missing something.  Any help?

(If your in need of more details, I'll try to work on that, too)

---

### Post by akiratheoni on 2007-09-21
Instead of just using Alt+F2 to open it up, fire up a terminal and type in compiz --replace. It will output any errors, then post the errors. Sorry, that's all I can do to help you; once you post the error, I'm sure other people can help you.

---

### Post by japtar10101 on 2007-09-21
> **akiratheoni said:**
> Instead of just using Alt+F2 to open it up, fire up a terminal and type in compiz --replace. It will output any errors, then post the errors. Sorry, that's all I can do to help you; once you post the error, I'm sure other people can help you.

```
mydesktop:~$ compiz --replace
Fatal: Failed test: texture_from_pixmap support
Checks indicate that it's impossible to start compiz on your system.

```
Yeah.  That kind of solves it....
Tell me there's some work-around this -.-'

---

### Post by Forlong on 2007-09-22
What graphics card are you using?
In case you don't know:
```
lspci | grep VGA
```
And did you install any driver?

---

### Post by japtar10101 on 2007-09-24
> **Forlong said:**
> What graphics card are you using?
In case you don't know:
```
lspci | grep VGA
```
And did you install any driver?

I'll check this out.  I know I'm using an Ati Radeon X1550 graphic card, but that says little, doesn't it?

Also, Restricted Drivers are installed.

---

### Post by Forlong on 2007-09-24
Alright, you have to use the fgrlx driver with that card as well as [Xgl]("https://help.ubuntu.com/community/CompositeManager/Xgl").

If it still doesn't work after setting that up, post your xorg.conf

---

### Post by japtar10101 on 2007-09-24
> **Forlong said:**
> Alright, you have to use the fgrlx driver with that card as well as [Xgl]("https://help.ubuntu.com/community/CompositeManager/Xgl").

If it still doesn't work after setting that up, post your xorg.conf

My friend here says I need to uninstall fglrx because I have Feisty Fawn. True or False?

---

### Post by Forlong on 2007-09-24
> **japtar10101 said:**
> My friend here says I need to uninstall fglrx because I have Feisty Fawn. True or False?
Like I said, you _have to_ use the fgrlx driver with your graphics card. There is no alternative to that.

---

### Post by japtar10101 on 2007-09-24
> **Forlong said:**
> Like I said, you _have to_ use the fgrlx driver with your graphics card. There is no alternative to that.

:( It's going to be a while until I'll be able to touch my Ubuntu desktop (lots of exams to study), but once I do get to it, I'll let you know how it went.

---

