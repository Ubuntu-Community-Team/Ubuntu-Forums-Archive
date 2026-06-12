---
title: "Edgy Crash"
date: 2006-11-18
forum: Desktop Environments
---

### Post by antisho on 2006-11-18
Ubuntu Edgy keeps crashing. That is, occasionally the display will freeze up and catapult me back to the login screen. It happens with semi-graphics-intensive stuff, like certain screensavers. Sometimes when logging back in, the desktop won't initiate and makes me hard reboot, which is bad since the filesystem doesn't get unmounted cleanly.
A while ago, after upgrading to Edgy, Xorg started sucking up CPU. The problem seems to have stopped right when this one started, since Xorg rarely uses above 20% CPU and most of the time under 10%.
I noticed that this started after I restored Windows XP's C:/Windows from backup, this shouldn't have any connection, since XP's a different OS on a different partition even though it's mounted in the filesystem.
It was suggested to me to check /var/log/ for Xorg logs, but as far as I can tell (which isn't very far) they don't show anything unusual. They're also long so if they're needed tell me which part to post.

---

### Post by cantormath on 2006-11-18
> **antisho said:**
> Ubuntu Edgy keeps crashing. That is, occasionally the display will freeze up and catapult me back to the login screen. It happens with semi-graphics-intensive stuff, like certain screensavers. Sometimes when logging back in, the desktop won't initiate and makes me hard reboot, which is bad since the filesystem doesn't get unmounted cleanly.
A while ago, after upgrading to Edgy, Xorg started sucking up CPU. The problem seems to have stopped right when this one started, since Xorg rarely uses above 20% CPU and most of the time under 10%.
I noticed that this started after I restored Windows XP's C:/Windows from backup, this shouldn't have any connection, since XP's a different OS on a different partition even though it's mounted in the filesystem.
It was suggested to me to check /var/log/ for Xorg logs, but as far as I can tell (which isn't very far) they don't show anything unusual. They're also long so if they're needed tell me which part to post.


PEOPLE!!!!
YOU NEED TO REALIZE THAT EDGY IS NOT!!!!!.....STABLE YET.
Sorry for yelling.  If you cant fix the problem, dont do the upgrade until  edgy (hint in the name) gets more stable.  Dapper is there offically supported industry version for the next few years, hence the ETS in the title.  Edgy is named edgy for a reason....

I know that this does not fix the problem, I am just seeing way to many people switching to EDG-Y expecting it to be bug free.....

what kinda hardware are you running edgy on?
Did you do all the upgrades yet?

---

### Post by antisho on 2006-11-18
What's this about "Don't do the upgrade until Edgy gets more stable"? I upgraded a long time ago, otherwise I wouldn't be asking about it! Don't think I wasn't aware of the risks when I upgraded. I was. And this turned up weeks after I did so, thus I think there's something more than just Edgy being unstable.

As for updates, yes, I have the latest version of all installed packages, as far as I can tell, and assuming that's what you mean.

Hardware, be more specific? Or should I lspci or something and dump it here? It's an x86 architecture, with an ATI video controller.

---

### Post by antisho on 2006-11-19
Can someone help?

---

### Post by Crooksey on 2006-11-20
Have you installed latest gfx card drivers?

---

### Post by antisho on 2006-11-20
> **Crooksey said:**
> Have you installed latest gfx card drivers?
How would I check that?

---

