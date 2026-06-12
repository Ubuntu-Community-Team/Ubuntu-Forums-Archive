---
title: "Check Gmail from Deskbar Applet"
date: 2009-05-10
forum: Desktop Environments
---

### Post by bhagwad on 2009-05-10
Hi,

Just wanted to know if anyone has found a way to search their Gmail from the Ubuntu Deskbar Applet.

Previous solutions involved putting my username/password in plain text like so: [http://www.kryogenix.org/days/2006/03/20/gmail-deskbar](http://www.kryogenix.org/days/2006/03/20/gmail-deskbar), but I'm not comfortable doing that.

I'm using Tracker with the Deskbar and I'd like to search my online Gmail as well.

Thanks in advance for any help.

---

### Post by ABINAYA on 2009-05-11
I swear by the Deskbar applet. I swear by GMail. So lets put two and two together. Deskbar allows you to add “handlers” which are 3rd party extensions to this wonderful search utility. **[Here]("http://svn.kryogenix.org/svn/deskbar-plugins/tags/LATEST/gmail-deskbar-hack.py") is a handler to allow Deskbar to search your GMail from within Ubuntu. **Just save this script in your **/home/.gnome2/deskbar-applet/handlers/** directory and it will automatically appear in your **Deskbar Preferences**. The script requires a little tweaking – you will need to hardcode your GMail username and password in order for it to work. At the top of the script there is a section:








=======================================================
:guitar::guitar::guitar::guitar:
\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\
[Illinois Sexual Predators](http://www.registeredsexualpredators.org/Illinois-Sexual-Predators)
[human growth hormone](http://cibexolabs.com/)

---

### Post by bhagwad on 2009-05-11
> **ABINAYA said:**
> I swear by the Deskbar applet. I swear by GMail. So lets put two and two together. Deskbar allows you to add “handlers” which are 3rd party extensions to this wonderful search utility. **[Here]("http://svn.kryogenix.org/svn/deskbar-plugins/tags/LATEST/gmail-deskbar-hack.py") is a handler to allow Deskbar to search your GMail from within Ubuntu. **Just save this script in your **/home/.gnome2/deskbar-applet/handlers/** directory and it will automatically appear in your **Deskbar Preferences**. The script requires a little tweaking – you will need to hardcode your GMail username and password in order for it to work. At the top of the script there is a section:


=======================================================
:guitar::guitar::guitar::guitar:
\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\
[Illinois Sexual Predators]("http://www.registeredsexualpredators.org/Illinois-Sexual-Predators")
[human growth hormone]("http://cibexolabs.com/")

I've already seen this. As I mentioned in the first post, I don't *want* to hardcode my Gmail password anywhere - it makes me cringe just to SEE my password in plain text!

- Any other suggestions?

---

