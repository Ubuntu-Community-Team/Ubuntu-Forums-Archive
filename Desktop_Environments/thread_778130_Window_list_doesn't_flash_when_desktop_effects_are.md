---
title: "Window list doesn't flash when desktop effects are turned off"
date: 2008-05-01
forum: Desktop Environments
---

### Post by EnderBender on 2008-05-01
Hi,

I have a freshly installed Ubuntu Hardy Heron and when I deactivate the desktop effects, applications in the window list (the bar at the bottom in gnome) stop flashing orange when they want attention, like when I have a new message waiting in an instant messanger.

It works again when I put the desktop effects back on the "normal" setting instead of "none" but I don't want to use compiz, everything 2D (like scrolling a website in firefox) is slow (not unusable slow but still slow) because I use an ATI graphics card and have to use the closed source driver (HD 2600 XT graphics card).

Does someone here know of this behavior when turning off desktop effects and maybe has a solution, or is there something wrong with my installation?

Thanks in advance for any help.

---

### Post by Zorael on 2008-05-02
As far as I know, the taskbar applet isn't Compiz-aware, which in essence means Compiz (as the window manager) isn't passing on information on what running apps are flagged as wanting urgent attention. This is, at the very least, the case in KDE. (There is a kicker-taskbar-compiz package, but I don't seem to get urgent windows to flash when using it, either.)

I'm not sure there is a solution, beyond bullying developers into investigating the issue. The fault may lie in Compiz not broadcasting urgent states, or the Gnome (and KDE) taskbar applets being ignorant to them; I couldn't say.

---

### Post by EnderBender on 2008-05-02
> **Zorael said:**
> As far as I know, the taskbar applet isn't Compiz-aware, which in essence means Compiz (as the window manager) isn't passing on information on what running apps are flagged as wanting urgent attention. This is, at the very least, the case in KDE. (There is a kicker-taskbar-compiz package, but I don't seem to get urgent windows to flash when using it, either.)

I'm not sure there is a solution, beyond bullying developers into investigating the issue. The fault may lie in Compiz not broadcasting urgent states, or the Gnome (and KDE) taskbar applets being ignorant to them; I couldn't say.

Hi, thanks for the reply :)
But it is the other way around for me. In compiz it does work, in metacity it doesn't.

---

### Post by Zorael on 2008-05-02
Ugh, I obviously fail basic reading comprehension.

---

### Post by EnderBender on 2008-05-03
> **Zorael said:**
> Ugh, I obviously fail basic reading comprehension.

No problem ^^
I should have mentioned Compiz and Metacity, would have been better to understand I think :) I tend to write a bit.. I don't want to say crazy, but I have to.

**Update:**

I found out what's causing this by looking into the amsn-project forum. It is a bug in Metacity. Priority for this bug is set to low so I don't think it will be fixed any time soon. I'll use KDE for the moment I think because for me this flashing behavior is essential. I don't want to switch to a messenger window every minute to see if someone wrote me.


**Links with more info:**
[amsn forum thread]("http://www.amsn-project.net/forums/viewtopic.php?t=4903")
[Launchpad Bug report]("https://bugs.launchpad.net/ubuntu/+source/metacity/+bug/220555")

---

