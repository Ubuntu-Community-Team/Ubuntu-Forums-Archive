---
title: "gnome: clicking &quot;quit&quot; freezes session"
date: 2007-07-10
forum: Desktop Environments
---

### Post by dbbolton on 2007-07-10
when i go to System > Quit in a GNOME session, it freezes, so i can't log out. i have to restart my computer, because if i simply restart X i will remain logged in.

---

### Post by scragar on 2007-07-10
I know this is a little round the houses but couldn't you add lock screen to one of your panels then use that to return to the user select and shutdown/logout?

as I said it's a little around the houses but in theory it should work.

---

### Post by dbbolton on 2007-07-10
> **scragar said:**
> I know this is a little round the houses but couldn't you add lock screen to one of your panels then use that to return to the user select and shutdown/logout?

as I said it's a little around the houses but in theory it should work.
yeah, that probably would work, but i need to actually log out.

thanks anyway

---

### Post by VictorR on 2007-07-13
Something similar happened after I had installed xcompmgr. So before hitting Quit I have to terminate xcompmgr now. I just made an extra launcher next to quit with 
$ killall xcompmgr
which I click before Quit.

---

### Post by vanadium on 2007-07-13
i have this issue now and then, and it seems to occur only after i have used XMMS. I can then kill X-org using Ctrl+Alt+Backspace, and from then on, Ubuntu shuts down normally.

---

### Post by dbbolton on 2007-07-13
> **VictorR said:**
> Something similar happened after I had installed xcompmgr. So before hitting Quit I have to terminate xcompmgr now. I just made an extra launcher next to quit with 
$ killall xcompmgr
which I click before Quit.
this turned out to be my issue as well

---

### Post by nowshining on 2007-10-26
i don't have the xcompmgr but I myself get freezes in gutsy - however if I remove all my home files - yes I have a backup and logout ctrl alt and backspace and log in then 99 percent of the time It works fine, so now I have a good starting point to start from that I can just restore ugh!

---

### Post by nowshining on 2007-10-26
okay i think i solved it - i searched dbus in synaptic and re-installed all the dbus packages and then noticed dbus (x11) was not installed - looked at the description and it said it was needed for dbus apps - installed that - when all done installing - hit quit - froze - backspaced out of it - re-signed in and it seems to once again work.. :)

---

### Post by Lardarse on 2007-10-27
I have similar problems with my quit button. However, X doesn't completely freeze, it just no longer responds to input. I am not yet sure what this is related to, but I have a few ideas...

---

### Post by Guardian-Mage on 2007-10-27
I downloaded Ubuntu 7.10 Gutsy from the Ubuntu.com website and installed it, and the same thing happened to me. I clicked Main Menu>Quit and X11 froze. My mouse could still move around but I couldn't click on anything(Nor Type). I went into Menu>Synaptic Package Manager, and searched DBUS. I installed the packages: dbus-1-doc and dbus-x11 and now it works.

Good luck

---

### Post by bluespymaster on 2007-10-27
This also happened to me when I changed the file /etc/rc.d/rc to have the option CONCURRENCY=shell (supposedly to speed up bootup time).  This messed up HAL and caused the freezing issue.  When I set it back to CONCURRENCY=none and rebooted, the problem disappeared.

---

### Post by nowshining on 2007-10-28
lolz I tried that too and it did that actually it quit seeing my centon drive..lolz

---

### Post by ebash on 2007-10-28
I have encountered the same problem in my computer, but strangely this bug doesn't affect all users. My account is fine and has no problems when I click the logout screen but my wife's account wasn't that fortunate.

When she clicks the logout button it seems as if the computer freezes. Although the mouse can be moved, in fact if you have the Geyes applet installed the eyes follow the mouse just fine. The problem is that the mouse clicks and  keyboard keys are ignored, thus making the computer unusable.

Both accounts are using compiz, but it happened also when she was using metacity. The only difference between the accounts is that I have an administrator profile, while she doesn't.

I will give a try to the installation of dbus-x11.

---

