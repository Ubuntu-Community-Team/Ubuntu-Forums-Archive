---
title: "OpenOffice.org menus and buttons like to hide"
date: 2009-02-03
forum: General Help
---

### Post by Aaron44126 on 2009-02-03
Hi, I'm wondering if anyone else has seen this.  I did some searching but I wasn't able to find anything that looked like this particular issue.

In OpenOffice.org, menus entries, buttons, etc. sometimes hide when I move the mouse over them.  I can sometimes get them to reappear my moving the mouse over again, but it doesn't always work (seems random).

Here's some screen shots to describe what I'm talking about:

[IMG]http://stuff.aaron-kelley.net/oo1.png[/IMG]
Help menu with some text missing.

[IMG]http://stuff.aaron-kelley.net/oo2.png[/IMG]
Mouse over a toolbar button.  You can see the button outline but not the little icon.

[IMG]http://stuff.aaron-kelley.net/oo3.png[/IMG]
Options dialog.  Notice that there is a button on the bottom with no text, one of the drop-downs are messed up, and the text next to some of the checkboxes is missing.

I'm using Ubuntu 8.10 (latest updates) with an NVIDIA GeForce 8600 graphics card (with the proprietary driver, 177.82).  Graphics settings are pretty much defaults (but I do suspect that this has to do with the Compiz graphics effects?).  This is easy for me to reproduce in both OpenOffice.org 2.4 and 3.0, but I haven't seen any behavior like this in any other applications.  It has been doing this since I first started using Ubuntu.

Ideas?

Thanks!

---

### Post by bapoumba on 2009-02-03
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/286932](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/286932)
Looks like a bug..

---

### Post by Aaron44126 on 2009-02-03
Thanks, dunno why I couldn't find that.  I'll follow that bug.

---

### Post by bapoumba on 2009-02-03
> **Aaron44126 said:**
> Thanks, dunno why I couldn't find that.  I'll follow that bug.
You're welcome.

I had to refine the google search a couple times. I believe what worked (this was the second link) was : openoffice button disappear mouse nvidia ;)

---

### Post by binbash on 2009-02-03
Please try this

System > preferences > appearance > fonts > and tick subpixel rendering/smoothing

See if it fixes it.

---

### Post by Aaron44126 on 2009-02-03
Actually, I found that an easy fix is just to update to version 180 of the NVIDIA driver.  It's already in the Ubuntu repos (but not offered to you by default).

sudo apt-get install nvidia-glx-180

Then reboot, and it's fixed.

---

### Post by x C0MMAND0 x on 2009-02-03
> **Aaron44126 said:**
> Actually, I found that an easy fix is just to update to version 180 of the NVIDIA driver.  It's already in the Ubuntu repos (but not offered to you by default).

sudo apt-get install nvidia-glx-180

Then reboot, and it's fixed.

Thank you so much!  That worked perfectly and it "seems" my 3d effects rendering is smoother, but I'm sure it's all in my head.  Thank you very much though, I really appreciate this fix.

---

### Post by Aaron44126 on 2009-02-04
I think the 3D effects are rendering smoother here, too.  I think this is because the new driver prefers to keep the graphics card at a higher performance level for some reason.  You can check the performance level in the NVIDIA X Server Settings (in the PowerMizer section), it updates in real time; I've looked at it a few times using NVIDIA 177 and it usually stayed at 0, but now I notice that it usually stays at 1.  Hmm...

---

