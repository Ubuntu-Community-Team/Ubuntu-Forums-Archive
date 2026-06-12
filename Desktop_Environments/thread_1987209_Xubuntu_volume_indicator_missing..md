---
title: "Xubuntu volume indicator missing."
date: 2012-05-26
forum: Desktop Environments
---

### Post by crosstalk on 2012-05-26
I recently installed Xubuntu 12.04 on my laptop, then began tweaking it. I tried removing Pulseaudio (I don't need it), but found that my volume control keys no longer worked (which is neither a surprise nor a major concern to me).

However, after I re-installed the "pulseaudio" and "pavucontrol" packages, I did not get back the indicator applet which shows my volume. I also installed the "indicator-sound" package.

How can I restore that indicator? Did I grab the right package?

Thank you for your help.

---

### Post by bug67 on 2012-05-26
Maybe try right clicking on the panel then selecting panel, "Add new items."  Then you can scroll through a list of things you can add to the panel.  One of which is the "Indicator Plugin."  That's the one you want.

---

### Post by brainwash on 2012-05-26
Re-install the package **indicator-sound-gtk2** to restore the volume indicator.

On a side note, you can create custom keyboard shortcuts to adjust the volume in case you really want to get rid of Pulseaudio.

---

### Post by crosstalk on 2012-05-26
> **brainwash said:**
> Re-install the package **indicator-sound-gtk2** to restore the volume indicator.
Thank you, this (and a reboot) did it.

> On a side note, you can create custom keyboard shortcuts to  adjust the volume in case you really want to get rid of  Pulseaudio.I am aware of this, having done it in the past; but since I am only  trying to remove it to get a more lightweight system, I don't consider  the hassle (with another OS (forgot which), it broke the volume  indicator) to be worth the effort.

---

### Post by sampayu on 2012-07-26
Well, this is a new reply to an old topic, anyway I decided to reply 'coz I believe that it might still be of some help to the readers.

I'm on XUbuntu 12.04 and I accidentaly (euphemism for "stupidly") removed the sound control from the panel. After some *hours* trying to figure what the heck I had done, I realized that it's not necessary to install anything (quite obvious since nothing was uninstalled): you just have to right-click the panel, go to the _Panel Preferences_ and add this item: **Indicator ****Plugin**.

After you do this, the volume daemon (**xfce4-volumed**) will place the sound control back on the panel and thus you'll be able to use the sliding volume control again.

---

### Post by guillermo_lopez on 2012-12-04
> **bug67 said:**
> Maybe try right clicking on the panel then selecting panel, "Add new items."  Then you can scroll through a list of things you can add to the panel.  One of which is the "Indicator Plugin."  That's the one you want.

:guitar:
Thank you Bug 67. It works for me!!!
You rock

---

### Post by andreic74 on 2012-12-27
Thank you. It works!

---

### Post by Buntu Bunny on 2012-12-27
Ditto for me! Thanks all.

---

### Post by kevin34ct on 2013-06-06
LOL, worked for me too.  It's called Indicator Plugins though.  I removed the Weather applet and my sound and messenger got removed at the same time.  Not sure why that happened, but this was a great help.

---

### Post by mai.joshua.2012 on 2013-12-28
thanx

---

### Post by wildmanne39 on 2013-12-30
Thread closed. Please do not post in old threads.

---

